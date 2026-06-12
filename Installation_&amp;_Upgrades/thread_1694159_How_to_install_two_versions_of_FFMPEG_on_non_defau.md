---
title: "How to install two versions of FFMPEG on non default locations"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by tauxeef on 2011-02-24
Hi Guys
Its ma first post in ubuntu forum and i hope you people will not disappoint me! :)

I have an assignment as follow.

I have to install 2 versions of FFMPEG 0.6.1 and Alexander Strange on non default locations with all required dependencies and check the dependancies for each of these and make sure to install the required dependancies in the local folder of the app rather than at the system root.

[COLOR=#202020][FONT=Times]The flags to set for the above must include
  --enable-mp3lame --enable-gpl --disable-vhook --disable-ffplay --disable-ffserver --enable-a52 --enable-xvid --enable-faac --enable-faad --enable-amr_nb --enable-pthreads --enable-x264 



[/FONT][/COLOR]Now how to install them? and how to run them simultaneously? 
Please guide me.. Do let me know if any other thing/info required.

Please i have to solve this ASAP

---

### Post by FakeOutdoorsman on 2011-02-24
> **tauxeef said:**
> The flags to set for the above must include
```
  --enable-mp3lame --enable-gpl --disable-vhook --disable-ffplay --disable-ffserver --enable-a52 --enable-xvid --enable-faac --enable-faad --enable-amr_nb --enable-pthreads --enable-x264 
```
Most of these options are invalid and will not work with the current FFmpeg source code. Why do you want these specific options? Where did you get these options from?

---

