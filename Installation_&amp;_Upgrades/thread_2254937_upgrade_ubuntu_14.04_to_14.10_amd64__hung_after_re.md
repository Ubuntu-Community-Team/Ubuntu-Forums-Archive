---
title: "upgrade ubuntu 14.04 to 14.10 amd64  hung after reboot"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by sj1astroboy on 2014-12-01
desktop :   HP 810 160     preinstalled  Window 8.1 64-bit
dual boot  Ubuntu 14.04 amd64

was working fine for 4 months.  Then did an upgrade  to 14.10.

when reboot,  hp810-160  only got into  the 'hp' logo & hung.
reboot while pressing 'esc' or F9 or F10 or F11 or F12  would  not get into  'boot menu'.

did i wipe out the bios ?

any helps or hints will be appreciated.

---

### Post by ajgreeny on 2014-12-01
How did you upgrade; by using the package manager (or command-line) or did you use a burned DVD or USB?

---

### Post by sj1astroboy on 2014-12-01
i did it on command line  per instructions from :
[http://www.techrepublic.com/article/pro-tip-how-to-easily-upgrade-ubuntu-14-04-to-14-10/](http://www.techrepublic.com/article/pro-tip-how-to-easily-upgrade-ubuntu-14-04-to-14-10/)

command is :   do-release-upgrade

the upgrade process, ie, downloading the packages & unpacking packages seems to go very smooth.
toke about 1.5 hours download & 1.5 hours unpacking.

---

### Post by sj1astroboy on 2015-01-02
reset 'cmos' .  now boot into windoss 8.1 OK. in the process of reinstall ubuntu 14.04.  not dare to 'upgrade' any more.

Reset 'cmos' proceedures:
1) power down the desktop
2) leave the original Windows disk in
3) on the motherboard, find a 3-pin connector, marked 'cmos reset' 
4) pull out the jumper, put it on the other position
5) power up the desktop   (you wtll see a message saying  'reset cmos to default ...' on the screen
    it will continue to boot into windows.
6) shut down windows
7) reposition the jumper to it original position

---

### Post by MAFoElffen on 2015-01-02
So wait... The system is UEFI. You reset the CMOS and now it goes to Windows without going to the Grub2 Menu first? Or does it and you are just nervous to start Your Linux instance?

---

### Post by sj1astroboy on 2015-01-04
You are right.  after cmos reset, it boots into windows ... press F10  to get cmos setup.
now,   enbale legacy boot + disable secure boot.   i booted  on  CD-drive with u14.04 live CD
& reinstalled from there.   during install, loaded grub2 on  sata1  (sata0 is the origianl W-8.1).
on  next boot, set cmos to boot from 'ubuntu'.

some how, the 14.10 'upgrade' screwed the cmos settings :)
any body knows why ?

---

