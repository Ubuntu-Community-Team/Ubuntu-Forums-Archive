---
title: "Cannot login after WUBI install on Windows 7"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by John_Beck on 2014-08-07
Used Wubi 12.04 install found on wubi.en.uptodown.com/download.  The download put wubi-12-04-28597-en-setup.exe on my Windows 7 PC, which I ran.  Install went smoothly, including the dialog box (attached) that asked for username and then password (twice).  

Ubuntu 12.04 booted nicely, but when it asked for username and password, Ubuntu did not recognize the name and password I had entered in the Wubi dialog box.  I then signed into Ubuntu as guest, but of course could not do anything I needed to (i.e. install packages) because I did not have permission.

Since install process is relatively quick and smooth, repeated process maybe 10 time, trying different usernames and passwords.  Yes, double checked the Caps Lock.

Repeated entire install, including Wubi download, on second PC, this one with Windows 7 Embedded, and got the exact same results.

Scanned a couple of forums, and found a solution to lost and unknown passwords that seems to be the most common - hold down left Shift while booting to get to grub.  Don't know the details, but this doesn't work with this Wubi install (use Windows boot instead of Grub?).

New to Linux, but need to get a PC running Linux because an embedded SW toolchain requires it.

Any help greatly appreciated.

---

### Post by yancek on 2014-08-07
The image you posted indicates you are trying to install Ubuntu 8.04 which has not had any support for over three years.  Since you indicate you downloaded the 12.04 wubi from some site, I'm curious as to where that came from.  Better to get  a newer version of Ubuntu, 12.04 or 14.04 by googling Download Ubuntu.  Also, the Windows Ubuntu installer is no longer supported although for some reason it is still on the installation media or repositories.  It will probably not work on new releases of Ubuntu.  Also, you do understand that the wubi method just installs Ubuntu as a program inside windows, much like using virtual software.  It is not separate from windows but inside windows.

Holding down the Shift key in some situations will get you a boot menu, it won't do anything to recover your password and generally the Grub bootloader does not have a password but the Ubuntu OS does.

---

### Post by coffeecat on 2014-08-07
Welcome to the forum. 

Wubi does use grub, but the menu is hidden. If you choose Ubuntu in the Windows 7 bootloader menu, it passes control of the Ubuntu bootloading to grub. What you discovered about shift to reveal the grub menu is correct, but the timing has to be spot on. It's possible you were pressing shift too late. I suggest you tap shift repeatedly while you select Ubuntu in the Windows boot menu. 

It's very curious that your password has gone wrong twice. Did you use any special characters in the password? It's possible that the installer was set to one locale keyboard layout and the installed wubi to another.

If neither of those suggestions work, I have a couple of others, but let's see. 

By the way, wubi works just fine with Ubuntu 12.04 and Ubuntu 14.04 so long as Windows is 7 or earlier. It doesn't work in Windows 8 with uefi. Wubi is no longer maintained rather than not being supported.

---

### Post by grahammechanical on 2014-08-07
That web site that you downloaded from is not an official Ubuntu download site. It only downloads wubi.exe. How it will install Ubuntu without the rest of the Ubuntu files I do not know. I think that this failure is down to not actually having Ubuntu installed at all.

The normal, official, safe way is to download an ISO image of Ubuntu from Ubuntu.com and then burn the image to DVD or USB memory stick. And then run wubi.exe using the Windows Add/Remove programs utility. Wubi will then copy files from the DVD/USB. In fact it will install the full Ubuntu distribution. This may work with Windows 7 but it definitely will not work with Windows 8 and I do not see how wubi.exe without all the Ubuntu files on the DVD/USB could install Ubuntu.

Ubuntu software is open source software. That means that any body can get access to the source code and modify it. That exe file could have been modified to do malicious things to your OS.

You may have downloaded and activated a Trojan horse form of software.

[http://en.wikipedia.org/wiki/Trojan_horse_(computing)](http://en.wikipedia.org/wiki/Trojan_horse_(computing))

Edit: I will add this: On an official Ubuntu ISO image that has been downloaded and burn to a DVD then wubi.exe is simply called "wubi.exe." But that download from that site gives the file the name wubi-12.04-28597-en-setup.exe. Now, renaming a file is one thing. But has anything else been done to the wubi program? That is the big question. 

Regards.

---

### Post by coffeecat on 2014-08-07
> **grahammechanical said:**
> It only downloads wubi.exe how it will install Ubuntu without the Ubuntu files I do not know. 

If you run wubi.exe from within Windows and it cannot find the iso in the same directory, it will simply donwload all it needs from the Ubuntu servers. It is a perfectly valid way of installing wubi.

For example, you can download wubi.exe by itself from Canonical's own site. Scroll down to the bottom of this page for 12.04:

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Although I agree about the site the OP mentioned. Downloading wubi from a 3rd party site would be as unwise as downloading the Firefox Windows installer from the non-Mozilla sites that come up in a google search.

---

### Post by John_Beck on 2014-08-07
Ubuntu 12.04 was installed.  It booted fine as long as I logged in as Guest, explored a little - was able to launch a browser, open a Terminal window - but couldn't install anything.  The website I got it from was [COLOR=#000000]wubi.en.uptodown.com/download.

Since my initial post here, I went to another Wubi site ([/COLOR]http://download.cnet.com/Wubi/3000-2094_4-10701841.html#userreview)[COLOR=#000000].  Downloaded 12.04 again, got the exact same result.  Interestingly, though, this site had a bunch of user reviews, all complaining about exactly what I found - password not working.  So I am assuming something is up with Wubi?


[/COLOR]

---

### Post by coffeecat on 2014-08-07
I've never had this problem the few times I've installed wubi, and it's an unusual if not rare problem on these forums.

I've downloaded wubi.exe from your latest link and from the source in your first post and also from the official Canonical source in the link that I posted. According to md5sums, the wubi.exe from your two sources are identical, but different from the wubi.exe from the official source. Whether that is the reason for your problem, I don't know, but it just reinforces  what I said about not downloading things from 3rd party websites. 

If you are going to download and use wubi, I suggest you do so from the official source: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

But please read all the previous posts. Wubi is unmaintained and although you may get it to work OK, it is a dying resource and probably not worth the effort. There are alternatives to what you are trying to achieve. If you don't want to set up a conventional dual-boot with Ubuntu in a native Linux partition (the best option) then you could install Ubuntu as a guest virtual machine OS in virtualisation software such as VirtualBox running in Windows.

---

### Post by John_Beck on 2014-08-08
Coffeecat -

You da man (woman?).  Downloaded Wubi from the site you suggested, ran it, installed Ubuntu, was able to login with password as designated.  Able to access drives, etc. was not able to access before.  Running on it right now, as a matter of fact - my first non-trivial Ubuntu act.

I hear you about not using Wubi.  Once I get my feet under me Linux-wise I will probably set up a dual boot, as I did with Red Hat years ago.  This was SUPPOSED to be a quick way to explore some issues I need to know to run some tools.

Very impressed with how quickly you and others on this forum got me through this issue.  Thank you very much.

BTW - don't know what version of Ubuntu this is - is there a Ubuntu version of the Windows About ?

---

### Post by coffeecat on 2014-08-08
If you downloaded from the site I linked, you will have Ubuntu 12.04, specifically the 12.04.5 point release. 

I'm not sure whether this is so for 12.04, but in 14.04 if you click on the cogwheel top-right and then "About this Computer" you'll get something similar to Windows About. Alternatively, open a terminal, and:

```
cat /etc/lsb-release
```

Another couple of reasons not to use to use wubi for long, and to replace it with a conventional installation or a VM as soon as you can, are that wubi runs sluggishly compared with a native install. Also, it is vulnerable to filesystem corruption in the host Windows partition, which can lead to temporary or permanent loss of your wubi install.  

By the way, after a lot of sleuthing I eventually managed to find the 12.04 (the very first pre point-release) version of wubi.exe on a Canonical site. It has the same md5sum as the versions of wubi from the two sites you posted about, which means that they were not dodgy. Nevertheless, only downloading Ubuntu stuff from Ubuntu sites is good practice. I don't recall there being a bug in the 12.04 version of wubi which might explain your problem, but at least the 12.04.5 wubi has enabled you to install OK.

---

