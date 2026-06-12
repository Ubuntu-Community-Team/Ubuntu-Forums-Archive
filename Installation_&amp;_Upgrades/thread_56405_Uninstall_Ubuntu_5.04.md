---
title: "Uninstall Ubuntu 5.04"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by amclpreston on 2005-08-12
Hi

I installed Ubuntu 5.04 from a Cd on a mag. And then found that it wouldn't recognise the modem on my laptop.

See [http://www.ubuntuforums.org/showthread.php?t=43539&highlight=acer+527](http://www.ubuntuforums.org/showthread.php?t=43539&highlight=acer+527)

I've been running back and forth between home and the internet computers at the local library trying to sort this, and would now just like to remove Ubuntu. and restore from Windows XP. I don't know much about Linux, or command lines, I got to somewhere in Ubuntu and tried entering fdisk but it doesn't seem to recognise it. 

Has anyone uninstalled Ubuntu, and could they talk me through it to the point where the system recognises, and loads from my Windows XP cd. I got the fdisk bit above from the Unistall Linux screen at Microsoft

Andrew

---

### Post by sbassett on 2005-08-12
Ubuntu Linux is an OS, so as such, there is no "uninstall" method. This would be like asking how one would uninstall windows. If you have followed the entire setup on the refered site [DialupModemHowto - Ubuntu Wiki](https://wiki.ubuntu.com/DialupModemHowto) , and there are no other alternatives, then simply place your Windows CD into the drive and reboot. This would be a last resort, and I hate to recomend anyone going back to Windows (especailly ME).

---

### Post by amclpreston on 2005-08-12
Hi

The link for How to dial-up presupposes that the system on the PC has actually recognised that a modem exists on the PC. I tried the suggestions about finding if , where, and fropm whom a modem driver might or moght not exist for this laptop, and got lost as soon as the guidance descended deep into the technicalities. The laptop is an Acer 527TE. from memory when Windows was on it, the modem is a Lucent/AMR softmodem. 

As I got lost in the technicalities, and just needed something that wasn't pretty, or wonderful, or really cool, but does in fact just work, and allows me to connect to the internet..., I decided to return to Windows. 

When I loaded Ubuntu 5.04 everthing got wiped, its in one partition I think. 
When I try to intervene in the start-up process, I get taken to some kind of menu screen about what I want to load, a choice of three things all related to Ubuntu. From somewhere else on the internet, this looks like something called Grub amending the master boot record, and overides anything that I want to do. 

The Microsoft helpsite has some instructions on uninstalling Linux, Google on 'uninstall linux' and its on the first page, but when I type in fdisk to start the process of overwriting the Linux/Ubuntu partitions, the system doesn't seem to recognise the command. So I 'm not really sure that i'm issuing the right command, or from the right place. So i'm stuck.

Which is why, if someone has actually uninstalled Ubuntu 5.04, could they talk me through it from the point at which Ubuntu declares itself , and the nice brown screen comes up, and it does that really cute little drum-roll. I love it really, but its got to go...

Andrew

---

### Post by sbassett on 2005-08-12
If you are trying to "remove" Ubuntu linux, and replace with Windows XP, merely boot off of the XP cd. That will take you into the install process for XP, then wipe out any "UNKNOWN" partitions it finds. There is no uninstall, though. Just overwrite. This is bascially what FDISK does as well. This will change the partitions/partition table.

---

### Post by amclpreston on 2005-08-13
Last night, I got down into root user/Terminal from the system tools menu.
I tried fdisk, but no matter how I played around with it, but couldn't get it to delete partition. I then found cfdisk and tried that. It seemed to work and I  deleted every partition.  

I then did Ctrl+Alt+del to restart, pressed F12 to get into the multi-boot boot menu to go to the CD-Drive first, and resumed. 

What came up on the screenwhen.....

GRUB Loading stage 1.5

Grub loading, please wait....

Error 22


and that's it, eveything is stopped, locked up completely.


Any ideas how to resolve this. 


Andrew

---

### Post by heimo on 2005-08-13
Yes, you have now successfully removed Ubuntu and that's why it won't load anymore, including last stages of Grub. All you need now to install other operating system is to boot from CD. Go to BIOS settings (pressing F1 or F10 or DEL button at very beginning of POST), choose CD-ROM as your first boot device and insert operating system install CD into the CD-ROM drive. Good luck.

---

### Post by Buffalo Soldier on 2005-08-13
From my past experience in re-installing WinXP, the easiest way to remove Ubuntu is to simply re-install WinXP. Just follow the steps by Sbassett.

If you were dual-booting (Ubuntu - WinXP) before this. And want to preserve your current WinXP data and partitions. What you should do is after booting into WinXP Install CD, choose Recovery Console. That will take you to a MS Windows command line. Key in [b]fixmbr[]/b] and ENTER. That should make your system able to boot directly to WinXP.

Please search [b]fixmbr[]/b] at google for further readings.

p/s: Do you have any experience in installing WinXP. If not, I would suggest you take it slow and read the instructions carefully.

---

### Post by amclpreston on 2005-08-13
After power-on, what comes up is..

Enter <F2> to enter setup, <F12> to enter Multi Boot Selection Menu..

Only those 2 keys seem to have any effect, otherwise the machine just proceeds onwards ...

So, I enter F12 and set the thing to boot from CD and the system comes out of that..

shows..

Initializing Intel Boot Agent Version 2.6 (build 004)
Press Ctrl & S to enter the Setup program...

then proceeds onwards to..

GRUB loading stage 1.5




Help..?

Andrew
Grub loading, please wait....
Error 22

---

### Post by heimo on 2005-08-13
[QUOTE=amclpreston]
So, I enter F12 and set the thing to boot from CD and the system comes out of that..
[/QUOTE]

Do you have bootable CD (Windows install CD) in drive when you do this? Grub cannot prevent you from booting from CD as it's on hard disk and won't be loaded if BIOS chooses to boot from CD. But if it fails to boot from CD, it probably tries other boot devices, including hard disk - that's the usual behaviour.

---

