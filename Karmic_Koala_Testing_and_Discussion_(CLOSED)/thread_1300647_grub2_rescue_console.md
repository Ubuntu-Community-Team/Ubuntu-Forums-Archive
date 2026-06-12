---
title: "grub2 rescue console"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-10-25
need a little help with grub2 rescue console - i kind of messed up my main install and grub2 drops straight to rescue. I have another grub2 setup on another partition and need to know how to point the rescue console to it - only internet i have is on my phone so searching google is a pain also on access to another sc

---

### Post by mick222 on 2009-10-25
[http://planetstephanie.net/2009/05/27/grub2-rescue-mode/](http://planetstephanie.net/2009/05/27/grub2-rescue-mode/)
 Hope this is of some help .Can't you boot with the live cd and maybe sort it from there.

---

### Post by celticbhoy on 2009-10-25
aspire one so no disk, and dont have a distro on usb

---

### Post by mick222 on 2009-10-25
Copied article if it makes it easier to read for you 0,2 by the way

> Grub2 Rescue Mode / Console

As a change of pace, this missive is actually meant to be useful and informative. If you don’t know anything about grub or grub2 and aren’t interested in learning about bootloaders, then this article is not for you. On the other hand, if you suffer insomnia, then you may wish to keep a copy of this nearby.

Grub2 is the next generation of the Grub bootloader. Grub stands for GRand Unified Bootloader, and offers advantages over LILO and others in that it offers a ‘command line’ mode, enabling one to possibly recover from a non-booting system. Like anything though, there is a learning curve and Grub has it’s own set of commands and quirks. For several years, this article at Linux Journal has been my Grub bible, as it were.

The original Grub (aka legacy grub) is a few years old, and appearantly there were some shortcommings with it, so Grub2 is now out there. It’s available in Debian and Ubuntu repositories, among others. When you install it, legacy Grub is automatically removed. There are warnings that Grub2 is not yet ‘finished’ and all that jazz, but in my case I was having trouble with Grub so I did switch to Grub2, and that seemed to solve my problems. However, it introduced some new ones. Grub2 has a different command set, and more or less works rather differently than legacy Grub. And being so new, there is a lack of good documentation for it. I’m not attempting to write the documentation, only to explain what I was able to figure out myself, in order to rescue a non-booting system.

When you see this upon booting your system, you know you are having some Grub2 problems.

Welcome to GRUB!
error: no such disk
Entering rescue mode...
grub rescue>

In my case, I had copied the root partition from one drive to another, then installed grub2 on the second drive, then physically moved that second drive to a new system. The problem was that the device.map that was installed with Grub2 was from the original system, and was not valid on the new system. This leaves Grub2 in a just-barely-working state.

Here is one of the main differences between Grub2 and legacy Grub. With legacy grub, at this point there would be an error that it couldn’t find/load it’s Stage2 components and you’d be stuck. With Grub2 it installs just enough into the MBR of the drive that even without finding the rest of itself, there is enough here to work with. Grub2 uses modules (similar to linux kernel modules) instead of one monolithic Stage2. In the rescue mode, there are a minimal set of modules and a minimal set of commands. Not enough to boot the system directly, but enough to (hopefuly) find the rest of the Grub2 modules then boot the system.

In my case, the available commands (you can list them by typing help) are boot, cat, dump, exit, help, insmod, ls, lsmod, rmmod, root, set, unset. Boot and exit aren’t much help at this point, if it could have booted you wouldn’t be sitting at the rescue console, and exit just drops you to whatever your BIOS’s next boot device is. Linux users will recognize the commands cat, insmod, ls, lsmod and rmmod. These do work as you would expect them to. And in this case, the first thing to do is type ls by itself – this will list the root devices (i.e. disks) that Grub2 can see – in my case, the list is:

(hd0) (hd0,1) (hd1) (hd1,1)

This list is showing that there are two physical hard drives (hd0 and hd1) and each hard drive has a single partition on it (hd0,1 and hd1,1). Where legacy Grub counted partitions from #0, Grub2 counts partitions from #1. Another important thing to note is that the order in which Grub2 names the drives does not necessarily correspond with the drive device assignments in Linux. So the first linux drive /dev/sda is not necessarily (hd0). You can figure out which drive is which though, by ‘mounting’ them and checking. The Grub2 root command ‘mounts’ the volume. Note that you want to mount the partition, not the drive. So if I issue the command root (hd0,1) to mount the partition on the first drive, Grub2 responds with:

(hd0,1): Filsystem is ext2

This is good news; the volume is there, it is the right filesystem (in my case I have formatted the volume as ext2; you might have ext3 or ext4 etc.) Still, the other volume (in my case) was also formatted ext2, so I do need to ensure this is the drive I want. To do that, I’m going to use the ls command again, but this time I’m going to give it some parameters – namely, I want to list the files in the /boot/grub folder. If you give ls a directory that doesn’t exist you will get an error message (file not found). In this case, the command ls /boot/grub does return with the correct output. (I won’t type it all out here, suffice to say there’s a few dozen files.) If you further want to verify, you can use the cat command. In this case I can cat /boot/grub/grub.cfg to display the contents of the grub configuration file, and verify fully that I’ve got the right volume.

At this point, we have the correct volume ‘mounted’ so we now need to load the kernel and (optionally) an initram image. Except, our grub2 console doesn’t have the commands to do that… so what do we do? We need to load the correct Grub2 module. Here’s where documentation would help, if there is any, if I could find any. Of all the dozens of modules in /boot/grub, the only one you need is _linux.mod – and you activate it with the insmod command:
insmod /boot/grub/_linux.mod

If it works, there will be no feedback, just a new grub rescue> prompt. If it doesn’t work, you’ll get an error message. Now if you use the help command again, you will see there are two more commands available: initrd and linux (in legacy Grub, the kernel was loaded with the kernel command; in Grub2 the command is now linux).

At this point we can go ahead and load the kernel – if you require any kernel options, be sure to include them on the command line. In my case the full command is:
linux /boot/my_fmlinuz vga=785 ROOT=/dev/sda1 quiet
The only part of that which is required is the linux kernel itself, the /boot/my_fmlinuz part. Yours will be different of course. The rest of that command is unique to my setup and you may have different requirements. If successful, Grub2 will respond with some feedback. For me, it returned:

[Linux-bzImage, setup=0x2e00, size=0x1e5c30]

Your results will probably not be identical, but as long as you don’t get an error, you have the kernel loaded. Next, if you use an initrd image, load that with the initrd command. In my case: initrd /boot/my_ramfs.img. Again your command will differ, you need to use the correct initrd file name for your system. If the initrd command works, there is no feedback. Otherwise there is an error.

Incidentally, you can list the various files in your boot directory with the command ls /boot. Generally speaking, initrd files will usually have a .img suffix, and the kernel may contain the word linuz (not linux). On Ubuntu installations for example, they make it even easier – the kernel is symlinked to /vmlinuz and the initrd file is symlinked to /initrd.img so you don’t even have to go into the boot directory. You could just use the commands linux /vmlinuz and initrd /initrd.img to load them.

Now, we have the kernel loaded, and we have the initrd loaded, finally we can just issue the boot command, and it should work!

Assuming everything does work correctly and you get into linux, it would be a good idea to repair whatever went wrong with Grub2 in the first place. You can do this by verifying that the device.map is correct then issuing the grub-install command. For more information on this, read the manual: man grub-install

I hope this document has been of some use to someone — I sure could have used it yesterday! :)

Cheers!

---

### Post by celticbhoy on 2009-10-25
thanx - some of the commands dont work but did manage to get to a busybox prompt so a bit more messing about !

---

### Post by mick222 on 2009-10-25
ok hope you get it going

---

### Post by DougieFresh4U on 2009-10-25
I also having a grub issue [my drama]("http://ubuntuforums.org/showthread.php?t=1299653"). 
Just wanted to say that my grub-rescue> messege is a little bit different than the standard:

```
Welcome to GRUB!
error: no such disk
Entering rescue mode...
grub rescue>
```

as mine reads:

```
GRUB Loading.
error - invalid arch independent ELF magic
grub rescue>
```

---

### Post by celticbhoy on 2009-10-25
managed to get into my windows partition using the old install usb I had setup, so I am just going to download ubuntu and create a live usb to see if I can sort it from that. Busybox was no good to me as I dont know enough about it.

---

### Post by mick222 on 2009-10-25
Theirs a post somewhere about chrooting into Karmic from a live cd might help . I ended up reinstalling last time I messed up grub quicker and esier as i have a separate home partition. Grub 2 really need something like super grub.

---

### Post by celticbhoy on 2009-10-25
> **mick222 said:**
> Theirs a post somewhere about chrooting into Karmic from a live cd might help . I ended up reinstalling last time I messed up grub quicker and esier as i have a separate home partition. Grub 2 really need something like super grub.

Thing is I dont think I have messed up Grub, I think I haved corrupted the partition that the grub config files live on. So I am hoping a simple fsck will fix it.

---

