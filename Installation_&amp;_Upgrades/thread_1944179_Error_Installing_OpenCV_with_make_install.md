---
title: "Error Installing OpenCV with make install"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by leovn on 2012-03-20
Help me,

I installed OpenCV as guided by this link [http://opencv.willowgarage.com/wiki/InstallGuide]("http://opencv.willowgarage.com/wiki/InstallGuide") and this link [http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian]("http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian")

But I got errors at this step...Please help me out. Thanks.

```
phuocpv@ubuntu:~/opencv/release$ sudo make install
[sudo] password for phuocpv: 
[  0%] Built target opencv_imgproc_pch_dephelp
[  1%] Built target pch_Generate_opencv_imgproc
[  2%] Built target opencv_core_pch_dephelp
[  2%] Built target pch_Generate_opencv_core
[  5%] Built target opencv_core
[ 13%] Built target opencv_imgproc
[ 14%] Built target opencv_calib3d_pch_dephelp
[ 14%] Built target pch_Generate_opencv_calib3d
[ 15%] Built target opencv_features2d_pch_dephelp
[ 15%] Built target pch_Generate_opencv_features2d
[ 16%] Built target opencv_flann_pch_dephelp
[ 17%] Built target pch_Generate_opencv_flann
[ 17%] Built target opencv_flann
[ 17%] Built target opencv_highgui_pch_dephelp
[ 17%] Built target pch_Generate_opencv_highgui
[ 17%] Building CXX object modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_ffmpeg.o
In file included from /home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg.cpp:45:0:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In member function ‘void CvCapture_FFMPEG::close()’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:451:9: warning: ‘void av_close_input_file(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1436) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:451:31: warning: ‘void av_close_input_file(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1436) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In member function ‘bool CvCapture_FFMPEG::reopen()’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:483:5: warning: ‘void av_close_input_file(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1436) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:483:27: warning: ‘void av_close_input_file(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1436) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:486:52: error: ‘av_open_input_file’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:487:5: warning: ‘int av_find_stream_info(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1266) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:487:27: warning: ‘int av_find_stream_info(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1266) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:494:50: error: ‘avcodec_thread_init’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:497:5: warning: ‘int avcodec_open(AVCodecContext*, AVCodec*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3719) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:497:28: warning: ‘int avcodec_open(AVCodecContext*, AVCodec*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3719) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In member function ‘bool CvCapture_FFMPEG::open(const char*)’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:524:63: error: ‘av_open_input_file’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:529:11: warning: ‘int av_find_stream_info(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1266) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:529:33: warning: ‘int av_find_stream_info(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1266) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:541:54: error: ‘avcodec_thread_init’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:550:13: warning: ‘int avcodec_open(AVCodecContext*, AVCodec*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3719) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:550:36: warning: ‘int avcodec_open(AVCodecContext*, AVCodec*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3719) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In function ‘AVStream* icv_add_video_stream_FFMPEG(AVFormatContext*, CodecID, int, int, int, double, int)’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:999:7: warning: ‘AVStream* av_new_stream(AVFormatContext*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1460) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:999:26: warning: ‘AVStream* av_new_stream(AVFormatContext*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1460) [-Wdeprecated-declarations]
In file included from /home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg.cpp:45:0:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In function ‘int icv_av_write_frame_FFMPEG(AVFormatContext*, AVStream*, uint8_t*, uint32_t, AVFrame*)’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1121:20: warning: ‘int avcodec_encode_video(AVCodecContext*, uint8_t*, int, const AVFrame*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:4039) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1121:72: warning: ‘int avcodec_encode_video(AVCodecContext*, uint8_t*, int, const AVFrame*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:4039) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In member function ‘void CvVideoWriter_FFMPEG::close()’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1298:20: error: ‘url_fclose’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp: In member function ‘bool CvVideoWriter_FFMPEG::open(const char*, int, double, int, int, bool)’:
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1411:35: error: ‘av_set_parameters’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1415:35: error: ‘dump_format’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1442:15: warning: ‘int avcodec_open(AVCodecContext*, AVCodec*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3719) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1442:36: warning: ‘int avcodec_open(AVCodecContext*, AVCodec*)’ is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3719) [-Wdeprecated-declarations]
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1479:42: error: ‘URL_WRONLY’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1479:52: error: ‘url_fopen’ was not declared in this scope
/home/phuocpv/opencv/modules/highgui/src/cap_ffmpeg_impl.hpp:1485:25: error: ‘av_write_header’ was not declared in this scope
make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_ffmpeg.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by pepellou on 2012-03-22
I got the same problem, gonna try this: [http://code.opencv.org/issues/1605](http://code.opencv.org/issues/1605)

---

