---
title: "How to install ubuntu"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by john_mattson on 2015-11-09
Hi,


Iwanna install ubuntu 15.04 but I have encountered some problem. Ithink the problem is about partitioning and allocating. I have 6partitions on my harddrive. On my harddrive it stands: 




Disk0


partition1: 100MB. Working  efi-systempartition. 
Partition2: 900 MB working  recoverypartition.
Partition3: C:100 GB ntfs.working  systemstart, swap, kraschdump, primärpartition, 
partition4: 85 GB, not allocated
Partition5: data D: , 265 GB. Ntfs. working primary partition. 
Partition6: 15 GB. Working . Recovery partition. 


Theterms may not be exact since i don't have an operating system inenglish. 
Ihave windows 10 and I wanna make a dualboot. 


Anyidea what I should do?

---

### Post by TheFu on 2015-11-09
a)  support for 15.04 ends in 2 months. 15.10 support ends in June. Perhaps you really want 14.04.1 which is supported into 2019?

b) Please boot off a live-boot linux distro,  open a terminal, and run  **sudo parted  -l**.  Copy/paste the results back into this thread.  The output created by the boot-repair tool would provide much more useful information.

---

### Post by Bucky Ball on 2015-11-09
Welcome. All of what TheFu said previously. Provide the output of that command TheFu gives, but what you have as 'partition 4: 85Gb not allocated' looks like the place to install. First the output. 

[This link shows you how to install]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"), but it will be a bit different in your case as we need to take into account what you already have there, so best to discuss here first. :)

What make/model of machine and how much RAM?

---

### Post by yancek on 2015-11-09
In your initial post you show your first partition as an EFI partition so I would suggest that you read through the link below on dual-booting Ubuntu/windows in UEFI.  If you do not install Ubuntu UEFI with windows UEFI, you will have nothing but problems.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by john_mattson on 2015-11-13
[FONT=Verdana, sans-serif]Hi,[/FONT]


[FONT=Verdana, sans-serif]Ok,I go for 14.04 instead. [/FONT]




[FONT=Verdana, sans-serif]Ican't install ubuntu on my computer, so i cant run any sudo. When Itry to insall linux the installation stops after a while and doesntgå anywhere so i have to end the installation. After that my pc is jammedand i have to reinstall windows 10 again.[/FONT]




[FONT=Verdana, sans-serif]Ihave 4 gb of ram. I have 64 bit processor. I have an  asus x553malaptop. I have a intel celeron  2,16 ghz processor. [/FONT]


[FONT=Verdana, sans-serif]Howdo i install an uefi?[/FONT]


[FONT=Verdana, sans-serif]Bestregards[/FONT]

---

### Post by TheFu on 2015-11-13
> **john_mattson said:**
> Ican't install ubuntu on my computer, so i cant run any sudo.

No need to install.  Boot off any live-boot  media-CD,DVD,Flash-Drive  ... most have a "Try Ubuntu" option. 

Then you can do the requested steps.
> 
b) Please boot off a live-boot linux distro, open a terminal, and run sudo parted -l. Copy/paste the results back into this thread. The output created by the **boot-repair** tool would provide much more useful information. 

Getting the exact output from those commands provides the info we need in the format we expect. Plus it removes human error, almost always.

Oh... and please use code-tags in the posting so things line up.  The boor-repair output would provide much more useful data - it will put out a URL.

Or you can run my personal sys-info script [http://blog.jdpfu.com/sysinfo](http://blog.jdpfu.com/sysinfo) and post the URL it creates.  Any of those work.  The URLs are easier for you AND for us.

---

### Post by john_mattson on 2015-11-16
I have tried "try ubuntu" but the same thing happens. the computer freezez.

---

### Post by Bucky Ball on 2015-11-16
Boot from install media again, hit F6 at the 'Try Ubuntu' screen and choose the option 'nomodeset' from the pop-up list. Proceed. Any luck?

---

### Post by john_mattson on 2015-11-18
I tried F6 but nothing happened. no pop-up list appeared.

---

### Post by Bucky Ball on 2015-11-18
Sorry. It's earlier than that. See [HERE]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options"). :)

Then F6 and 'nomodeset'.

---

### Post by john_mattson on 2015-11-19
> **Bucky Ball said:**
> Sorry. It's earlier than that. See [HERE]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options"). :)

Then F6 and 'nomodeset'.


I'm using a usb to boot. I tried F6 and my windows  10 started. i tried  F2 and then i got into "aptio setup utility" with boot configuration. is that bios?   ialso tried to boot from windows 10. if i do that i got this "install ubuntu-sign" .

---

### Post by Bucky Ball on 2015-11-19
? Doesn't sound like you followed the instructions on the link I posted. Please read it carefully.

Boot from the Ubuntu install USB, at the screen with the logo at the bottom, hit any key, at the options there hit F6, choose nomodeset.

Please re-check that link and follow carefully. There are pictures to follow. :)

---

### Post by john_mattson on 2015-11-20
lets see if i got it right this time :)

i booted the usb and press f6 while it was booting. then i came to the grub ("try ubuntu..."). i tried to press f6 also here but nothing happened. the text on the grub stated:
try ubuntu without installing
install ubuntu
oem install (for manufatures only)
check disc for defects.

there wasn't any f1 to f6 options.  i run the disk for defects and the program stated there was 2 defects but it  didn's say what kind of defects. 

i pressed esc and come to 
grub>_

and there is stood: press e to edit the commands before booting or press c for a command line. 

it also stood:

minimal bash-like editing is supported, for the first word. tab lists possible command completions anywhere else tab lists possible device or file completions.

---

### Post by sudodus on 2015-11-20
You are running in UEFI mode, so the system boots from the USB install drive to grub (not syslinux, and the looks described by Bucky Ball). See these links with more details

Post #6: [Is the computer running in UEFI mode or in classical BIOS mode?](http://ubuntuforums.org/showthread.php?t=2230389&p=13370798#post13370798)
Post #7: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

