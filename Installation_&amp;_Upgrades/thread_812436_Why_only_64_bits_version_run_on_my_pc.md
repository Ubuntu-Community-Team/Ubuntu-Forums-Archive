---
title: "Why only 64 bits version run on my pc?"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by pVilaça on 2008-05-29
I've a Dual Core E2180 

I try to install the ubuntu 8.04 and in the installation menu, after it loads the kernel i got a black screen. I try the ubuntu 7.10 and same thing. I try the 7.04 and I have no problems.

After, I try to install Ubuntu 8.04 64 bits version, and I've no problems. 

Could you help me, please?

---

### Post by tommcd on 2008-05-29
[QUOTE=pVilaça;5074966]I've a Dual Core E2180 

I try to install the ubuntu 8.04 and in the installation menu, after it loads the kernel i got a black screen. I try the ubuntu 7.10 and same thing. I try the 7.04 and I have no problems.

After, I try to install Ubuntu 8.04 64 bits version, and I've no problems. 

Could you help me, please?[/QUOTE

I suppose it is possible that the live CD installer for Hardy 32 bit is having problems with your video card, and the Hardy 64 bit does not. To test this, download the Ubuntu Hardy 32 bit alternate install (text based) CD and see if you can install from that.
Any 64 bit CPU can install 32 or 64 bit Operating systems (as far as I know anyway). I have an AMD Athlon64 CPU and I have always used 32 bit Ubuntu, Debian, and many others.
EDIT: What video card do you have anyway?

---

### Post by pVilaça on 2008-05-29
I've an onboard video card.

Board: Abit Fatal1ty F-I90HD
 and the video card is an ATI Radeon Xpress X1250

Thanks

---

### Post by tommcd on 2008-05-29
A quick google search turned up this:
[http://wiki.linuxmce.org/index.php/Abit_Fatal1ty_F-I90HD](http://wiki.linuxmce.org/index.php/Abit_Fatal1ty_F-I90HD)

```
You probably need to use the Kubuntu Alternate Install CD. Pick you favorite mirror, 
and then choose the alternate install CD. This will get you a nice text-only installer.

Get video going:
The F-I90HD uses the ATI Xpress 1250 chipset, so after installation is completed, 
you can follow this guide to get video going properly. 
```

IN case you are wondering, linux MCE is a media center add on for Kubuntu. So it seems they needed the alternate install CD also, so try that.
I don't know much about ATI cards. Here are the official Ubuntu instructions for ATI:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(ati)|(driver](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(ati)|(driver))
Or here is the instructions from linux MCE:
[http://wiki.linuxmce.org/index.php/Display_Drivers#Installation](http://wiki.linuxmce.org/index.php/Display_Drivers#Installation)[COLOR="Red"][/COLOR]

---

### Post by pVilaça on 2008-05-29
I will try.

I'de install ubuntu with alternate cd, but after, when I try to use ubuntu, it dont boot.

---

### Post by tommcd on 2008-05-30
Well, what happens when you try to boot it? Anything? Any error messages? 
Did the install go ok? Any problems with the install?

Please be specific. How did you install via the alternate CD? Any problems encountered during the install? And if it won't boot exactly what happens. Do you get the grub menu? then a kernel panic or other errors?

---

### Post by pVilaça on 2008-05-30
At installation, I've no problems. But, I need to active two options to run the install (noapci and noapic="no").

Then, when I turn on pc, I see grub menu, I choose ubuntu and It stay at a black screen saying "starting..." and don't say anything more.

---

