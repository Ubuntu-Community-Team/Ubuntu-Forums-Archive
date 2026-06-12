---
title: "Ubuntu-restricted-extras Error"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by niki85 on 2014-11-30
Hello,


I use 14.04.01 LTS try to install ubuntu-restricted-extras, add:


```
sudo apt-get install ubuntu-restricted-extras
```
I get this error:


```
E: Unable to locate package ubuntu-restricted-extras
```

How to fix this ?

Thanks.

---

### Post by Frogs Hair on 2014-11-30
Try the following and run the installation command again . ```
sudo apt-get update && sudo apt-get upgrade
``` If that doesn't work open software and updates and check the box next to Canonical Partners and run the following.```
 sudo apt-get update 
``` Now try the installation command again.

---

### Post by niki85 on 2014-12-01
> **Frogs Hair said:**
> Try the following and run the installation command again . ```
sudo apt-get update && sudo apt-get upgrade
``` If that doesn't work open software and updates and check the box next to Canonical Partners and run the following.```
 sudo apt-get update 
``` Now try the installation command again.

Hello,

I try your solution with 

```
sudo apt-get update && sudo apt-get upgrade
```

And

```
 sudo apt-get update 
```

And i get same error again.

---

### Post by carlwsnyder on 2014-12-01
Did you even check to see if the proper repositories are enabled as suggested by the previous post? 

[COLOR=#000000]> If that doesn't work open software and updates and check the box next to Canonical Partners and run the following.[/COLOR][COLOR=#000000]Code:
 sudo apt-get update[/COLOR]
[COLOR=#000000]Now try the installation command again.If you don't have the proper repositories enabled, you never will find the packages.[/COLOR]

---

### Post by niki85 on 2014-12-01
> **carlwsnyder said:**
> Did you even check to see if the proper repositories are enabled as suggested by the previous post? 

[COLOR=#000000]If you don't have the proper repositories enabled, you never will find the packages.[/COLOR]

How to check if my repositories are enabled and if not how to enable repositories ?
I found some tutorials online but don't help me.

Thanks.

---

### Post by slickymaster on 2014-12-01
Open Software & Updates. Select the 'Other Software' tab and check the box that says, "Canonical Partners". You'll be prompt for your password, insert it and reload your software sources.

Frogs Hair had already posted on how you should do it in his [post #2]("http://ubuntuforums.org/showthread.php?t=2254885&p=13177911&viewfull=1#post13177911").

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> Open Software & Updates. Select the 'Other Software' tab and check the box that says, "Canonical Partners". You'll be prompt for your password, insert it and reload your software sources.

Frogs Hair had already posted on how you should do it in his [post #2]("http://ubuntuforums.org/showthread.php?t=2254885&p=13177911&viewfull=1#post13177911").

I need to tutorial for do this via PuTTY ?

Thanks.

---

### Post by slickymaster on 2014-12-01
> **niki85 said:**
> I need to tutorial for do this via PuTTY ?

Thanks.

I'm not sure I understood your question. What's PuTTY have to do with your issue? PuTTY is terminal emulator, serial console and network file transfer application and it's not minimally related with your issue.

All you have to do is to open Ubuntu Software Center and from the 'Edit' menu option click 'Software Sources'. This will open the Software & Updates dialog where you'll have to navigate to the 'Other Software' tab and check the box that says, "Canonical Partners". You'll be prompt for your password, insert it and reload your software sources.

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> I'm not sure I understood your question. What's PuTTY have to do with your issue? PuTTY is terminal emulator, serial console and network file transfer application and it's not minimally related with your issue.

All you have to do is to open Ubuntu Software Center and from the 'Edit' menu option click 'Software Sources'. This will open the Software & Updates dialog where you'll have to navigate to the 'Other Software' tab and check the box that says, "Canonical Partners". You'll be prompt for your password, insert it and reload your software sources.

I do this via terminal software i have ubuntu 14.04 LTS install on my dedicated software.

Thanks.

---

### Post by slickymaster on 2014-12-01
> **niki85 said:**
> I do this via terminal software i have ubuntu 14.04 LTS install on my dedicated software.

Thanks.

To add it via terminal, run the following, one at a time:```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
```

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> To add it via terminal, run the following, one at a time:```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
```

I add this command:

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
```

But they show me again error:

```
sudo: add-apt-repository: command not found
```

?

Thanks.

---

### Post by slickymaster on 2014-12-01
Can you please post back the output you get when you run:```
apt-cache policy software-properties-common
```

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> Can you please post back the output you get when you run:```
apt-cache policy software-properties-common
```

Sure, please check:

```
software-properties-common:
  Installed: (none)
  Candidate: 0.92.37.2
  Version table:
     0.92.37.2 0
        500 http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     0.92.36 0
        500 http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

---

### Post by slickymaster on 2014-12-01
At the terminal run:```
sudo apt-get install software-properties-common
```Once that done try again one at a time:```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
```

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> At the terminal run:```
sudo apt-get install software-properties-common
```Once that done try again one at a time:```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
```

I run:

```
sudo apt-get install software-properties-common
```

Then:

```
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update
```

And then:

```
sudo apt-get install ubuntu-restricted-extras
```

And i get again same error:



```
root@:~# sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras
```

maybe this is because i use vps not dedicated server ?

---

### Post by slickymaster on 2014-12-01
> **niki85 said:**
> I run:

```
sudo apt-get install software-properties-common
```

Then:

```
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update
```

And then:

```
sudo apt-get install ubuntu-restricted-extras
```

And i get again same error:



```
root@:~# sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras
```

Sorry, my bad. Just now I realize you want to install ubuntu-restricted-extras. For that what you have to enable is the multiverse repository, not the partners one.
Use these:```
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) multiverse"
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> To add it via terminal, run the following, one at a time:```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update
```

This work thanks a lot Sir on patience with me, i now try to install:

```
sudo apt-get install ffmpeg
```

And get similar error:

```
E: Package 'ffmpeg' has no installation candidate
```

and then i found on internet some solution:

[http://tinyurl.com/kswxug8]("http://ivanblagojevic.com/2014/09/where-is-the-missing-ffmpeg-from-the-ubuntu-repositories/")

and then i try to install:

```
sudo apt-get install php5-ffmpeg
```

and again get similar error:

```
E: Unable to locate package php5-ffmpeg
```

before on some other ubuntu version i easy install all this with one command, my question is why i need on this 14.04 LTS add all this solution for install basic plugins ? And how avoid this ?

In future if i get this error i will install all with this way:

```
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) multiverse"
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras or ffmpeg or what ever
```

?

Thanks.

---

### Post by slickymaster on 2014-12-01
FFmpeg package was removed since some time now from Debian repositories, and Ubuntu now has **avconv** instead of FFmpeg. But it will be returning to the Official Ubuntu Repositories with Ubuntu 15.04 Vivid Vervet.

To install _avconv_ you need to install the **libav-tools** package:```
sudo apt-get install libav-tools
```
Or if you prefer, you can use the following PPA:```
sudo apt-add-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get install ffmpeg
```

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> FFmpeg package was removed since some time now from Debian repositories, and Ubuntu now has **avconv** instead of FFmpeg. But it will be returning to the Official Ubuntu Repositories with Ubuntu 15.04 Vivid Vervet.

To install _avconv_ you need to install the **libav-tools** package:```
sudo apt-get install libav-tools
```
Or if you prefer, you can use the following PPA:```
sudo apt-add-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get install ffmpeg
```

Thanks,

what about:

[B]sudo apt-get install php5-ffmpeg

[/B]?

---

### Post by slickymaster on 2014-12-01
> **niki85 said:**
> Thanks,

what about:

[B]sudo apt-get install php5-ffmpeg

[/B]?

From [http://ffmpeg-php.sourceforge.net/]("http://ffmpeg-php.sourceforge.net/:")> ffmpeg-php is an extension for PHP that adds an easy to use, object-oriented API for accessing and retrieving information from video and audio files. It has methods for returning frames from movie files as images that can be manipulated using PHP's image functions. This works well for automatically creating thumbnail images from movies. ffmpeg-php is also useful for reporting the duration and bitrate of audio files (mp3, wma...). ffmpeg-php can access many of the video formats supported by ffmpeg (mov, avi, mpg, wmv...)

I honestly can't manage to find any sane reason for you to install it, if you're just intending to watch videos.

---

### Post by Elfy on 2014-12-01
php5-ffmpeg 

is only in 10.04 for server and 12.04 

[http://packages.ubuntu.com/search?keywords=php5-ffmpeg](http://packages.ubuntu.com/search?keywords=php5-ffmpeg)

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> From [http://ffmpeg-php.sourceforge.net/]("http://ffmpeg-php.sourceforge.net/:")

I honestly can't manage to find any sane reason for you to install it, if you're just intending to watch videos.

I need this for one script who convert videos,
In setup.txt write and this command,

---

### Post by slickymaster on 2014-12-01
> **niki85 said:**
> I need this for one script who convert videos,
In setup.txt write and this command,

I advise you to open a new thread on that issue, since the reason behind this one is solved.

From [Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811")> **Post only one thread on your topic**. Posting multiple threads dilutes community effort, and makes it more difficult for others to help.

---

### Post by niki85 on 2014-12-01
> **slickymaster said:**
> I advise you to open a new thread on that issue, since the reason behind this one is solved.

From [Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811")


Ok. thank you very much on patience.

---

