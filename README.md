# esp_ld3320
esp8266 ld3320

https://www.arduino.cn/thread-78023-1-20.html

void VoiceRecognition::noiseTime(uint8_t noise_time_)；
//上电噪声略过，参数（0x00~0xff,单位20MS），默认值0x02，按需更改
void VoiceRecognition::voiceMaxLength(uint8_t voice_max_length_)；
//最长语音段时间，参数（0x00~0xC3,单位100MS），默认值0xc3，20秒，例程里的短语识别的话改为2~3s即可
void VoiceRecognition::speechEndTime(uint8_t speech_end_time_)；
//调整语音端点结束时间（吐字间隔时间），参数（0x00~0xC3,单位10MS），我没有更改这项
void VoiceRecognition::speechStartTime(uint8_t speech_start_time_)；
//调整语音端点起始时间，参数（0x00~0x30,单位10MS），我没有更改这项
void VoiceRecognition::speechEndpoint(uint8_t speech_endpoint_)；
//调整语音端点检测，参数（0x00~0xFF,建议10-40），看不懂这项在说什么
void VoiceRecognition::micVol(uint8_t vol)；
//调整ADC增益，参数（0x00~0xFF,建议10-60），室内使用调小，室外调大
void VoiceRecognition::reset()
//LD3320复位操作
void VoiceRecognition::init(uint8_t mic);
//模块启用，参数为麦克风选择（MIC/MONO）在SETUP中调用，MIC即3.5mm麦克风接口，MONO为内置咪头，默认为咪头，大部分参数设置请在这个函数调用后设置
int VoiceRecognition::read()；
//识别结果读取，返回值为读到的命令编号
void VoiceRecognition::addCommand(char *pass,int num)
//添加指令，参数为拼音加指令标号（read()返回的就是这个标号）示例：    Voice.addCommand("kai deng",0);Voice是事先初始化好的VoiceRecognition对象，在init()后使用
unsigned char VoiceRecognition::start();
//开始识别，此函数会将之前设定的参数传递给模块