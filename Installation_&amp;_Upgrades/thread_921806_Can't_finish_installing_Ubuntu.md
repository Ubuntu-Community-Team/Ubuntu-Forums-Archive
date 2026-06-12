---
title: "Can't finish installing Ubuntu"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by genros on 2008-09-16
I read through some of the posts and none of them helped me.

I successfully installed Ubuntu 8.04.1 LTS Desktop Edition to my computer with a CD. I then rebooted my computer. I then get to a screen asking me which operating system to use (I also have Vista installed). When I choose Ubuntu, It gives me the Ubuntu loading screen and then opens a command screen. I don't get anything else. How can I get to the Ubuntu installer?

I read that changing SATA ports helped some people, I did that to mine and it made no change.

---

### Post by Pumalite on 2008-09-16
Why do you ask how can you get to the Ubuntu installer after saying that you successfully installed Ubuntu? You probably installed the Server Edition. If that is the case and you want a GUI; try:
sudo apt-get install ubuntu-desktop

---

### Post by genros on 2008-09-16
It is the Desktop Edition. The CD Even says so. As for if it's installed or not, I believe that I partially installed it. I installed it enough for my computer to recognize that there is a second operating system on it but when I run Ubuntu, I don't get to a desktop. Just a command screen.

Also, if I type in any command, nothing happens. Except for a few commands such as when I type in "help". In a nutshell, nothing gets me away from the command screen.

---

### Post by genros on 2008-09-16
the top picture is my computer loading Ubuntu. The bottom picture is what comes next. It's that screen that I can't get past.

---

### Post by Pumalite on 2008-09-16
Try reinstalling with the Alternate CD

---

### Post by genros on 2008-09-16
Alternate CD?

I only have the one Ubuntu.com sent me.

---

### Post by Sef on 2008-09-17
Read this [thread]("http://ubuntuforums.org/showthread.php?t=765195") to help with your busybox problem.

> Alternate CD?The alternate cd is a text-based installer.  It is fairly easy to use.  You can download it from the [Ubuntu Download]("http://ubuntu.com/getubuntu/download") site.  You have to check the box below the green arrow.

---

### Post by sabbathpriest on 2008-09-17
I have the same problem and I have tried Desktop 32 & 64, Server 32 & 64 and alternate 32 & 64. I am reading all I can about it but apparently the issue is apparent only with certain hardware (ASUS Motherboards, A8V-X or A8V-XE for sure). Unfortunately I am not familiar with many of the terms used on the bug report forums and I don't want to post there as it seems to be intended for developers. [This thread]("http://ubuntuforums.org/showthread.php?t=720093&highlight=busybox") does have some pointers. 
I will have some time to experiment further during the weekend and will post back on this same thread. Hopefully someone with solid Linux knowledge will be able to pick up on it and help us. I posted here now because I've noticed that when this issue is reported there are a lot of quick dismissal responses, but the issue is real, as reported on the [ubuntu launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129817")

---

### Post by Pumalite on 2008-09-17
I took a look at the link you posted to launchpd. A lot of the issues seem to be answered there. Unfortunaly Ubuntu doesn't like some hardware, but you can try some boot parameters.

---

### Post by sabbathpriest on 2008-09-20
[COLOR="Red"]**[CENTER]**WARNING: I am using Sidux NOT Ubuntu. They are both based on Debian and they both have the same identical issue with Busybox on certain motherboards. This worked for me**[/CENTER]**[/COLOR]

OK, I found  a way to fix the busybox issue on my Asus A8V-X motherboard:
1- I changed the BIOS settings from SATA controller to RAID. Saved and continue to boot. It took a while.
2- When I got to the Busybox prompt I typed ```
exit
```. I got to the GUI login.
3- After logging in I changed the GRUB menu.lst (/boot/grub/menu.lst) as follows:
Erase all after ```
quiet splash
``` and replace with ```
apci=off pci=nomsi
```

Now I can boot normally, and I can see all the kernel messages scrolling by while the box is booting.

---

### Post by genros on 2008-09-22
Switching my BIOS to RAID was all I had to do. Now it works just fine.

---

