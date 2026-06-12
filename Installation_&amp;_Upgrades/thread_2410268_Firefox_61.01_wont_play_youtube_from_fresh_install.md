---
title: "Firefox 61.01 wont play youtube from fresh install"
date: 2019-01-13
forum: Installation &amp; Upgrades
---

### Post by cam17 on 2019-01-13
I having performed an install running from a CD only of Ubuntu 18.04 AMD 64 with SHA 256 5748706937539418ee5707bd538c4f5eabae485d17aa49fb13ce2c9b70532433 running Firefox 61.01 and noticed it does not run any Youtube videos becuase it is missing HTML5.

I do not understand why HTML5 is not included is this correct?

---

### Post by Frogs Hair on 2019-01-13
Run the update manger and try again.

---

### Post by walts48 on 2019-01-14
Video stuttering on YouTube was fixed in Firefox 64.0.2 if anyone is experiencing that problem.

[https://www.mozilla.org/en-US/firefox/64.0.2/releasenotes/](https://www.mozilla.org/en-US/firefox/64.0.2/releasenotes/)

---

### Post by cam17 on 2019-01-15
Is Firefox html5 dependant on the operating system? Or should it be built in to Firefox?

---

### Post by ajgreeny on 2019-01-15
I'm not sure how necessary it is to do this but go to [https://www.youtube.com/html5](https://www.youtube.com/html5) to check that you have set the browser to use html5 as default player.

---

### Post by cam17 on 2019-01-17
I have performed the check from youtube nad it shows H.264 and MSE & H.264 with a red exclamation mark. This is after I performed a update with "Software updater"

How can I identify the missing components? I have another workstation that does not have this problem.

---

### Post by #&amp;thj^% on 2019-01-17
You might also have to install package libavcodec-extra to get the codecs:
```

sudo apt install libavcodec-extra
```
Also if those streaming services use DRM, you must enable DRM in Firefox's settings: Preferences -> General -> Play DRM-controlled content

---

### Post by cam17 on 2019-01-17
I appreciate the suggestion but I don't understand why Firefox on a updated operating system is unable to play live videos from Youtube such as [https://www.youtube.com/watch?v=JUCekz5k9E4](https://www.youtube.com/watch?v=JUCekz5k9E4).  Other Youtube videos play but Live items do not. What is wrong with the newly installed Ubuntu with Firefox?

---

### Post by walts48 on 2019-01-18
Because it is an old version of Firefox. The current version should be 64.0.2.

Try updating, or installing it from Mozilla. [https://www.mozilla.org/en-US/firefox/all/](https://www.mozilla.org/en-US/firefox/all/)

---

### Post by cam17 on 2019-01-19
No. Initially a new install starts with version 61.01 but after updating as of Jan-19-2019 Firefox was upgraded to version 64.0 and the same problem occurs. I tested playing live youtube links like "https://www.youtube.com/watch?v=JUCekz5k9E4"  on a Mac OS running Firefox 61.01 and it works which suggest the Ubuntu from a fresh install should play.

In Ubuntu youtube live doesn't run on either versions of Firefox on a newly installed Ubuntu 18.04.1 LTS

---

### Post by walts48 on 2019-01-19
Try 64.0.2?

> Fixed video stuttering on Youtube ([bug 1513511]("https://bugzilla.mozilla.org/1513511"))

REF: [https://www.mozilla.org/en-US/firefox/64.0.2/releasenotes/](https://www.mozilla.org/en-US/firefox/64.0.2/releasenotes/)

You could also try Help > Restart in Safe Mode or a test profile.

Provide a link to a video that doesn't play. Happy to check it out.

---

### Post by cam17 on 2019-01-21
It appears that Ubuntu 18.04.1 LTS does not come with FFMPEG preinstalled on the intial installation of the operating system is this correct?

---

### Post by cam17 on 2019-01-22
To correct the problem I had to install "ffmpeg" I used the command "sudo apt install ffmpeg"

Is FFMPEG not installed by default with Ubuntu 18.04.1 LTS which has been fully updated?

---

### Post by cam17 on 2019-01-26
To correct this problem you have to install ffmpeg using the following command. 
```
 sudo apt install ffmpeg
```
  
I placed this already on this site but it was removed.

---

### Post by monkeybrain20122 on 2019-01-27
To play most media you need something from the restricted-extras package(codecs etc) IIRC you need some gstreamer packages not installed by default to play youtube on Firefox (these will be pulled in if you install restricted-extras)
```

sudo apt install ubuntu-restricted-extras
```

This is one of the first things I install whenever I set up Ubuntu.

---

### Post by cam17 on 2019-01-28
To correct the problem you have to install ffmpeg for youtube live and others to run

enter the following command 
```
sudo apt install ffmpeg
```

Should ffmpeg be installed by default in Ubuntu 18.04.1 KTS

---

### Post by cam17 on 2019-02-02
Can anyone tell me if FFMPEG is installed by default on Ubuntu 18.04.1. LTS?

---

### Post by Dennis N on 2019-02-02
> **cam17 said:**
> Can anyone tell me if FFMPEG is installed by default on Ubuntu 18.04.1. LTS?

No, it's not in my Ubuntu 18.04.1, so it wouldn't be in a default install.

```
dmn@Sydney:~$ apt-cache policy ffmpeg
ffmpeg:
  Installed: (none)
  Candidate: 7:3.4.4-0ubuntu0.18.04.1

```

---

### Post by monkeybrain20122 on 2019-02-02
> **cam17 said:**
> To correct the problem you have to install ffmpeg for youtube live and others to run

enter the following command                          [COLOR=#262626][FONT=Menlo-Regular][SIZE=3][I]sudo apt install ffmpeg

Should ffmpeg be installed by default in Ubuntu 18.04.1 KTS
[/I][/SIZE][/FONT][/COLOR]


No, you need ubuntu-restricted-extras.

---

### Post by cam17 on 2019-02-02
the ubuntu-restricted-extras adds a litle more than I need. I don't remember installing anything special for video in my 16 version of Ubuntu and it worked.

---

### Post by cam17 on 2019-02-02
Does the libavcodec-extra allow you to play Youtube live videos?

---

### Post by Dennis N on 2019-02-03
> **cam17 said:**
> Does the libavcodec-extra allow you to play Youtube live videos?
On my Ubuntu 18.04.1, I can play all the YouTube videos (including the eaglets in the nest you linked in post #8) and don't have **libavcodec-extra** installed, so it must not be necessary. I've not found any that won't play.
```
dmn@Tyana:~$ apt-cache policy libavcodec-extra
libavcodec-extra:
  Installed: (none)
  Candidate: 7:3.4.4-0ubuntu0.18.04.1

```

---

