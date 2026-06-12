---
title: "Can't install Ubuntu 12.04 from USB"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by Allenph on 2012-08-23
I have been working on my "new" machine for a couple days now, at first I was going to install Chromium but when that didn't work I figured i'd settle for the latest Ubuntu distro. I have a Sandisk Cruzer 8 GB which I tried to install Ubuntu on. The goal was to boot from this and install to a fresh partition I just made. But I got a little taste of Murphey's law and when I booted up on my Dell Dimension 4600c (Yes I know its old.) I get "Operating system not found." I installed using UNetbootin and I can see the files on the drive from Windows 8 so I know it worked. I tried again anyways. Same results. I know the drive is okay because I just installed Windows 8 with it. What gives?!

---

### Post by 2F4U on 2012-08-23
Just because you see the files on the usb does not mean that it worked. Sounds as if the bootloader was not installed correctly by unetbootin. I had serveral of these problems with unetbootin in the past. Are you sure that the downloaded is is ok, did you verify the checksum of the iso? If you have the chance, create a liveCD and see if that boots.

---

### Post by Allenph on 2012-08-23
Alright well, what other software can I use? Should I re-download the image? I don;t have any blank CDs.

---

### Post by darkod on 2012-08-23
Depending on the windows version you are doing this from, you might need to start unetbootin with right-click, Run As Administrator, instead of the double click.

Sometimes it needs higher permissions in windows to write to boot sectors.

While it's preparing the stick watch closely whether it says the bootloader is installed correctly towards the end.

PS. As for other software, you can use Universal USB Installer for example, to prepare the stick. I would run it as administrator too, otherwise in Vista and 7 writing to boot sectors might be blocked sometimes.

---

### Post by Allenph on 2012-08-23
Windows 8. It asks even if I only double click it. Honestly the 3rd step moves by so fast I can't even see what it says. Although it does say (Done) Right next to it.

---

### Post by darkod on 2012-08-23
> **Allenph said:**
> Windows 8. It asks even if I only double click it. Honestly the 3rd step moves by so fast I can't even see what it says. Although it does say (Done) Right next to it.

Not sure how it works on 8. Try Universal USB Installer, maybe it will work better.

---

### Post by Allenph on 2012-08-23
Tried again. Still no cigar. Could it have something to do with my computer not wanting to boot from a USB with multiple partitions? I mean its an old computer.

---

### Post by darkod on 2012-08-23
Not really sure. In theory, the computer only needs to fire off the bootloader and then the bootloader needs to boot the partition it's configured to boot. But that's in theory.

How are you using usb stick with multiple partition in windows anyway? Or win8 accepts this? That option is not available on win7, it sees only the first partition. Or this is a usb hdd?

Another idea, try making the partition FAT32 not NTFS. I usually have installation sticks with FAT32.

---

### Post by Allenph on 2012-08-23
Tried the new software. Still have the same issue.

---

### Post by Allenph on 2012-08-23
I have already tried both formats. I always thought that linux used multiple partitions. Just thought it might be the reason why.

---

### Post by darkod on 2012-08-23
> **Allenph said:**
> I have already tried both formats. I always thought that linux used multiple partitions. Just thought it might be the reason why.

Linux does see multiple partitions on usb sticks. But you are preparing the stick in windows, right? In win7 the driver that loads for sticks sees only the first partition on it, regardless how many exist. So you can only specify this partition as the destination. Not sure if that has changed in win8.

But anyway, since after using unetbootin or usb installer the stick will have grub bootloader, loading the install process from any partition should be fine. As long as win8 allows you this partition as destination when using unetbootin or usb installer.

Sounds like you are doing it right, not sure what's bothering it.

The long way around you could try, is extracting the ISO to a partition on the stick, and then install the grub4dos bootloader on it and create entry in the boot menu.
[http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/)

---

### Post by Allenph on 2012-08-23
Alright I formatted the drive as Fat32, I extracted the contents of the image onto it, how do I use wingrub now?

---

### Post by darkod on 2012-08-23
I don't remember the exact file name, but there was a file like grub_gui.exe or grub_inst_gui.exe.

That will install grub1 on the MBR of the stick. Just make sure you select the correct letter. That is very important.

After making the boot sector, you only need to copy the grldr file onto the stick/partition, and the menu.lst. In menu.lst make an entry for your ubuntu which should be like:

```
title Try Ubuntu
root=(hd0,0)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd /casper/initrd.lz
boot
```You might need to make modifications in the root=(hd0,0) line, the hd0 is the first disk which should be the stick when booting from it, and the other 0 means the first partition on the stick. The counting starts from 0. So, if the partition is not the first, modify the line. I think I got the spelling right. :)

That should load the live mode and you can click the Install icon on the desktop to start the installation.

---

### Post by Allenph on 2012-08-23
All I see is something called grub.exe and it opens this...

[IMG]http://i1074.photobucket.com/albums/w408/TheScripter1/Screenshot_WinGrub.png[/IMG]

Never done this before. Sorry. Haha

---

### Post by darkod on 2012-08-23
Is G: the stick? If it is, it looks like it's installed. Browse and check if /boot/grub/menu.lst exists on the stick.

If it does, open it with notepad or wordpad, and add the title item I posted earlier.

Then try booting with the stick and selecting that ubuntu entry in the menu that shows up.

I'm not sure if you need the = in root=(hd0,0) so try with that and if it doesn't work change it to root(hd0,0).

---

### Post by Allenph on 2012-08-23
Only loopback.cfg in boot/grub. No menu.lst. Should I create one? What do I put in it?

---

### Post by Allenph on 2012-08-23
However there is a MENU.LST inside G:/GRUB

---

### Post by darkod on 2012-08-24
> **Allenph said:**
> However there is a MENU.LST inside G:/GRUB

OK, add the above mentioned entry in there. If you don't see the entry when you boot, that's not the correct menu.lst.

If you do see the entry but it doesn't boot ubuntu live mode, that's the correct file but the entry has some error in the syntax.

---

### Post by Allenph on 2012-08-24
SO if I said (hd1,0) it is skipping all my partitions on the first disk and going to the USB right? Because disk one has 5 partitions on it. 


The Original file said...

```

timeout 10

title Windows at (hd0,0)
root (hd0,0)
chainloader +1

```

I changed it to...

```

timeout 10

title Try Ubuntu
root=(hd1,0)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd /casper/initrd.lz
boot

```

Nothing different happened. Still "No operating system found"

---

### Post by darkod on 2012-08-24
The thing is that when booting from usb bios sometimes can consider the usb stick to be the first disk, so it can be hd0. Try that too. It depends from computer to computer whether a usb will be read before the hdd or after when booting from it.

Also, the = symbol is not needed, I wasn't sure about that earlier. I know saw on another place that for grub1 it's like root(hd0,0) without the =.

---

### Post by Allenph on 2012-08-24
GRRR!!! Still nothing. It should not be this complicated. :'(

---

### Post by darkod on 2012-08-25
What do you mean still nothing more precisely, do you get the grub boot menu at least or not?

If you are not getting it, you are not booting from the stick or grub is not installed on it.

If you are getting the grub menu but it doesn't boot ubuntu, then there is an error in the syntax of the entry.

Please specify.

It's actually not very complicated and is easily done on a linux machine but obviously you don't have one to work with it. On windows it can be sometimes little bit more complicated since windows wants only the windows way.

I'll try to find and attach the exact files I used since the GUI didn't look like the screen you posted. Maybe that will help.

---

### Post by darkod on 2012-08-25
OK, try these files.

First, format the stick as a single FAT32 partition.

Download the attached grubinst.zip and extract it, there will be a folder grubinst. In that folder, start the grubinst_gui.exe but use right-click Run As Administrator on win7, not double click.

At the top in the Device section select Disk and the usb in the drop down box. According to the size of the disks in the list you can easily find the usb stick. IMPORTANT: Make sure you select the stick because if you select your hdd it will install the grub bootloader over your windows bootloader!!!
Click the Install button on the bottom. As far as I remember (because I haven't used this a while, you don't need to select anything else in the options, just the disk where you want grub to be installed.

Once that is done, from the grubinst folder copy the grldr and menu.lst files to the stick.

After that extract the ubuntu ISO to the stick. Extract it, don't just copy the ISO file.

That's it. Try to boot with the stick and you should see a menu with Try Ubuntu, Command line and Reboot options. Selecting Try Ubuntu should start loading the live desktop. Once it loads and you can confirm it works on your hardware, you can install with the Install icon on the live desktop.

I adjusted the menu.lst for you, and used root(hd0,0). In case your computer doesn't consider the stick as hd0 it might not work but in any case you should see the boot menu at least. We will adjust the menu.lst later if needed, that depends on the computer.

---

### Post by Allenph on 2012-08-25
Well the command prompt when I press install on the program says "grubinst: Unknown image type
Press <ENTER> to continue..."

Is that would should be happening?

---

### Post by darkod on 2012-08-25
> **Allenph said:**
> Well the command prompt when I press install on the program says "grubinst: Unknown image type
Press <ENTER> to continue..."

Is that would should be happening?

I don't think so.

So, you are staring the grubinst_gui.exe with Run As Administrator right? And the window opens, you select the Disk option and the stick. You press Install and you get that error?

---

### Post by Allenph on 2012-08-25
Yep. I have already tried to use this utility before and got the same error. I tried anyway still the same error. No operating system found. TO answer your previous question no I haven;t even been able to get into grub. The USB does boot up at all.

---

### Post by r0n d0n on 2012-08-25
I had this very same problem. The Sandisk flash drive I was using had something called a launch pad installed on it. You have to get this tool ---> [http://drivers1.sandisk.com/DriverDownload/assets/USB%20Flash%20Drives/launchpadremoval.zip](http://drivers1.sandisk.com/DriverDownload/assets/USB%20Flash%20Drives/launchpadremoval.zip) in order to remove it, then format and write the image and you should be good to go. 

I hope this helps you out.

---

### Post by Allenph on 2012-08-25
> **r0n d0n said:**
> I had this very same problem. The Sandisk flash drive I was using had something called a launch pad installed on it. You have to get this tool ---> [http://drivers1.sandisk.com/DriverDownload/assets/USB%20Flash%20Drives/launchpadremoval.zip](http://drivers1.sandisk.com/DriverDownload/assets/USB%20Flash%20Drives/launchpadremoval.zip) in order to remove it, then format and write the image and you should be good to go. 

I hope this helps you out.

Thanks but...This program isn't doing anything. All it says is "Please insert a U3 Smart drive." Are you sure this isn't a virus? :-o

---

