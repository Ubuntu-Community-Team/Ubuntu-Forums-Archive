---
title: "Lubuntu installation problems."
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by ghost14 on 2016-04-11
[FONT=&amp]I’ve seen this problem brought up all over the place, but no solution seems to work for me.[/FONT]
  
  [FONT=&amp]I have an “intel D2500CCE Atom D2500 Dual LAN & Dual COM Fanless Mini-ITX PC w/ 2GB, Morex T3410” (this is its exact name, plugging it into any search should bring up any other specs needed.) It was given to me by a friend who moved away and was unable to take it with him. When I first booted it up I thought there would be nothing on it, but it loaded a GNU GRUB (Version 0.97) command prompt, I don’t believe there is anything else loaded on this computer, but because it is not brand-new I can’t be sure. [/FONT]
  
  [FONT=&amp]I’m new to Linux and, because it is not a very powerful machine, I wanted to install the LTS Lubuntu (Version 14.04.4)-(64bit.) I downloaded it and made a bootable USB flash drive using Universal-USB-Installer-1.9.6.4.[/FONT]
  [FONT=&amp]I made the computer boot into flash drive on startup and I was able to get to the Lubuntu menu. When I tried to install or try before install the screen goings black.[/FONT]
  [FONT=&amp]I looked around and the solution seemed to be to edit “Try Lubuntu without installing” and replace the words “quiet” and “splash” with the words “nomodeset” and “xforcevesa.”[/FONT]
  [FONT=&amp]It seemed to work for a short time and it looked like Lubuntu was booting but after a few walls of text (some too fast to read) the screen goes black and I assume it hard-locks or crashes.[/FONT]
  
  [FONT=&amp]I apologize if this question has been answered before, but I’ve done numerous searches and can’t seem to find any solutions for why this is happening.[/FONT]

---

### Post by mail-2o on 2016-04-12
When neither “nomodeset” nor “xforcevesa" have worked for me, I've sometimes found that adding "vga=791" instead, to the grub boot line, will work.   From my experience, Intel have used some seemingly unsupported graphics chips on some of their fanless motherboards. I have a fanless board for which only a Windows 7 driver was ever released, ie not win 8 nor 10, and no open source details were released so I can only get it to run at something like 600 x 600 using Linux. Am I right in saying that graphics drivers are becoming a worse and worse problem?  (Heads off back to try again to get a VIA Chrome M'Board working on any flavour of Ubuntu. Debian OK, Ubuntu not)

---

### Post by RobGoss on 2016-04-13
Hello and welcome, It would helpful if you provided the specs for that machine in question. At this point we can only guess what maybe giving causing this problem.

---

### Post by mail-2o on 2016-04-13
The specs for my VIA Board are:
> Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
VGA compatible controller: VIA Technologies, Inc. VX900 Graphics [Chrome9 HD]
Audio device: VIA Technologies, Inc. Device 9170
CPU CentaurHauls VIA Nano X2 L4050 @ 1.4 GHz
But I don't want to hijack Ghost14's thread. I don't have the fanless Intel board with me at the moment so cannot give the specs.

---

### Post by sudodus on 2016-04-14
I think a good way to find a linux distro and version is ***trial and error***. Download or get via torrent various iso files. Check with md5sum (or whatever checksum is available) that the download was good. This is checked automatically with torrent.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

You can try with the next version of Lubuntu, Xenial Xerus. It will be released during this month as Lubuntu 16.04 LTS. You can find it via the testing tracker at
this link: [Download links for ISO-testing Lubuntu Desktop i386 ](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/116833/downloads)

As has been stated, there can be problems with some graphics chips. This computer is not brand new, so it might work better with an older version. *Lubuntu 14.04.1 LTS* is the oldest supported version, but there are light-weight community re-spins and other distros based on Ubuntu 12.04 LTS, for example ***Bento***, ***Bodhi***, ***LXLE*** and ***ToriOS***. You can get one of those. I suggest that you try 32-bit (alias i386, i586, i686) operating systems.

As already written by *mail-2o*, Debian might work better. ***Debian Jessie*** is the current stable version.

If problems with these distros, you can try with ***Knoppix*** and the ultra-light linux distros ***Wary Puppy***, ***TahrPup*** and ***Tiny Core***.

---

### Post by Bucky Ball on 2016-04-14
If nomodeset worked and you booted fine then you rebooted and things were back to chaos, it is because changing the grub kernel line the way you did is only effective for that boot. Lost on reboot. You need to make those options that work permanent. 

Add them to the line again so you can boot in and once at a desktop, open a terminal and:

```
sudo nano /etc/default/grub
```

Look for this bit at the top and the line I have in bold:

```
[QUOTE]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT=""**
GRUB_CMDLINE_LINUX=""
```

Make that line look like:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Add any other options you were using there after a space ("nomodset other_option"). You must keep the quotation marks.

Control+x then 'y' to save and close the file, then:

```
sudo update-grub
```

Reboot.

---

### Post by mail-2o on 2016-04-14
> **ghost14 said:**
> [FONT=&amp]I have an “intel D2500CCE Atom D2500  [/FONT][FONT=&amp][/FONT]I notice that this board and mine (an Intel DN2800MT) have the same recommended Linux Intel graphics driver, a 32 bit driver, [Intel PowerVR graphics]("https://downloadcenter.intel.com/download/21938/Graphics-Linux-PowerVR-Graphics-Media-Drivers") I suspect that this is for the same chipset, the Intel® NM10 Express Chipset. 
As Sudodus said, I think only a 32 bit distro will work for you. As the board is totally silent, and, assuming that it is like mine, has a silent external power supply, it is an attractive board and worth persisting with. I will be doing so, but unfortunately cannot for a couple of months.
For info, From the Intel website:
> **Purpose **Provides Linux* PowerVR graphics/media  drivers (32-bit). These graphics/media drivers are ported from  Imagination Technologies* (IMG) Device Driver Kit (DDK) version 1.7  ED862890. 
**Additional Notes **Refer to [**Enabling hardware accelerated playback**]("http://support.intel.com/support/motherboards/desktop/sb/CS-033648.htm") for case studies using a system with Intel® Atom™ Processor N2800 and Intel® NM10 Express Chipset.

> **sudodus said:**
> You can try with the next version of Lubuntu, Xenial Xerus.This looks good. I'm writing this from the Live CD, at this moment, using vga=791 on the boot line, but am still hitting the same problem that I hit with any recent Ubuntu distro, 14.04 upwards. I get an installer error about 3/4 way through copying files whilst trying to install. The error is "Errno 5" "input/output error". It doesn't seem to matter what DVD drive I use, or even a USB key, it just seems that no flavour of Ubuntu, and I've tried several, will install to this motherboard. 
I know it is not a well supported board. 
It is strange that both Debian 8.4 and Antix-15 (debian based) will install OK. 

CPU CentaurHauls VIA Nano X2 L4050 @ 1.4 GHz
VIA Technologies, Inc. VX900 Graphics [Chrome9 HD]

---

### Post by mörgæs on 2016-04-15
Have you tried installing using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by sudodus on 2016-04-15
Well, Debian 8.4 is a major distro, and it works for you. This is quite good :-)

It can be difficult to find out what is causing the problems with Ubuntu.

I suggest that you install Debian. Maybe later on you can try Ubuntu or an Ubuntu based flavour again.

---

### Post by Bucky Ball on 2016-04-15
> **mörgæs said:**
> Have you tried installing using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

^^^
This.

Give it a go.

---

### Post by mail-2o on 2016-04-16
> **mörgæs said:**
> Have you tried installing using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?I hadn't thought of that, but have tried that now, thank you. It fails at the "select and install software" step which is probably the same step at which the ISOs fail. So I've learned something. I can at least get the minimal install to boot to an initramfs prompt which has given me more clues. (There is no Windows partition on this disk!)
I might pursue this further at a later date, but for now, as Sudodus recommends, I'll stick with the working Debian distro. I need to use the machine, but hate to be beaten by it. :)

Thanks for all your advice. I'll explore your [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") article further.

I hope we will hear more how ghost14 fairs.

---

### Post by bill100 on 2016-04-21
I'm not sure if this is relevant but it may be worth a try.

LXLE doesn't install a GUI if you select auto login during installation and possibly similar distros have the same problem.

I failed to boot after install on two machines but no problem when I reinstalled with autologin disabled.

(I had no problem installing mint or linux lite with autologin enabled.)

[http://www.lxle.net/forums/discussion/1217/black-screen-after-lxle-installation-no-problem-with-live-environment](http://www.lxle.net/forums/discussion/1217/black-screen-after-lxle-installation-no-problem-with-live-environment) is a useful reference but I can't register there!

---

### Post by mail-2o on 2016-04-22
> **bill100 said:**
> LXLE doesn't install a GUI if you select auto login during installation and possibly similar distros have the same problem.Thanks bill100, but I don't think that was an issue for me. One distro didn't install a GUI, as you stated, but using apt-get install I was able to install and try xfce and lxde desktops.      

I have now tried many Ubuntu flavoured distros from Emmabuntus 14.04, Ubuntu 16.04, Mint 17 to the likes of Lubuntu minimal. The only one with which I had any success was Lubuntu 12.04 but even that was a bit flaky. I upgraded to 14.04 which appeared to go well but some packages wouldn't work, ie Synaptic despite purging and reinstalling it.   

As said previously, some Debian distros will install but still have some problems, maybe due to my lack of raw Debian knowledge.  

However, I have had considerable success with Mythbuntu 14.04, which is working well on this VIA MBoard, but I have to install packages one by one as if I try a bunch all together, it just freezes. Weird. It is now a nice little MythTV machine.    

I deem this a success, keeping an old problematic MBoard alive for a little longer, so thank you all for your assistance. I was about to give it away, running Windoze 10, which works fine but a bit slow, but the MBoard is of no use to me with that OS.

> **ghost14 said:**
> [FONT=&amp]I’ve seen this problem brought up all over the place, but no solution seems to work for me.[/FONT]
  
  [FONT=&amp]I have an “intel D2500CCE Atom D2500 Dual LAN & Dual COM Fanless Mini-ITX PC w/ 2GB, Morex T3410” ... [/FONT]
  
  [FONT=&amp]I’m new to Linux and, because it is not a very powerful machine, I wanted to install the LTS Lubuntu (Version 14.04.4)-(64bit.) I downloaded it and made a bootable USB flash drive using Universal-USB-Installer-1.9.6.4.[/FONT]
  [FONT=&amp]I made the computer boot into flash drive on startup and I was able to get to the Lubuntu menu. When I tried to install or try before install the screen goings black.[/FONT]ghost14, it seems that this issue has been solved with 16:04, at least I have installed Xubuntu 16:04 now, and the graphics driver problems have been solved in this latest distro. Well done the Ubuntu team. It now supports the Intel ® NM10 Express Chipset. At least 16:04 has solved this long standing problem on my Intel DN2800MT Board.

---

