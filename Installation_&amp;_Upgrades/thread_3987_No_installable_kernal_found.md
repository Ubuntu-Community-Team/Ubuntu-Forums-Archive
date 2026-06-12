---
title: "No installable kernal found"
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by CAPTAIN RON FL on 2004-11-10
After doing Install Base System, I get the following error. No installable kernal was foundin the define Apt sources. The default kernal package is "linux-386". You may try to continue though this strange error is probably going to fail. Which it does. I am running an emachine 466mhz, 96mb ram, 5gb hd., cdrom, ethernet card. no floppy.
Where do I go from here? I am a newbie of course. Plain english Please. Thanks, Ron

---

### Post by FLeiXiuS on 2004-11-11
[QUOTE=CAPTAIN RON FL]After doing Install Base System, I get the following error. No installable kernal was foundin the define Apt sources. The default kernal package is "linux-386". You may try to continue though this strange error is probably going to fail. Which it does. I am running an emachine 466mhz, 96mb ram, 5gb hd., cdrom, ethernet card. no floppy.
Where do I go from here? I am a newbie of course. Plain english Please. Thanks, Ron[/QUOTE]

Sounds like you've got a bad ISO.  Check the MD5.  Or perhaps burn on a slower speed.

---

### Post by CAPTAIN RON FL on 2004-11-11
I went with lowest burn rate. I will try to burn it with a different puter. I also tried to burn a copy of the live install and it would not boot in any of my 6 computers. I am looking for a linux distro to put on them,plus others for my fiends, as Billy's OS is driving me crasy with all the spy and ad junk, not to mention the other things going wrong. I have been reading a couple of post that said they were having cd buring problems and change over to a linx distro to burn them and they worked. I just need to know which distro I need to use and which program , how to do it as it is very different in linux. I used two different buring programs with the same results[Nero 6, Roxio 6]. Also I do not know how to check the Md5. When I down load it it is just a string of letters and numbers.  Any ideas???? I am so tired of making coasters. I was going to buy a rewritable disk but hwas told that they brake down too. Thanks , Ron

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=CAPTAIN RON FL]I went with lowest burn rate. I will try to burn it with a different puter. I also tried to burn a copy of the live install and it would not boot in any of my 6 computers. I am looking for a linux distro to put on them,plus others for my fiends, as Billy's OS is driving me crasy with all the spy and ad junk, not to mention the other things going wrong. I have been reading a couple of post that said they were having cd buring problems and change over to a linx distro to burn them and they worked. I just need to know which distro I need to use and which program , how to do it as it is very different in linux. I used two different buring programs with the same results[Nero 6, Roxio 6]. Also I do not know how to check the Md5. When I down load it it is just a string of letters and numbers.  Any ideas???? I am so tired of making coasters. I was going to buy a rewritable disk but hwas told that they brake down too. Thanks , Ron[/QUOTE]

What motherboard do you have?

---

### Post by CAPTAIN RON FL on 2004-11-15
I do not know. Some type of Intel made for emachine.  ](*,)

---

### Post by mr_ed on 2004-11-15
Don't know how to check the md5sum?
Download this program:
[http://www.download.com/SolidBlue-Win-MD5-Sum/3000-2381-10115916.html](http://www.download.com/SolidBlue-Win-MD5-Sum/3000-2381-10115916.html)

Open the ISO in it, and it should eventually give you a big string of numbers.  Compare that to the one here:
[http://releases.ubuntu.com/warty/MD5SUMS](http://releases.ubuntu.com/warty/MD5SUMS)
(I assume you'll use this one:  
a491903a2d2197651864dec3836d85e0  warty-release-install-i386.iso)

If that doesn't match up with what you got from the WinMD5Sum program, then you'll have to re-download the ISO.

---

### Post by Noggin on 2005-06-03
I am having the same problem.  I'll try another ISO later today or tomorrow, MD5 checks out fine.  I have failed in at least 3 different areas of the install from this CD.

f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso is the ISO I'm using.  

Compaq Presario 1245 laptop, 96 MB ram 333 MHz K6-2.  I've had nothing but trouble installing LInux on this machine, this is the 4th flavor I've attempted.  Mandrake 10.0 was the most successful so far (or was it Debian?) but all of my I/O devices were rediculously slow.  Floppy, CD, USB, PCMCIA, and maybe hard drive.  Keyboard was ok, but its such a low bandwidth device that maybe I just didn't notice.  It took nearly 10 minutes to copy a wireless card driver from the floppy to the hard drive.  In windows, all devices run fine.

Anyway, I'm going on a business trip on Sunday and I'm either going to have LInux on this machine once and for all, or its back to Windows it goes until the silicon turns to dust.

It also sometimes acts as though its a heat problem, I'm installing right now with the laptop sitting on a block of ice.

Error message now states, "Couldn't retrieve bsdutils" and I've seen something about adduser before too.  All errors occur during the "Install the base system" step.

CD burned at 4x speed as 1x wasn't available.

---

