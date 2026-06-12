---
title: "Win 7 &amp; Ubuntu 9.10 on separate drives, is this possible?"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by traderjb on 2010-02-09
Greetings everyone, I hope you're all well!  I am needing a little advice here with a situation my computer will be facing.  Currently, my machine (has AMD Athalon 6000 X2 64-bit) has Windows 7 installed on a hard disk.  Now I would like to install Ubuntu 9.10 (64-bit) on a separate hard disk, not a partition. Am I better off to unplug the "Windows disk" and plug in the blank and install Ubuntu and then plug in the Win disk? In the past, I've encountered a problem with grub, so I'm a tad fearful here sorry. Will plugging both in after installing Ubuntu 9.10 (as the second hard disk, windows will still be HD0) affect the Win 7 disk?  

Thank you so much for any assistance.

---

### Post by darkod on 2010-02-09
It's your choice whether to unplug, personally I like all hardware present when installing an OS. Just because of the fact that you can't be sure which will be HD0 and which HD1 after replugging.

There is no need to worry about grub. The main thing that you should ALWAYS do with multiple drives, is confirming where grub will be installed. Usually you would leave the windows bootloader on your windows disk, and put grub on the ubuntu disk.

If you decide to leave the windows disk connected, when you start the ubuntu installer in step 4 make a note how is the ubuntu disk called (most probably it will be /dev/sdb, and the windows disk /dev/sda). In the last screen, before clicking Install, click on Advanced and it will tell you where it plans to install grub2. Just select /dev/sdb, if that was the name of the ubuntu disk, and that's it.

Obviously, if you have the windows disk as first hdd option in BIOS, you will boot straight into windows. To see grub2 you will have to set the ubuntu disk as first option.

---

### Post by jpaulb on 2010-02-09
Is there a way to choose from a menu which OS is to be booted?

---

### Post by darkod on 2010-02-09
> **jpaulb said:**
> Is there a way to choose from a menu which OS is to be booted?

The grub menu at boot should list all OSs you have installed, so, yes.

---

### Post by jpaulb on 2010-02-09
> **darkod said:**
> The grub menu at boot should list all OSs you have installed, so, yes.

Does that mean that grub would have to be on the MBR of the first drive?
I wish to do a simular setup shortly, I don't have a clue how.

---

### Post by darkod on 2010-02-09
> **jpaulb said:**
> Does that mean that grub would have to be on the MBR of the first drive?
I wish to do a simular setup shortly, I don't have a clue how.

If you mean the first drive in boot order, yes. But not necessarily the first hdd.

Basically, usually people decide to keep the windows disk with windows bootloader, and ubuntu disk with grub. In BIOS you can usually easily set which hdd you want to boot from first. So just set the drive where you told grub to install as first, and off you go. :)

PS. Note that if you disconnected the windows disk during ubuntu installation, grub will not know about it at first, because it wasn't there to be detected. In this case just let ubuntu boot and in terminal do:
sudo update-grub

It should sort it out automatically.

---

### Post by raymondh on 2010-02-09
> **jpaulb said:**
> Does that mean that grub would have to be on the MBR of the first drive?
I wish to do a simular setup shortly, I don't have a clue how.

what Darko may mean is that

-  install GRUB in the HD where you have installed Ubuntu.  Grub will install in the MBR of _THAT_ hd.
-  Set the Ubuntu HD as first to boot in BIOS
-  Leave the windows hd as is (as well as its' MBR which contains the windows bootloader).

Above means that the original poster has a 2 HD set-up.

Raymond

EDIT: I type slow

---

### Post by sameden on 2010-02-09
hi 
this is not what you wonted to do but this is what i would do.

what i would do is put both hard drives in the computer, then partition one of the HDs (the larger) for the two OS and then use the 2nd HD for the documents.

i set up my computers like this because i find it better having one hard drive with all the documents so it easy getting all the documents on both the OS instead of scouting around the other hard drive for the document folder when im in the other OS.

hope i help 
i know it was not what you wonted to do but i thought you may like another way of doing it

sam

---

### Post by jpaulb on 2010-02-09
Thanks everyone.
Sorry for hijacking the thread; but now things are clearer.

---

### Post by traderjb on 2010-02-09
Wow, thank you for the response.  So far so good except for one hiccup. Grub shows "windows 7 (loader)" when the machine first boots up, but when you click on it it says it's a no go. When I did sudo update-grub I got the following:

john@JBuntu64:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

done
john@JBuntu64:~$ 


Once more, thank you for the help so far, and any assistance on this one issue would be supremely appreciated! :)

---

### Post by darkod on 2010-02-10
> **traderjb said:**
> Wow, thank you for the response.  So far so good except for one hiccup. Grub shows "windows 7 (loader)" when the machine first boots up, but when you click on it it says it's a no go. When I did sudo update-grub I got the following:

john@JBuntu64:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

done
john@JBuntu64:~$ 


Once more, thank you for the help so far, and any assistance on this one issue would be supremely appreciated! :)

If a drive was unplugged it might not have a reference for it in  device.map file. One of the reasons I don't encourage unplugging unless  you really have a problem.
A new device map, if I'm not mistaken, is generated with:

sudo grub-mkdevicemap

Try the sudo update-grub after.

---

