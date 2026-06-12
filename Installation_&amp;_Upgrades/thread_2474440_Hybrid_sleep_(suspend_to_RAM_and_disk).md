---
title: "Hybrid sleep (suspend to RAM and disk)"
date: 2022-04-29
forum: Installation &amp; Upgrades
---

### Post by gansket on 2022-04-29
Searching for "hybrid" I just found an [old thread]("https://ubuntuforums.org/showthread.php?t=2450710") which wasn't answered, but is closed already.

The history: When I had an iBook more than 15 years ago, I got used to just closing it and re-opening at any time. It didn't matter if I forgot it and the battery went empty after a week, because it suspended to both RAM and disk. It took some time for saving, but it responded fast when re-opened. It took some time when memory was clear, but it also just continued where it was. Today again I started some long running task on my notebook running Ubuntu and forgot the cable. It turned off. When I activated it, it just rebooted! It is really not necessary that this task needs to be restarted. I want my computer to remember its state.

The current state: The Ubuntu experience is not good. I often do tasks like convert videos which take several hours, consuming much battery so it runs empty fast. If I forget to connect to ac connector, I have to boot and re-run. If I remember what exactly I did.

I did a configuration for hybrid sleep when using an earlier version of Ubuntu (currently I am using 22.04, could be that it was on 21.04 or similar), but it never ran reliably and had strange problems. So I didn't change the action on close-lid this time by now. In the older thread I linked above it was stated that only if battery is low, saving to disk is being done. This is not what I want. I want the notebook to hybrid sleep on close-lid. If you then leave the notebook closed for some days, the hibernate state will also end, battery being empty. If suspend to disk is not being done on the initial close-lid, the state will be lost and the computer will just boot.

Questions:

[LIST=1]
[*]Is there a fast and reliable way to achieve the behavior I want? I remember following several different instructions on several webpages when doing it on that previous Ubuntu Linux, most of them were not working fine.
[*]Is systemctl-hibernate working reliably on all relevant platforms? My current computer is a Thinkpad E570.
[*]Why is the hybrid sleep (suspend to both RAM and disk) behavior still not default installation? Not having such comfort by default, it is no wonder that people stay using other OS.
[/LIST]

Thank you in advance for helpful hints.

---

### Post by Dáire Fagan on 2022-06-02
It seems to work for me now but sometimes I will have problems resuming when I can see my system has power but nothing is displayed, that may just be specific to my hardware or something else in my configuration.

It has been awhile since my last install but I have some notes to complement the guide I followed. You should be able to set this up without following the guide but I am including here for reference:

[COLOR=#000000][FONT=&amp][https://mutschler.eu/linux/install-guides/ubuntu-btrfs/](https://mutschler.eu/linux/install-guides/ubuntu-btrfs/)

Also, a word of warning about Timeshift in the guide in case it interests you. It worked well for a time but I had to eventually remove it completely because it kept filling up my drive in error or there was some other issue with it so that I had to remove it completely.

[/FONT][/COLOR][B][COLOR=#000000][FONT=Arial]Enable hibernation from swap file[/FONT][/COLOR]
[/B]
[COLOR=#000000][FONT=Arial]*#Willi&#8217;s guide follows the swap file creation in *[/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]*Swapfile#Swap_file_creation*[/FONT][/COLOR]]("https://wiki.archlinux.org/index.php/Swap")[COLOR=#000000][FONT=Arial]* although he does not seem to use the command:*[/FONT][/COLOR][COLOR=#000000][FONT=Arial] dd if=/dev/zero of=/swapfile bs=1M count=512 status=progress[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]*#Compute the resume_offset according to *[/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]*Hibernation into a swap file on Btrfs*[/FONT][/COLOR]]("https://wiki.archlinux.org/index.php/Power_management/Suspend_and_hibernate#Hibernation_into_swap_file_on_Btrfs")
[COLOR=#000000][FONT=Arial]*sudo nano /etc/default/grub*[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]*#Get UUID of the /swap subvolume from:*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cat /etc/fstab[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]*#Edit the line: GRUB_CMDLINE_LINUX_DEFAULT="":*[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=<INSERT UUID> resume_offset=34818 quiet splash"[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]sudo update-grub and reboot, test with systemctl hibernate[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]*#No changes need to be made to initramfs*[/FONT][/COLOR]
 
**[COLOR=#000000][FONT=Arial]Desktop - Suspend and Hibernate at the same time -  RETURN TO THIS[/FONT][/COLOR]**
 
[COLOR=#000000][FONT=Arial]suspend-to-both[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]pm-suspend-hybrid[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]hybrid-sleep[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]#Enable &#8216;true&#8217; hybrid-suspend:[/FONT][/COLOR]
 
[[COLOR=#1155CC][FONT=Arial]http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html[/FONT][/COLOR]]("http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html")
 
**[COLOR=#000000][FONT=Arial]Laptop - Suspend then Hibernate[/FONT][/COLOR]**
 
[COLOR=#000000][FONT=Arial]sudo systemctl suspend-then-hibernate[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo nano /etc/systemd/sleep.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][Sleep][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HibernateDelaySec=3600[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo nano /etc/systemd/logind.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HandleSuspendKey=suspend-then-hibernate[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HandleLidSwitch=suspend-then-hibernate[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]systemctl restart systemd-logind.service[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]

---

### Post by GhX6GZMB on 2022-06-02
First, for some obscure security reasons, Hibernate is disabled on all variants of Ubuntu. You'll need to install and set it up first.

Second, I'm running Lubuntu which has a different desktop.
But I have the following setup:
- Power Low: Hibernate.
- Lid close: Hibernate when on battery, Suspend when on AC.
Works well, I've no problems.
One scenario I haven't tested: what happens if you pull the plug when the laptop is suspended. Will it automatically Hibernate when battery is low? Dunno, I'll have to try it at some point.

---

