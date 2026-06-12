---
title: "Upgrade 16.04, running in low graphics mode. AMD Drivers or Low storage?"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by Mike1977 on 2017-02-19
ASUS P8 Z77-V Motherboard

Intel® Core™ i7-3770 CPU @ 3.40GHz × 8

Gallium 0.4 on AMD TAHITI

Kingston 120GB SSD/ 1TB HDD

I'm able to boot into GRUB, however Windows is now missing (dual boot). I'll get the splash screen for a second, then randomly it will either direct me to "The System is running in low graphics mode", or will go to generic terminal.
From recovery, I've tried "Clean", which brings me to same error message, but bigger font. I've tried "repair broken packages", same result. I've tried failsafex as well, which gives me multiple theme parsing errors, and I have to manually reboot.

```
lspci | grep VGA
```
AMD/ATI Tahiti XT Radeon

Simply running
 ```
sudo apt-get install fglrx
```
gives me error "Package has no installation candidate" I do see that some suggest going to AMD site, and downloading driver, then installing. I have no way of getting online from this machine. 
One thing that does look curious is
 ```
df -h
```

Shows that ```
/dev/sda1
``` is showing 48gb of 54gb is being used, equaling 94% of disc. This looked odd to me, because my Ubuntu is fairly minimal.
So I ran ```
rm ~/. xsession.errors
``` ( purely based on a hunch, but I don't know if it is x-session errors) and received "No such file or directory exists" (perhaps I'm entering the command wrong).

I ran a full backup with Ubuntu's stock backup utility, before upgrading through Software upgrade in GUI. I stored the back-up file in my Video folder (because I selected backup process to ignore video folder) So at this point I'm not sure what direction to go. Should I move forward, and try to resolve 16.04.2. Or can I restore 14.04 from back-up via terminal? And also, what happened to my Windows partition? I don't have a live cd, and no Windows to run Unebootin. I do have an old USB with 12.04 installation set-up. 
```
uname -a
``` 3.13.0-108-generic #155-UBuntu X86_64
```
Xorg -version
```  X.Org  X server 1.15.1

I'm going in two different directions here with uncertainty. 1. Possible graphics driver defect  2. Not enough room on Disc, and thus kicked down to low graphics mode.
```
du -sc /*/* |sort -g
```
Shows a few things interesting:
175008 /opt/google
223056 /var/cache
339180 /opt/wine-staging ((While on 14.04, I would randomly get error pop-ups regarding Compholio Wine)) 
There are outputs much bigger, and ones much smaller, but these particular ones looked unimportant to the system build.

Also:
```
du -sc * |sort -g
```
Shows the 4 biggest folders are 
20266528 Videos  (I don't have very many videos, so this must be mostly the back-up file that I have saved in Video folder as default setting))
5884876   Downloads
108208     installer linux.sh
108156     installer_linux.tar.gz

---

