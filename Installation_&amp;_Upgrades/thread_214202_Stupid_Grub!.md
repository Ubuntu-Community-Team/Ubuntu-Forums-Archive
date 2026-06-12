---
title: "Stupid Grub!"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by Muppeteer on 2006-07-12
Whenever i try to install Fedora Core 5 or Ubuntu Dapper i can't get either to boot from Grub. I've tried everything i can think of. I have 3 HDD's and for some reason my no.3 drive which runs off a sata pci extension always shows as HDA or SDA. This doesn't seem to be a problem though as i've tried installing both distro's without that drive and get the same results.

Here's the order of my drives
HDA - WD 80GB
HDB - 10 GB Windows Partition/100GB NTFS
HDC - 100 GB NTFS/10 GB Linux Partition

In Fedora i have the option to change the boot order. I've tried multiple, by making my windows drive HDA and the Linux partition HDB. I've tried installing Grub to the MBR on HDA and HDB (Windows Drive) in all sorts of boot orders.

In Ubuntu, i can't change the boot order so i have to install Grub to HDB (Windows), but when i do this and restart it will come up saying "GRUB GRUB GRUB GRUB" forever. I've read this can be a problem with Sata drives or another drive is trying to boot.

Now, here's the weird thing. I can get Suse 10.0 and 10.1 to install no problem. When i go into Yast and check the bootloader it looks like this

[[IMG]http://img369.imageshack.us/img369/8630/yast20018dk.th.png[/IMG]](http://img369.imageshack.us/my.php?image=yast20018dk.png)
[[IMG]http://img400.imageshack.us/img400/7361/yast20022vg.th.png[/IMG]](http://img400.imageshack.us/my.php?image=yast20022vg.png)
[[IMG]http://img369.imageshack.us/img369/5982/yast20039dq.th.png[/IMG]](http://img369.imageshack.us/my.php?image=yast20039dq.png)

Anyway, it looks like Suse has put Grub on SDB, which is what i've tried with the other distro's. Any ideas where i'm going wrong?

Could i try and install Ubuntu on another partition and hope that Grub (Suse) picks it up?

---

### Post by parkash on 2006-07-12
Okay...  This seems a little unfriendly... :s

First. You should know which of your HDD is Master... That's, hardware master...  Or, which one is enabled in your BIOS to boot first.  Then, you should install grub into the mbr of that HDD... That's easy I suppose.

Now, I'll tell you a tip, with grub it is very easy to change the boot order. Open /boot/grub/menu.lst (after a successful installation that is) in an editor (as super user of course) --I prefer nano in a console or a terminal.

```

$sudo nano -w /boot/grub/menu.lst

```

And once there, go to nearly the end of the file. The order in which the "titles" are written is the boot order. If you want Windows to boot first then you should only put 

```

Title Windows XP
root (hd0,0)
chainloader +1
boot

```

Before the other OS's.

Note.- This is just an example, you should, in fact, copy the lines corresponding to Windows just as the installation program left them before.

Hope I helped you :cool:

---

### Post by Muppeteer on 2006-07-12
Hi, Thanks for the help...

My Windows drive is master (Hardware) then the drive which shows SDC is second and SDA is third, but for some reason shows as first even though it's 3rd in the bios. 

I checked the grub menu and this is what i got..
```
###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE Linux 10.1
    root (hd1,1)
    kernel /boot/vmlinuz root=/dev/sdc2 vga=0x317    resume=/dev/sdc5  splash=silent showopts
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE Linux 10.1
    root (hd1,1)
    kernel /boot/vmlinuz root=/dev/sdc2 vga=normal showopts ide=nodma apm=off acpi=off noresume edd=off 3
    initrd /boot/initrd

```

I'm not sure exactly what i'm supposed to do here because this is Grub working. My prob is that i can't get it working with anything other than suse, as it just goes straight into windows.

---

### Post by parkash on 2006-07-12
Ok...  Let me get it straight...   According to Grub, Windows is installed in hd0,0 -> That means the first partition of your master HD. That would be, normally hda1, but in your case I think that's sda1.
Then, Linux is installed in hd1,1 -> that means the second partiton of your second HD. Normally would be hdb2, but in your case I suppose it's sdb2.
I just need to know where your Grub is installed.

Your configuration is a little messy... How long have you been using Linux? 
Anyway, first we need to get your configuration straight. 

Normally, as far as I know, Linux interprets hda as Physically the Master HDD, then hdb the second, hdc the third (usually cd-rom) and so on...

You can see how Linux is naming your disks by running 
```
$sudo cat /proc/partitions 
```
in a terminal/console.  And comparing sizes.

---

### Post by Muppeteer on 2006-07-13
Well i got it working. The only way i could get linux to recognise that XP is hda was to unplug my 3rd HDD from the pci expansion. Ubuntu installed fine and grub works a treat. Now i'll have to figure out a way for it to recognise windows as hda with the other drive plugged in. I'm considering plugging my windows drive into the pci expansion. Right now it seems as thuogh it's the only fix as the boot order in my bios is correct.

Thanks for the help

---

