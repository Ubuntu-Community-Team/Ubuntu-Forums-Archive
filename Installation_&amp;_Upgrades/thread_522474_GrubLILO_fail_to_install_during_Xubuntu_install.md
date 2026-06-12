---
title: "Grub/LILO fail to install during Xubuntu install"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by 0graham0 on 2007-08-10
Hi, I am attempting to install Xubuntu 7.04 on a Dell Latitude LM (40 MB Ram, 6 GB hard drive). I have an external floppy drive hooked up to the serial port, and it has an internal cd drive. I was successful in running the alternative install CD by booting from a windows 98 floppy, and theh using linld.com to boot to the CD from DOS. ( As detailed in [http://ubuntuforums.org/showthread.php?t=244918&highlight=linld](http://ubuntuforums.org/showthread.php?t=244918&highlight=linld) )```
linld image=d:\install\vmlinuz initrd=d:\install\initrd.gz "cl=root=/dev/ram boot=install ramdisk_size=1048576 devfs=mount,dall"
```

The install cd booted up, and I partitioned 5 GB to an Ext2 / partition , and 1 GB as a swap partition. (I've also tried partitioning with a 4.9 GB Ext3 / partition, a 100 MB Ext2 /boot partition and a 1 GB swap partition.)

The install runs fine until the Grub installer pops up with the error "Grub failed to install to /target/" and I also got the same message when LILO fails to install. 

Any help would be greatly appreciated, thanks

NEW: ALSO - If I finish the installation without installing a bootloader, When I reboot back into the alt. install CD, the partition i set up on my hard drive as root is now identified as /media/sda1 ...?

---

### Post by scorp3000 on 2007-08-10
Better try Damn Small Linux or Zenwalk.

---

### Post by 0graham0 on 2007-08-10
You mean, Boot into DamnSmallLinux and install Grub that way?

---

### Post by merlinus on 2007-08-10
From xubuntu --

**Minimum system requirements**

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

So xubuntu will not run on your computer.

Damnsmalllinux or zenwalk might.

-merlin

---

### Post by 0graham0 on 2007-08-10
So will Grub not run on the machine because of the specs? I don't mind if it runs insanely slow, I just want to test it out...

---

### Post by merlinus on 2007-08-10
Looks like xubuntu needs 64MB RAM to load the needed modules in order to run at all.

Maybe investigate getting another stick of memory.

-merlin

---

### Post by 0graham0 on 2007-08-10
So is it for sure that it will not run at all with 40 MB RAM, or will it run off of swap, albeit very slowly? Either way, is there any indication that Grub did not install due to the lack of creating a /boot directory prior to install?

thanks for the replys

---

### Post by merlinus on 2007-08-10
Grub does not need a /boot partition.  It can be installed in the mbr or in /.  The alternate install cd gives a choice via an Advanced option at that point.

If you can get to a terminal, you can reinstall grub.  If so, post back for directions.

-merlin

---

### Post by 0graham0 on 2007-08-10
So I attempted a reinstall, again with just a 5.0 gb partition for / and a 1.0 gb partition for swap. The install went along fine until the "Install the GRUB boot loader on a hard disk" section. The error I recieved is > "The grub package failed to install into /target/..." It gives me the option of Continuing Anyway. When I choose Yes the installer then prompts: > "It seems that this new installation is the only operating system on the computer. If so, it should be safe to install the GRUB boot loader to the master boot record of your first hard drive...Install the GRUB boat loader to the master boot record?"When I select Yes I am then given the error > "Unable to install GRUB in (hd0)
Exectuing 'grub-install (hd0) failed.

This is a fatal error.

Could this have to do with the fact that I booted from linld from a floppy? Thanks for the help so far...sorry Merlinus...I wouldn't know how to get to a terminal from here, or after a restart (Or maybe, all I have to do is select "Execute a Shell" from the installer main menu?)? Before re-installing I tried loading the installer in Rescue mode, but i didn't know where to go from there.

---

### Post by merlinus on 2007-08-10
What do you mean by, "I booted from linld from a floppy?"

Were you installing from the alternate text-based or live cd?

If you boot from the cd, you should have a "restore" option that will get you to a command line.

Also, the execute a shell option may work.

-merlin

---

### Post by 0graham0 on 2007-08-10
The bios on this computer cannot boot directly from a cd. I had to boot from a win98 floppy with linld.com added onto the floppy. I then was able to load the alternate cd from there. I will try the restore option, what should i do if i get a command line?

---

### Post by 0graham0 on 2007-08-10
Thanks for the help, i gotta actually go to bed, i'll update in the morning...

---

### Post by merlinus on 2007-08-10
```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute results from find for (hdx,x).  It will probably be (hd0,0).

-merlin

---

### Post by 0graham0 on 2007-08-11
So i finished the install without installing a bootloader and rebooted. I noticed something strange, when the partition manager opens, after rebooting, the partition I set as root, is now labeled as /media/sda1 

Could that have anything to do with the problem?

---

### Post by merlinus on 2007-08-11
Perhaps. What do you see under Places/Computer?

And what does this terminal command give"

```

mount

```

-merlin

---

### Post by 0graham0 on 2007-08-11
sudo grub cannot be entered in the installation shell. Where would I look for Places/Computer? When I enter mount I recieve the messages```
none on /proc type proc (rw)
tmpfs on /dev type tmpfs (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /.dev type tmpfs (rw)
/dev/scd0 on /cdrom type iso9660 (ro)
/dev/sda3 on /target type ext 3 (rw,data=ordered)
/dev/sda1 on /target/boot type ext2 (rw)
```

---

### Post by 0graham0 on 2007-08-11
Well...I tried another install today, and specified a 1 gb swap partition, a 100 mb /boot partition, and a 4.9 GB / partition. Same problem with Grub not being able to install to /target/. When I reboot back onto the alt. install disk, the partition manager now reads the partitions I had specified as /boot and / as /media/sda1 and /media/sda3. This makes me wonder if this is all happening because I have to boot the alt. install cd from the dos linld, on a win98 floppy disk?

---

### Post by merlinus on 2007-08-11
At this point, I do not know if the problems lie in having to boot from a floppy to install.

If you can see your data and system files at the /media mountpoints, then something is happening!

What are you using as a file manager?  Do you see the menubar?

-merlin

---

### Post by 0graham0 on 2007-08-11
Sorry if I was unclear... I'm seeing the /media partitions through the Alternative Install CD's partition manager and shell. And I typed "mount" in the shell provided by the install CD to get that info you asked for. If I boot with no floppy or cd, I get Unsupported Operating System, or No Operating System or something like that...

---

### Post by merlinus on 2007-08-11
What if you select "boot from hard drive" using the alternate install cd?

Or is that even an option?

Have you tried SuperGrub?

-merlin

---

### Post by 0graham0 on 2007-08-11
boot from hard drive is not an option on the alternate install cd. I opened a shell right after install using the cd and looked at the /target directory. A vmlinuz file and initrd file WERE there, however when I try to boot with supergrub it can't find my vmlinuz file.

---

### Post by merlinus on 2007-08-11
At this point, I do not know what to say.  Ubuntu stores its system files in the / partition, and creates a /home/username directory plus a /swap partition.

It seems that nothing like this has happened despite all your attempts at installing.

You might try zenwalk or damnsmalllinux, if you are wanting to run a linux distro on your machine.

-merlin

---

### Post by 0graham0 on 2007-08-11
Oops! I was able to boot! Using super grub disk, I pushed C to enter the command line...```
grub>  root (hd0,1)
grub> kernel /vmlinuz root=/dev/sda3
grub> initrd /initrd.img
grub> boot
```

The boot process begins! hurray.

thanks for all the help, sorry for my incompetence ; )

---

### Post by 0graham0 on 2007-08-11
Or maybe I celebrated too soon? The boot process began loaded a whole bunch of things, and then stalled for 2 minutes before displaying the message:> Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/moudles ls /dev
ALERT! does not exist. Dropping to a shell!
It then drops me into a busybook shell with the prompt (initramfs) Also...should I open a new thread for this?

---

### Post by 0graham0 on 2007-08-11
Okay, so I tried booting again with super grub disk, this time specifying the kernel root as /dev/sda1 . The boot process went farther than the last two times , and failed when it got to the mounting process. This time the message I got was:> Begin: Running /scripts/local-premount ...
kinit: name_to_dev_t(/dev/sda1) = sda1(8,1)
kinit: trying to resume from /dev/sda1
[   787.890144] Attempting manual resume
kinit: No resume image, doing normal boot...
Done.
mount: Mounting /dev/sda1 on /root failed: No such device
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

---

### Post by 0graham0 on 2007-08-11
3rd times the charm?

Booted again from supergrubdisk, this time specifying the kernel root as /dev/sda2...It seems to be booting into Ubuntu fine! Sorry again for the incompentence and thanks for all the help

---

### Post by 0graham0 on 2007-08-11
One last thing...The boot process runs fine and I end up logging in to a ubuntu command prompt. Any ideas on how to start the xfce gui?

---

### Post by merlinus on 2007-08-11
> 
 Any ideas on how to start the xfce gui?


```

startx

```

-merlin

---

### Post by 0graham0 on 2007-08-11
?

> The program startx is currently not installed. 
startx:command not found

---

### Post by merlinus on 2007-08-11
Try this:

```

/usr/bin/startx /usr/bin/xfce4-session

```

-merlin

---

### Post by 0graham0 on 2007-08-11
Still recieving "No such file or directory / command not found" I navigate to /usr/bin and nothings there? There was no errors during the installation, is it possible that its justnot there?

---

### Post by 0graham0 on 2007-08-11
Be afraid. Be very afraid.

So there I am in the ubuntu command line. Knowing next to nothing about linux I decide to try and install grub from the cd. I mount the cdrom, navigate to the /media/cdrom/pool/main/g/grub directory. I then run dpkg -i grub(restoffilename).deb

I restart and no operating system is detected. I run super grub disk and when I enter: root (hd0,0) (which worked before) i am told Error 21: Selected disk does not exist...

Did I just ruin my entire disk?

---

### Post by merlinus on 2007-08-11
> **0graham0 said:**
> Still recieving "No such file or directory / command not found" I navigate to /usr/bin and nothings there? There was no errors during the installation, is it possible that its justnot there?

If there is no /usr/bin, then the installation did not work.  It contains all sorts of executables and other files needed to run xfce.

-merlin

---

### Post by 0graham0 on 2007-08-11
There is a /usr/bin just no Xfce files. Do I need a internet connection when I install to get Xfce installed as well?

---

### Post by merlinus on 2007-08-11
So what is in /usr/bin, for example (not the whole list of files)?

-merlin

---

### Post by 0graham0 on 2007-08-11
I will let you know as soon as possible, however I fear I made my hard drive unbootable by unpacking the wrong grub package (i unpacked the file in the cdrom/install/pool/main/g/grub directory instead of the cdrom/install/pool/main/g/grub-install directory!). It shouldn't be too hard to install X off of the install cd once I get the ubuntu command line running, right?

---

### Post by 0graham0 on 2007-08-11
I had to install X from the cd after the install:
```
sudo apt-cdrom add
```
insert cdrom and press enter
```
sudo apt-get install xubuntu-desktop
```

(thanks to help at [http://ubuntuforums.org/showthread.php?t=523343](http://ubuntuforums.org/showthread.php?t=523343))

---

### Post by 0graham0 on 2007-08-12
Well all of that got GDM and X up and running, and was able to install grub from the cd using```
sudo apt-cdrom add
sudo apt-get install grub
sudo grub-install sda
``` 

however as I was warned  the system runs hideously slow. I assume that if I had just done the base X install without GDM things might run a bit quicker, but oh well...

Thanks again for all the help

---

