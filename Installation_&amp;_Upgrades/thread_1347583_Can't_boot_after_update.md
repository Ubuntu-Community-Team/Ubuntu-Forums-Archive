---
title: "Can't boot after update"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Trifud on 2009-12-06
Just updated my Ubuntu Netbook Remix and I didn't pay much attention but I think that there was a new Linux kernel in the update list as well. After installation of the new packets the system required a restart. I restarted and ended up in the GRUB console:
 
sh:grub

I wrote boot and linux but it complained that there should be a kernel version. I tried with boot 2.26.32 but it complained that no such file existed.

How do i bring Ubuntu back online?

---

### Post by Herman on 2009-12-06
Something like as follows,
```
set root=(hd0,1)
```Where: Your Ubuntu partition is in the first hard disk, (disk zero), and in the first partition, (partition 1). You may use tab completion to assist you in discovering what disks and partitions GRUB 2 can detect.
```
linux /vmlinuz root=/dev/sda1
```Where  /vmlinuz is your symlink to your Linux kernel, all Ubuntu installations have one and most other Linux distros do too.
Where /dev/sda1 is a file system which contains /sbin/init, (your 'root' file system).
```
initrd /initrd.img
```Where  /initrd.img is your symlink to your initrd.img file, which assists the kernel to boot.
```
boot
```The command to boot, should be followed by a lot of text scrolling up your screen and hopefully result in a successful boot at the other end of it. :D

---

### Post by Herman on 2009-12-06
Just a couple of extra notes for the less experienced, 

'**tab completion**' means you just type the first two or three numbers or letters of most of the commands you're typing into the terminal, and then press your 'tab' key and GRUB will try to guess what it is you were trying to type and automatically complete it for you or if it's not sure, GRUB will offer you a list of suggestions.
Needless to say, this is an extremely useful feature in the GRUB console, because you can use it to get GRUB to 'take a look around' inside your computer for you and tell you what it can 'see'.

'**symlinks**' are like shortcuts in Linux, and you'll always find a built-in shortcut to the latest Linux kernel and initrd.img file there somewhere. That saves you the extra work of having to type in the exact file path and file name for the particular kernel and initrd.img files you want. If by some calamity they don't exist or you can't find the symlinks,  you can use 'tab completiion' to find the exact file path and file names for your kernel and initrd.img files.

---

### Post by Trifud on 2009-12-06
I have four partitions on the HDD: Recovery (primary), Windows OS (primary), Data (logical) and Ubuntu (logical). So I started:

```
set root=(hd0,4)
```That was OK. After that I tried with

```
linux /vmlinuz root=/dev/sda1
```but I got an error the kind of "no such something". I booted SLAX from a USB memory stick and expected the partition where Ubuntu is. It was sda6. Then I went back to GRUB and tried with sda6 and actually everything from 1 to 6 but still the same result :(

---

### Post by tuxeee on 2009-12-06
> **Trifud said:**
> 
```
set root=(hd0,4)
```That was OK. After that I tried with

```
linux /vmlinuz root=/dev/sda1
```



if hd0,4 is correct then you have to change the next code to:

```
linux /vmlinuz root=/dev/**sda4**
```

if you dont know if hd0,4 is correct then type:

"root (hd0,4)"
"find / <tab>" Note: after the forward slash press tab dont type it like that and it will give you a list of what is in the directory.

hd0,4 on my pc is to boot from USB

good luck :D

---

### Post by Trifud on 2009-12-06
Hm, I played a little bit with it:

```
set root=(hd0,1)
find / <tab>
```

gives me the content of the Recovery partition which is set as primary.

```
set root=(hd0,2)
find / <tab>
```

gives me the content of the Windows OS partition which is also set as primary.

```
set root=(hd0,3)
 find / <tab>
```

gives me nothing but the following line:

```
sh:grub find /
```

```
set root=(hd0,4)
  find / <tab>
```

gives me an error message. I tried with the above three variants to get to sda1 and sda2 but I couldn't. It seems that I can't reach to the logical partitions (on one of which is Ubuntu). Maybe somehow I have to change the Ubuntu partition from logical to primary?

---

### Post by Herman on 2009-12-06
> gives me an error message. I tried with the above three variants to get to sda1 and sda2 but I couldn't. It seems that I can't reach to the logical partitions (on one of which is Ubuntu). Maybe somehow I have to change the Ubuntu partition from logical to primary?No, Ubuntu can boot in a logical partition just as well as it can in a primary, and GRUB should be able to read the file system as well, providing the file system is readable.
Maybe you need to run a file system check?

Try this link, [Running a filesystem check on an ext3  filesystem]("http://members.iinet.net.au/%7Eherman546/p10.html#filesystem_check_on_an_ext3_filesystem") - from the command line in a live CD, USB or another hard disk installed Linux.

Or, this one, [Running a filesystem check with GParted]("http://members.iinet.net.au/%7Eherman546/p10.html#Running_a_filesystem_check_with_GParted_")** **- a user friendly GUI method

---

### Post by Herman on 2009-12-06
Try the uuid command in CLI mode GRUB for a list of your file sysems and their UUID numbers and check whether or not your Ubuntu file system appears in the list,
```
GRUB > uuid
```
 Another way to approach things would be to use the 'find' command,
```
grub > find /vmlinuz
```
```
grub > find /sbin/init
```

For more information about how to use GRUB (Legacy) in CLI mode, try the following link, [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli"). - GRUB can function as a miniature operating system.

---

### Post by tuxeee on 2009-12-07
> **Trifud said:**
> Maybe somehow I have to change the Ubuntu partition from logical to primary?

if you can boot ubuntu off a CD or a USB, you know the test mode then you can go to the partition manager and it will list all the directories for you.

You can also try (hd1,1) for example.

depends on how many HDs you have, list them here that might give us some more info on helping you out.

---

### Post by Trifud on 2009-12-08
> **tuxeee said:**
> if you can boot ubuntu off a CD or a USB, you know the test mode then you can go to the partition manager and it will list all the directories for you.

You can also try (hd1,1) for example.

depends on how many HDs you have, list them here that might give us some more info on helping you out.

My computer doesn't have an optical drive :)

I have just one HDD with two primary and two secondary partitions. They seem to be healthy since I can access both of them from WIndows and Slax.

---

### Post by darkod on 2009-12-08
Just to clarify, you didn't install trough wubi did you?

---

### Post by Trifud on 2009-12-08
> **darkod said:**
> Just to clarify, you didn't install trough wubi did you?

Yes, I did. Is that the source of all problems that I have? NTFS?

---

### Post by darkod on 2009-12-08
OK, I don't want to be rude but if you knew it was wubi why did you select [ubuntu netbook remix] for the thread type instead of [wubi]? You're completely misleading people trying to help you.

I don't know why this happens when you do updates in wubi (personally I never use it) but the procedure how to make it go away (this time) is in post #10 here:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Depending on which of your partitions you installed wubi, you might need to change /dev/sda1 in /dev/sda2, /dev/sda3, etc. First, second etc partition on the first drive.
Also the instructions are the same for all windows versions but in XP there is typing error in the third command, 26.31 should be 2.6.31.

That should get you going. And I would seriously consider using proper dual boot instead of wubi. Hope you get it to work.

---

### Post by Trifud on 2009-12-08
Aham, I didn't know wubi was running upon Windows. I thought wubi was just a way to install Ubuntu from Windows and after the restart it was pure Ubuntu. OK, now I want a real Ubuntu and there is just one way to get it: get rid of the wubi and install Ubuntu from USB flash (I have a 4GB one and I boot Slax from it). So there is just one question: how to get rid of the Ubuntu boot option when I start the computer? Even when I format the Ubuntu partition I still can choose Ubuntu Netbook Remix from the Windows boot manager.

---

### Post by darkod on 2009-12-08
Wubi is removed in add/remove program in control panel in windows. Just like any windows app. You do not just delete the folder.
That should also remove the entry in the windows bootloader.
In case it doesn't there are some manual steps to do here:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by Trifud on 2009-12-08
Just one last question: where do I find Ubuntu Netbook Remix 9.10 in IMG format. There is only an iso image of the installation.

---

### Post by darkod on 2009-12-08
You can use the ISO too, no need to be IMG. Depending how and where you're creating the usb stick. I find it easiest on ubuntu desktop if you have, just use in System-Administration program called USB Startup Disc creator.
If you have only access to windows you can use the free software unetbootin. If you use this and need advice how to disable the unetbootin menu and make the standard ubuntu menu show up, let me know.

---

### Post by Trifud on 2009-12-08
That was easy. I have a running version of UNR on my USB flash memory. Now how do I install UNR to the HDD alongside Windows? I didn't find any such information on the web. I already have an ext3 (logical) partition on the HDD.

---

### Post by darkod on 2009-12-08
> **Trifud said:**
> That was easy. I have a running version of UNR on my USB flash memory. Now how do I install UNR to the HDD alongside Windows? I didn't find any such information on the web. I already have an ext3 (logical) partition on the HDD.

If you already have a partition you want to use, the only option is selecting Manual partitioning in step 4 and do it yourself. But remember that you also need swap partition so only one won't do it.
The options are: Booting again from the usb stick and selecting Try Ubuntu, opening Gparted (in System - Administration) and deleting that ext3 partition. Then booting with the usb stick, selecting Install Ubuntu and telling it to use the Largest Available Free Space (it was called something like that). That option will create extended partition in the unallocated space and create / and swap partition inside it.
Or just booting with the stick, Install Ubuntu and at step 4 select Manual partitioning, delete the partition, and after that you can create / and swap as logical partitions. This way you can create separate /home if you want to. The automatic way doesn't create separate /home.

---

### Post by Trifud on 2009-12-08
I couldn't install it on the HDD because whenever I tried to install it on the partition I had made in advance the installer complained that it couldn't unmount /cdrom. When I let it install automatically it did it on the USB memory instead on the HDD. Maybe that's better. At least the risk to destroy my Windows installation will be reduced.

Thanks for the help!

---

