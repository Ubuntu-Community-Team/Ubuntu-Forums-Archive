---
title: "Installation on Via Esther processor, CN700 chipset"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by John Bergenholtz on 2006-11-05
Does anybody have expericence with installation of 6.10 desktop on this hardware? I have tryed 3 times now, but the installer hanges up.

Thanks in advance for any tips.

John

---

### Post by John Bergenholtz on 2006-11-10
any suggestions?

---

### Post by John Bergenholtz on 2006-11-12
Still trying to get the os running ...

now i have changed to 6.06, but same result. I get various error messages, like write to a read-only mount, error in unpacking the archive.

Appended are some logfiles, i could get from the computer.

---

### Post by duister on 2006-11-21
I see you have the epia EN12000 board, and you are using an ATA disk. I have the Epia EN 15000  board myself. 

I tried to install ubuntu on it as well, a while ago. And i didn't succeed, but i thought it was because of the sata disk. (i could however install slackware on it)

Which installationdisk did you use? I heard that many people had probs when using the standard installation cd. you might wanna try the alternative installer: you can download it for example at [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso)

I don't know what bios version you have. 1.05 had some problems with the mouse, and it hang on a win2K installation. and 1.07 fixed it.

I was very disappointed with this board. I wanted to use it as a low powered desktop, and use linux on it. Let's face it, Via does a lousy job when it comes to support linux. The graphics drivers only work with some beta drivers from openchrome project, the sata controller is not really supported..etc. 

I already gave up to use this board as a linux desktop. And turned it into a non-graphical server, with openBSD 4.0 . And now i'm actually satisfied with it. openbsd installed without any problems. And it does it's job as file/mail/sftp/firewall server, and it's very stable. Also the encryption instructionsets are supported with openbsd 4.0 >

Maybe you can get it working with ubuntu. Let me know whether the alternative installer worked :p

Let me give me some suggestions on using this board. If you really wanna use this board as a desktop you should buy a lvds connection for dvi-out, or buy a cheap pci graphics card, because the vga-out is terrible on this board when using 1024x768 or higher resolution. It will hurt your eyes.

---

### Post by John Bergenholtz on 2006-11-22
Good news: it is solved.

Reason was a bad connected DDR-module. The live-CD was working, but not the installer. Windows was working, but Firefox 2 crashed sometimes. Finally i had to search fore a hardware reason, i did not believe in so many bugs in the software.

The memtest, included on the ubuntu boot menue, found a memory error after about 1h of searching.

My main idea for this machine is, to get a file server for private use. The desktop performance for this is not important.

Anyway, thank you for the tips.

---

### Post by RFScheer on 2006-11-27
I've ordered a Via E12000EG mini-ITX board for a robot project and am hoping to install 6.10 on it.  It has a SATA 2.5" hard drive.  Are you using SATA successfully?  Anything else I should know first?  Thanks!

---

### Post by thorgal on 2006-11-30
Hi there,

I also tried ubuntu install on my epia en12000. No success, I gave up after a couple of attempts and hacks. But it was more out of curiosity since I heard many good things about this distribution. I am a debian user and the debian install works without any fuss! Since I don't have any CD/DVD drive plugged to the mobo, I use USB installation. Debian is very very handy with this sort of install. See the debian installation pages if you want to try. You might eventually change the apt repository paths to the ones for ubuntu. But I guess it would most likely result in messing up the package dependencies, etc. I would not recommend it. Debian does anyway a fair job on this mobo. The debian-installer lets you choose between standard desktop / server / what-not install options. As long as your internet connection is alive, the minimal debian install deos wonder :)

By the way, I use a SATA2 HD, although I read that it only supports SATA1 protocol. This is not a big issue, it just works anyway ;)

---

### Post by RFScheer on 2006-12-04
I am trying various installs on my new EN12000G.  Edgy of all types causes kernel panic early in the install. 

Breezy installs perfectly.  I really need Edgy working to be compatible with my main comp.

---

### Post by RFScheer on 2006-12-05
Ok, it's pretty simple.  A couple of people on the launchpad forum suggested using the option, acpi=force , during install and that's all it took.  Just hit that F6 key and add "acpi=force" to the end of the std options.  I've verified this with Xubuntu desktop cd install.  I love silent PC's!

---

### Post by Xemanth on 2008-02-17
I'm going to buy EN150000G board in few weeks.

Can I get it working with Gutsy 100% stable 24/7?
Does powersaving functions work properly?

edit: General impressions, whats working and whats not. Thats what I would like to hear too.

---

### Post by [h2o] on 2008-02-24
> **Xemanth said:**
> I'm going to buy EN150000G board in few weeks.

Can I get it working with Gutsy 100% stable 24/7?
Does powersaving functions work properly?

edit: General impressions, whats working and whats not. Thats what I would like to hear too.
I have the EN12000 which is almost the same, just slower and has no fan.
It is stable when it is acting as merely a webserver running lighttpd and mysql. When it is used to watch movies it hangs a lot. Unfortunately no one seem to know why yet.
Powersaving seem to work fine though.

Note: I am running Debian, not Ubuntu.

---

