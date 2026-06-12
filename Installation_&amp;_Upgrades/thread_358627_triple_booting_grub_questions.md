---
title: "triple booting grub questions"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by dckirba on 2007-02-11
Hello all,

I have been reading up on multi-boot systems. However, I still have a lot of questions :)

To give you a little background... for some unknown reason I want to try Fedora Core 6. I currently have a dual boot XP and Dapper on two seperate hard drives. Fedora will go on a third drive.

Now, the Fedora forums say finish the install and install Fedora's grub to the MBR. But then they say that any kernel updates have to be manually entered into menu.lst for Ubuntu.

They also mention another method where every system has it's own grub and a master grub leads to the entire setup.

Now, I already have Ubuntu's grub on the MBR. Does this mean that if I install a master grub as above, I will have to reinstall an Ubuntu speicific grub for Ubuntu?

And then is it just a matter of copying the menu.lst entries for each seperate os into the master grub?

Also, how does the master grub work with XP?

Sorry for the bad terminology :D

[COLOR="DarkOrange"]Slightly off-topic:[/COLOR] Are there people here who use Fedora Core? What are your experiences? I was researching clusters and Fedora Core was consistently mentioned as a good system to work with so that's one of my main reasons for trying it out.

Thanks in advance,

Cheers,
David K

---

### Post by Herman on 2007-02-11
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
Please click on this link (above)

I haven't tried Fedora Core, but with most Linux Distros I have tried, you can either install Grub to the operating system's own first sector (partition), or you can you install its Grub to MBR without any problems.

You can also install Grub to the MBR of the second or third hard disk and so in, if you wish.
 
It doesn't really matter which Linux operating system has its Grub in MBR, the best way to boot  up all the other Linux installs is by making a 'configfile' boot entry in the menu.lst or grub.conf of whichever operating system has the grub installed in MBR.

A 'configfile' boot entry looks something like this,
```
title        Ubuntu Edgy Eft
configfile   (hd0,5)/boot/grub/menu.lst
```By booting with a configfile boot entry you will be having grub bring up the grub menu of whichever operating system you are trying to boot.  Therefore you will be always booting the most up to date kernel for each operating system, since each operating system will update its own menu.lst or grub.conf file.

Another idea is to install grub in its own separate /boot partition if you wish. That can be a good way to do things too, some people like to do things that way.

Regards, Herman :)

---

### Post by dckirba on 2007-02-11
Thanks Herman,

just one more question though...

Wehn I installed dapper, I chose to install grub to MBR

Now when I install FC, if I choose to install it's grub to MBR and then add a config entry as you said, will it find Dapper in Dappers /boot?

When I installed Dapper's Grub to MBR, did it also write a copy in Dappers /boot is what I'm trying to ask?

Sorry for being slightly on the ignorant side ;)

Cheers,
David K

---

### Post by Herman on 2007-02-11
> Now when I install FC, if I choose to install it's grub to MBR and then add a config entry as you said, will it find Dapper in Dappers /boot?Yes, if FC's grub is installed to MBR, when you type the commands in correctly in FC's grub's configuration file, that wil find whatever file you type in the command to ask FC's grub to look for.
In other word, if you make an entry like this in FC's menu.lst,
```
  title        Ubuntu Edgy Eft
configfile   (hd0,5)/boot/grub/menu.lst
``` It will find the menu.lst file in /boot/grub, in whatever operating system is in partition number 6.

You will probably need to alter these commands a little bit to make it fit your computer. If you have Edgy in partition number 1, on the first hard disk, you would replace the (hd0,5) part with (hd0,0).
If you have Ubuntu in partition number 2, you would replace the (hd0,5) with (hd0,1), and so on.

For example, here is my grub menu from the computer I am typing to you from right now, the two normal kernel booting entries at the top and the memtest entry are for my Edgy install, because that is the one who's grub is represented in MBR.
Below that, under the end of the automagic kernels list, are my old Dapper Drake and Breezy Badger operating system entries.
It is important to make sure other operating system entries are below the bottom of the automagic kernels list or they will be deleted when the kernel gets updated.
I have two kinds of boot entries there, I have one 'configfile' entry for each system, plus one 'symlink' boot entry for each system just to make sure. That's not really needed, but anyone can do that if they like.
The main thing is the 'configfile' boot entries. Those find the /boot/grub/menu.lst file in either my Dapper or my Breezy install and bring up the menu from whichever one of those I choose. Then I can boot from the next grub's menu.
```
## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-11-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu, Dapper Drake, (config boot on /dev/hda3) 
configfile      (hd0,2)/boot/grub/menu.lst


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu Dapper Drake, (symlink boot on /dev/hda3) 
root        (hd0,2)
kernel        /vmlinuz root=/dev/hda3 ro quiet splash 
initrd        /initrd.img
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Ubuntu, Breezy Badger, (config boot on /dev/hda2) 
configfile      (hd0,1)/boot/grub/menu.lst


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Breezy Badger, (symlink boot on /dev/hda2) 
root        (hd0,1)
kernel        /vmlinuz root=/dev/hda2 ro quiet splash 
initrd        /initrd.img
boot


```

---

### Post by Herman on 2007-02-11
>  When I installed Dapper's Grub to MBR, did it also write a copy in Dappers /boot is what I'm trying to ask? When we say we are installing a boot loader in MBR, we don't really mean what we are saying exactly. It is just an abbreviation or a quick way to say something.

Grub is really in the Ubuntu partition, inside our /boot/grub directory. If you open yours you will see files called,
herman@rocky:~$ ls /boot/grub
> default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2 All those files aare part of grub, especially the one called stage2.

The part of grub that is in the MBR is just a very tiney, small bit of code to make the MBR point here. It is more like just a roadsign.
It is totally misleading to say we are installing a bootloader in the MBR, because the MBR is very small. A bootloader would never fit inside the MBR at all. It would be like trying to fit an elephant inside a volkswagon.

So the 'configfile' boot entry finds the menu.lst file here in the /boot/grub directory in whichever partition you tell it to look. 

Just try it, you will see how it works pretty quickly then. 
You can also make configfile boot entries in the other operating systems too, that point back to the first one of you want.
Another interesting experiment is to make more menu.lst type files but give them a slighly different filename, you can also configfile those ones too, it is possible to make a splashimage slideshow that way.

Regards, Herman :)

---

### Post by reiki on 2007-02-11
HERMAN!
:)

You da man.... I just read through this. VERY cool about configfile. I have 3 drives and 4 operating systems installed. Each one has it's own grub menu.lst. When something major happens I have been editing (manually) the menu.lst file that is actually booting the system.

This configfile thing is very cool. I'm going to try it and see what I can break! :)

---

### Post by dckirba on 2007-02-13
Hi Herman,

Thanks a lot, that cleared up many doubts in my mind. Now I'll just have to wait till payday to get another Hard drive and try out my triple-boot!

BTW, are those partitioning howtos yours? Great work,

cheers,
David K

---

### Post by Herman on 2007-02-13
Hello reiki, *Okay!* Well done, and thank you for the feedback too. :)

Hello dckirba, 
You are welcome and thank you for asking good questions, we probably helped a few other people who also wanted to know the same things.
Yes, the website in my signature links under my posts is mine, it just began as a way to help people use the 'Alternate' install CDs, but it has grown into more a boot loader website now, especially grub bootloader. There is still a lot more I have to learn about Grub myself, but I want to pass on what I have learned already so other people will like grub too. Grub is a wonderful boot loader but not enough people know how to use grub well. Actually, grub is very easy to understand and use with the right instructions, and also can be a lot of fun. I am glad you are having fun with grub.
Regards, Herman :)

---

