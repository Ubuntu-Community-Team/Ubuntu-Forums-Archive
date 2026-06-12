---
title: "apt-get update problems"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by acornbrain on 2010-02-17
I had this in the "Hardware & Laptops" category because I thought I had a display problem. Can't boot normally all of a sudden, only black screen.

However, I CAN boot from Live CD...

here is some of my flailing about trying to fix this situation:
this is me booting liveCD than mounting my hard drive, and switching to it's root. trying to get apt-get to upgrade/clean/update etc, blocked at every turn...

     ```
Code:
     cubuntu@ubuntu:~$ sudo chroot /media/disk
root@ubuntu:/# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
root@ubuntu:/# mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': Input/output error
root@ubuntu:/# rm /var/cache/apt/archives/partial
rm: cannot remove `/var/cache/apt/archives/partial': Input/output error
root@ubuntu:/# cd /var/cache/apt
root@ubuntu:/var/cache/apt# ls
apt-file  archives  partial  pkgcache.bin  srcpkgcache.bin
root@ubuntu:/var/cache/apt# cd archives
bash: cd: archives: Input/output error
root@ubuntu:/var/cache/apt# cd/var/cache/apt/archives
bash: cd/var/cache/apt/archives: No such file or directory
root@ubuntu:/var/cache/apt# mkdir archives
mkdir: cannot create directory `archives': Input/output error
root@ubuntu:/var/cache/apt# apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory
root@ubuntu:/var/cache/apt# apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory
root@ubuntu:/var/cache/apt# mkdir -p /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives': Input/output error
root@ubuntu:/var/cache/apt# cd /var/cache/apt/archives
bash: cd: /var/cache/apt/archives: Input/output error
root@ubuntu:/var/cache/apt# mkdir /var/cache/apt/archives
mkdir: cannot create directory `/var/cache/apt/archives': Input/output error
root@ubuntu:/var/cache/apt# pkill synaptic
Cannot find /proc/version - is /proc mounted?
root@ubuntu:/var/cache/apt# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
root@ubuntu:/var/cache/apt# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/var/cache/apt# apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory
root@ubuntu:/var/cache/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/var/cache/apt# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
root@ubuntu:/var/cache/apt# cd /var/cache/apt/archives
bash: cd: /var/cache/apt/archives: Input/output error
root@ubuntu:/var/cache/apt# ls
apt-file  archives  partial  pkgcache.bin  srcpkgcache.bin
root@ubuntu:/var/cache/apt# cd var/cache/apt/partial
bash: cd: var/cache/apt/partial: No such file or directory
root@ubuntu:/var/cache/apt# cd var/cache/apt/archives
bash: cd: var/cache/apt/archives: No such file or directory
root@ubuntu:/var/cache/apt# mkdir archives
mkdir: cannot create directory `archives': Input/output error
root@ubuntu:/var/cache/apt# rm /var/cache/apt/archives/lock
rm: cannot remove `/var/cache/apt/archives/lock': Input/output error
root@ubuntu:/var/cache/apt# 
still researching online, but so far I have not found anyone with the exact same problem as me, so none of their solutions are working...

```
-brian

---

### Post by Sef on 2010-02-17
1) What is your system specs, espcially your graphics card?

2) Did you install any proporietary drivers for your card?

3) What did you do just before the problem started?

---

### Post by acornbrain on 2010-02-18
Sef, thank you for helping.
 
#1. I'm at work right now, and not at my Ubuntu machine, so I will get you that info later. Is there a terminal command that I can run that will list that information so I can copy it to you?
 
#2. I don't remember having to install any special drivers for the graphics card.
 
#3. I don't know what event started all this. The last day my PC was working normally, I was trying to watch a wmv movie with the totem movie player. The move opened and "ran" for the entire length of the movie, but there was no sound and no picture.
 
I went to the ubuntu forums and searched on wmv movies, and I found some posts saying that mplayer was better, so I tried to add the program with add/remove. It wouldn't install. I tried apt-get and it still wouldn't install. Perhaps that was because of the same archives/partial error that I'm still getting.
 
I restarted, or shut down and rebooted (can't remember which), but was never able to boot successfully again. I tried my Ubuntu Live CD, and that seemed to work fine, but I can't boot up without the CD.
 
-brian

---

### Post by Sef on 2010-02-19
>  cubuntu@ubuntu:~$ sudo chroot /media/disk

Why were you doing this command?

---

### Post by acornbrain on 2010-02-20
[FONT=Times New Roman]I was follwing advice I found online, which said:[/FONT]
[FONT=Times New Roman]1. Boot Live CD[/FONT]
[FONT=Times New Roman][/FONT][FONT=Times New Roman]2. Mount the laptop's hard drive[/FONT]
[FONT=Times New Roman]3. Open terminal[/FONT]
[FONT=Times New Roman]4. type:[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]sudo chroot /media/disk[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman](this is the location of my hard disk mount, I assume the command is switching to the root user of that file system)[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]apt-get update[/FONT]
[FONT=Times New Roman]apt get upgrade[/FONT]
[FONT=Times New Roman]apt-get dist-upgrade[/FONT]
[FONT=Times New Roman]exit.[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]That's all I know. As you can tell, I was not able to complete the advice because of the errors I was getting.[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]I'm still pretty new to Linux, I am more familiar with Windows.[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]-Brian [/FONT]
[FONT=Times New Roman][/FONT]
[FONT=Times New Roman]PS-My system specs[/FONT]
[FONT=Times New Roman]9.04[/FONT]
[FONT=Times New Roman]Kernel 2.6.28-11-generic[/FONT]
[FONT=Times New Roman]gnome 2.26.1[/FONT]
[FONT=Times New Roman]244.8 MiB[/FONT]
[FONT=Times New Roman]Mobile INTEL Pentium III 1200 Mhz[/FONT]
[FONT=Times New Roman]graphics card: ATI Radeon Mobility M6 LY[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman][/FONT][FONT=Times New Roman] 


[/FONT]

---

### Post by acornbrain on 2010-02-20
PLEASE ANYBODY?
 
I was very happy with my Ubuntu Jaunty. If at all possible I want to perfom a fix using the Live CD and get it back to normal.
 
When I try to boot without the CD, it *seems* like it's trying to boot (indicator lights blinking, hard drive noises, etc), but I have no display at all so I can't be sure exactly what is going on. I can even get it to 'restart' by hitting ctrl-alt-del.
 
I realize part of my issue is probably my display setup. (see: [http://ubuntuforums.org/showthread.php?t=1407927](http://ubuntuforums.org/showthread.php?t=1407927)) There has always been a slight lag between the laptop and the vga monitor. What my fear is, is that if the laptop's screen worked, I would be able to see SOMETHING on there, error messages or a blinking cursor or something. Maybe there's a grub menu there that I can't see. I would also be able to see what I was typing. But something is going wrong with the boot and hence the external monitor never fires up. 
 
I suppose I can remove all my personal files off there, and re-install 9.04 from the live cd, but I want that as a last resort, because it was a major PAIN IN THE NECK to get it all set up the way i needed it with my wireless adapter driver and such. All that effort can probably be done again, but I'm sure not looking forward to it!!!!
 
Sef, I thank you for trying to help, but my thread doesn't seem to be getting any other responses besides yours....perhaps I should move it to another forum?
 
HELLLP!!
 
-brian

---

### Post by acornbrain on 2010-02-22
Well, I "solved" it by rescuing my files and re-installing the OS.
 
Oh well. Could have been worse.

---

