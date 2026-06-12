---
title: "Install problem; /bin/sh: can't access tty"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Pai on 2007-05-20
I recently downloaded Feisty (7.04 i386), and was anxiously awaiting the installation.

I popped in the live CD I created, and chose to Install in safe graphics mode. Within a few seconds, I received the following message:

> BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initram fs)[   37.455437] ata5.01: failed to set xfer mode (err_mask=0x4)
[  73.271566] ata5.01: failed to set xfer mode (err_mask=0x4)
[ 109.079798] ata5.01: failed to set xfer mode (err_mask=0x4)
[ 109.079798] ata5.00: failed to set xfer mode (err_mask=0x40)
_

There is blinking cursor following the message, but no input is recognized. At this point I am forced to manually shut down the computer.

What does this error message me, and what can I do to solve the problem? Right now I can't really do anything with this live CD. I have installed Edgy and Dapper in the past, but never had this problem.

Some hardware info:
[img]http://img413.imageshack.us/img413/6343/untitledhx1.png[/img]

Thanks in advance.

---

### Post by confused57 on 2007-05-20
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

---

### Post by Paul196234 on 2007-05-20
Response during installation is the same when I try 7.04 here. First I blamed the JMicron, but all the devices were recognised... without "quiet" option I watched the install process, the SATA HD was listed, the PATA burner and HD were listed as SCSI device... then the install process stopped.

I also tried to add via F6 the options "failsafe" and "all-generic-ide", with similar results.

My hardware is correctly set up, Windows XP works, Windows Vista works, even the outdated Caldera DR-DOS can access the harddisks and CD-ROM.

My guess is that, Caldera uses BIOS functions to access to the boot media (i.e. CD) so it can handle SATA, PATA etc without special drivers. We have to blame UBUNTU that it provides drivers what are used too early in the boot process.

It reminds me of the old question: "Can God create a stone so heavy that HE cannot lift it?"  -- Here it would sound: "Can UBUNTU boot from a drive for which it has no drivers?". The answer is yes, UBUNTU cannot configure its own starting device.

I used UNIX systems long tome ago, on machines like PDP-11 and 386 IBM (AIX). From time to time I try to install LINUX on my private computers, but always there's a serious hindrance. The Terratec soundcard is not supported, the laptop's Synaptic touchpad is not supported, no driver for the Volari graphics etc..at least the install CDs booted on those machines and told me the reason. The present LINUX / hardware is worse, the install CDs of UBUNTU, KNOPPIX etc start but hang without any further explanation on my dual core.

---

