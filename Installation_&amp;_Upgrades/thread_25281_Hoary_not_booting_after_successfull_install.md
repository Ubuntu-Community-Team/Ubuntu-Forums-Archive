---
title: "Hoary not booting after successfull install"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by shu on 2005-04-09
Hi!

I have really weird problem. I've downloaded hoary dvd iso. I booted it in 'livecd' mode to check if everything works ok, and it did. The whole system was properly recognized, with network printer and so on. 

Then I did the installation. It was successfull. No problems at all, until I had to reboot computer. After reboot I'm greeted with grub menu and when I choose to boot ubuntu it doesn't boot. 

Following lines appear on screen and that's all:
root (hd1,1)
kernel /boot/vmlinuz-2.6.10-5-k7 root=/dev/hde2 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-k7
savedefault
boot

I have AthlonXP processor and KT400 based motherboard. Ubuntu is installed on my second disk which is attached to Promise PDC20276 on board controller.

Notice 1:
Ubuntu is second linux on my box, I have also Slackware 10.1 installed on hda2. I can boot into ubuntu using slackware kernel just fine, except for all those warning about ubuntu unable to find modules and so on..

Notice 2:
I tried switching to 386 kernel, since livecd uses it, but it didn't solve the problem. It looks like kernel is not loading at all. 


Any advices?

---

### Post by lao_V on 2005-04-09
[QUOTE=shu]Hi!


kernel /boot/vmlinuz-2.6.10-5-k7 root=/dev/**hde2** ro quiet splash
[/QUOTE]

should this be hda2?

---

### Post by shu on 2005-04-09
No. Everything is fine. My root partition is root(hd1,1) in other words /dev/hde2.  Grub finds the kernel and reports that it found Linux-Bzimage and so on, but doesn't load it. I have no idea why...

---

### Post by kleeman on 2005-04-09
From your slackware boot check your logs from hde2 i.e. the partition with ubuntu on. You should be able to mount this from slack. Check /XXX/var/log/messages and /XXX/var/log/dmesg (/XXX being the Ubuntu mount point) to see if you can see why the ubuntu boot freezes.

---

### Post by shu on 2005-04-09
Well, after browsing through these forums and reading some other guys problems I decided to be more patient. And it actually boots fine, but it take 2 MINUTES!!! form the moment I press enter in grub till it starts uncompressing kernel. That means it takes 2 MINUTES to long. Any idea why this might be happening?

---

### Post by kleeman on 2005-04-09
In your grub menu line 
kernel /boot/vmlinuz-2.6.10-5-k7 root=/dev/hde2 ro quiet splash
remove the quiet and watch the boot up for clues.

---

### Post by shu on 2005-04-10
I booted it without 'quiet' flag but it didn't show any valuable info. In other word it's booting just fine, only it takes 2 minutes from pressing enter in grub to start of kernel. Start of kernel, not ubuntu booting sequence.

---

### Post by kleeman on 2005-04-10
Anything interesting in /var/log/messages  ??

---

### Post by shu on 2005-04-10
Nothing at all. There are no problems with booting. It's just this 2 minute delay before kernel gets uncompressed.

What is the difference between kernel on livecd and kernel used after installation? Is there anything I can pass as argument that would help in this situation?

---

### Post by kleeman on 2005-04-10
Got me there. Mine is rather slow as well. Perhaps you should lodge a bug on this and see what the devs say....

---

### Post by maqi on 2005-04-10
[QUOTE=shu]No. Everything is fine. My root partition is root(hd1,1) in other words /dev/hde2.  Grub finds the kernel and reports that it found Linux-Bzimage and so on, but doesn't load it. I have no idea why...[/QUOTE]

I would have thought that (hd1,1) would be /dev/hd**b**2 in the GRUB numbering format??!!?? And by the same format /dev/hde would be (hd4,0)?

cheers,
maqi

---

### Post by shu on 2005-04-10
No. Grub's hd1 is the second harddrive as reported by bios. My second drive is connected to additional ata controller (promise pdc20276), which in linux naming scheme is called hde. Anyway it has nothing to do with the problem. Kernel is found, initrd is found, ubuntu boots, but it takes AGES to load kernel. 

How do I report a bug in ubuntu?

---

### Post by kleeman on 2005-04-10
Go here and register before lodging the bug

[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

---

### Post by maqi on 2005-04-10
[QUOTE=shu]No. Grub's hd1 is the second harddrive as reported by bios. My second drive is connected to additional ata controller (promise pdc20276), which in linux naming scheme is called hde. Anyway it has nothing to do with the problem. Kernel is found, initrd is found, ubuntu boots, but it takes AGES to load kernel. 

How do I report a bug in ubuntu?[/QUOTE]

To report a bug go [here](http://bugzilla.ubuntu.com/).

But before you do ... 

Please search these forums and google for information regarding your ata controller. Is this a RAID set up? If so, it may just be a configuration problem :)

maqi

P.S. Support for your controller is included in the kernel. The name of the module is "pdc202xx_new". so it may just be a matter of making sure the module loads early by adding it to /etc/modules. I'm not sure exactly where in the list you should place it. Some research for you ;)

---

### Post by shu on 2005-04-11
I sent a bug report. In the mean time I found that system boots just fine with lilo.

---

### Post by steven_ellis on 2005-06-23
If you have a look at thread [http://ubuntuforums.org/showthread.php?p=226304](http://ubuntuforums.org/showthread.php?p=226304)  I have similar problems with my machine.

I have two drives on my VIA onboard ide channel (hda, hdb) and 3 drives on my motherboard PDC20276 controler (hde, hdg, hdh)

My core Linux root/boot/home paritions are RAID 1 on hda/hdb and Use the drives on the PDC controler for video editing.

On boot I have exactly the same boot delay issues as shu. If I disable the onboard extra IDE/RAID controler the boot is pretty much instant.

One thing to note is i'm only running the PDC20276 controller in IDE mode, i'm not using any of the Promise raid features.

So how can I convince GRUB to boot quickly as I don't want to switch to Lilo. I have a feeling that a custom kernel with the PDC driver compiled in will probably fix most of the problems.

Steve

---

### Post by steven_ellis on 2005-06-23
Looks like there are a couple of relevant bugzilla entries, but one that really sticks out is

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8899](https://bugzilla.ubuntu.com/show_bug.cgi?id=8899) 


Similar setup and same motherboard

---

### Post by afonic on 2005-06-23
Try turning off acpi or some other boot settings. It was so slow in one of my PCs that the installation from the CD needed 3mins to start and the system over 5mins.

I got it working with the
linux acpi=off noapic nolapic
option. Edit your grub load commands and try these.

---

### Post by steven_ellis on 2005-06-25
[QUOTE=afonic]Try turning off acpi or some other boot settings. It was so slow in one of my PCs that the installation from the CD needed 3mins to start and the system over 5mins.

I got it working with the
linux acpi=off noapic nolapic
option. Edit your grub load commands and try these.[/QUOTE]

Makes no difference. Still the same boot time and lack of feedback.

Steve

---

### Post by GML3G0 on 2005-06-26
Same problem. Occassionally it boots fine, other times it doesn't. I just reboot because I can't stand waiting that long. I have an Abit AV8 VIA K8T800 Pro motherboard with an Athlon 64 (939) 3200+. Raptor as my only HD on an SATA connection.

---

### Post by GML3G0 on 2005-06-27
bump

---

### Post by steven_ellis on 2005-06-27
[QUOTE=steven_ellis]Looks like there are a couple of relevant bugzilla entries, but one that really sticks out is

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8899](https://bugzilla.ubuntu.com/show_bug.cgi?id=8899) 


Similar setup and same motherboard[/QUOTE]

Well i've just tried a custom kernel build disabling CONFIG_FB_MODE_HELPERS=y, and I still have the same boot time problems.

Just running a new kernel compile that builds in the Promise pdc202xx_new and Via via82cxxx drivers in directly, rather than using modules. I'll see how well that goes tonight.

Just updating the bugzilla entry

Steve

---

### Post by GML3G0 on 2005-06-27
Hmmm, the problem stopped lately. Booted a couple of times today no problem. Don't want to jynx it though. :)

---

### Post by steven_ellis on 2005-06-28
Have you done a recent kernel install, or tweaked anything in the bios?

I tried my custom kernel with the VIA and Promise drivers built in, but I still get the same problems. Just updated to the newest 2.6.10 kernel security fix release and again no difference.

Steve

---

### Post by GML3G0 on 2005-06-29
nope. Just Synaptic upgraded my Linux Image, but I doubt it was that.

---

### Post by steven_ellis on 2005-06-29
Ok so which kernel package are you currently booting and what is the associated grub setting?

Steve

---

### Post by GML3G0 on 2005-06-29
Ubuntu, kernel 2.6.10-5-386

kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386

---

### Post by shu on 2005-06-29
**Possible solution!** 

The problem is caused - on my setup - by "BIOS Enhanced Disk Drive calls determine boot disk" option under "Processor type and features\Firmware Drivers" being enabled in default kernel. Disabling it makes system booting normally.

This feature experimental, unimplemented in most chipsets and known to make some systems fail to boot.  8-[

---

