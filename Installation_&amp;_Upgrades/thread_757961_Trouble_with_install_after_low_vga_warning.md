---
title: "Trouble with install after low vga warning"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by doowylloH on 2008-04-17
I'm really sorry if this has been already been posted but I've been searching all morning trying to find an solution to my problem.

I downloaded and burned the .iso for Ubuntu 7.10 and the disc boots up to the menu. I did a CD Integrity Check and everything came back fine. I click install and I see 4 lines show up all saying [Okay] (i believe). After that it will load up a warning message saying that it is putting me into low graphics mode and it gives me 3 options configure, cancel, continue. One time I tried Configuring and didnt really have too many options so I went through and just hit Continue then that screen goes away and leaves me with a blank screen or the screen with 4 lines of text with a flashing cursor and that is it. It will stay there for hours.

I have a nvidia 8800GT OC, and I heard down the line that people have been having trouble installing linux with this card  installed?

---

### Post by wpshooter on 2008-04-17
Are you trying to install from the Live (desktop) CD version or the ALTERNATE (text based) CD version ?

Have you tried installing using the safe graphics mode parameter ?

---

### Post by doowylloH on 2008-04-17
I'm assuming it's the GUI based version. I should try the text one, thats the one I read about and watched all the videos on.

And I dont remember seeing the option for safe graphics mode

---

### Post by Partyboi2 on 2008-04-17
Once you have installed ubuntu using the alternate cd you can try installing the lastest driver ffrom nvidia website.
If you have a working internet connection you can boot into recovery mode and then at the prompt download the driver
for 32bit
```
 
wget [http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)

```
for 64bit
```
 
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run)

```then after it has finished downloading start the installer by typing the correct one listed below.
32bit
```
 
sh NVIDIA-Linux-x86-169.12-pkg1.run

```
64bit
```
 
sh NVIDIA-Linux-x86_64-169.12-pkg2.run

```
once you have finished the installer
type
```
 
startx 

```or reboot into normal mode.

---

