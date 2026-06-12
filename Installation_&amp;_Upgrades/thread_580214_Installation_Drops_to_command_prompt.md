---
title: "Installation Drops to command prompt"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by cdnronin on 2007-10-18
I am a newbie to linux. I am attempting to install Ubuntu 7.10 to a Acer 210 (800MhzCPU). When I get the Ubuntu Login screen, I select install or safe graphics mode. Either way I'm dropped to a command prompt 

[FONT="Arial"]BudyBox v1.1.13. (Debian 1:1.1.3-5Ubuntu7) Biuilt in Shell (ash)
(initramfs)_[/FONT]

Anyone have any suggestions for me?

---

### Post by mocoloco on 2007-10-18
Does it load anything first before giving you the command prompt?  If so, what are the last few lines?  That may give a clue as to what's going wrong.

---

### Post by retrow on 2007-10-18
I was having a similar problem, but I had a few more options. I chose to "install in text mode" instead of command prompt. If you are able to get in text mode, its quite easy after that. Just make sure you do the partition correctly. In text mode the screen halts for a very very long time when it reaches "Configuring apts". I did the mistake of rebooting out of frustration. But after about 20-30 minutes, the screen does proceed (in your case it might be more or less) and the installation is successful.

When you reboot the system, it is possible that your display would go completely blank. Press alt-F1 or ctrl-alt-F1, and you should be able to see the boot up text, and eventually your login screen.

Good luck!

---

### Post by yellowfish on 2007-10-18
I have the same issue with the ubuntu 7.10 CD.  The Xubuntu CD won't even boot and the Xubuntu 7.10 RC cd loads until it's installing programs then freezes at various points each time I try.  

I have
PC Chips MB M811 ver 3.1
AMD 1.8 GHz Duron
1 GB DDR PC333 from Crucial
ATI Rage 128
IBM-DTLA-307045
Quantum Fireball CR8
Sanyo CD-ROM CRD-1

---

### Post by yellowfish on 2007-10-18
I also found this post
> **overdrank said:**
> Hi and yes if you follow those instructions it will just allow the live cd to continue ( so you won't be installing unless you want to)
Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you receive the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot. 
You may also try to use graphics safe mode. Good luck!

Edit and  I might also have you checksum the disc
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

on [this thread]("http://ubuntuforums.org/showthread.php?t=573419") and am currently making what looks like progress so you might give that a shot.

---

### Post by cdnronin on 2007-10-18
Well, tried the above suggestions. First, I tried to verify the iso has but I couldn't find a reference hash to compare. Then I followed the instructions for modifying the script after pressing F6. The only probelm I ran into was the "modprobe piix".  After pressing Enter, an error came up saying "cannot find module". The I ran the install which resulted in the command prompt again. But with a difference  a series of command line messages as follows:

hdc: lost interrupt
hdc:ATAPI 20X CD-ROM Drive, 2048kb Cashe, DMA
Uniform CD-ROM Driver  Rev 3.20
hdc: lost interrupt
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
hdc: lost interrupt 
ide-cd: cmd 0x1e timed out
hdc: lost interrupt

this "lost interrupt" message continue for about 60 minutes before lost patience and shut it off.

---

### Post by jdude1284 on 2007-10-18
modprobe piix will not work because the piix driver has been deprecated.

have you tried using the alternate CD and doing a text installation?

you could also try modprobe ata_piix instead and see if that helps you although this driver is usually by default. 

do you have any more detailed specs then what you've posted above? those are kind of vague -- who makes your mother board, what kind of processor, etc.

---

