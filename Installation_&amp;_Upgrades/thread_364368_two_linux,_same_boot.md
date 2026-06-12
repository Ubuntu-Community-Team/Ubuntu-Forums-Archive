---
title: "two linux, same /boot"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by jmvidalvia on 2007-02-18
I installed two linux: edgy+ubuntu and edgy + xubuntu (I know it is the same system, only desktop changes, but wanted to use them separately)
I use only one partition for boot, for both systems.
Yesterday, I upgraded ubuntu.
Today, I tried to start xubuntu, but this problem appeared: [http://www.ubuntuforums.org/showthread.php?t=364324](http://www.ubuntuforums.org/showthread.php?t=364324)
Now I realize perhaps it is not a good idea to share the same boot partition and same grub.
Now, in xubuntu, I have two retained programs:
linux-headers-generic linux-image-generic

¿what should I do now?

Please find below an extract of my grub.

#this starts xubuntu, but usb and network don't work
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,6)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda9 ro quiet splash locale=es_ES
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

#this starts xubuntu, everything works
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,6)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda9 ro quiet splash locale=es_ES
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot


#this starts ubuntu,everything works
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,6)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash locale=es_ES
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

---

### Post by jmvidalvia on 2007-02-18
I think I am starting to understand.
I installed last linux-headers-generic and linux-image-generic
Now Xubuntu works with the latest kernel version.
Probably when I upgrade Ubuntu, the grup was modified automaticaly to start with the new version, but as my ubuntu boot was aded by hand to grub, only xubuntu start-up was modified, although last kernel was not available yet in my xubuntu partition, as it was not installed.
What a mess!
Last time I share same /boot partition...
Thanks!

---

### Post by Herman on 2007-02-18
Hello jmvidalvia,
What to you want to do now, fix your two operating systems or re-install again new? I can help you try to fix them, it shouldn't be too complicated, but it depends on how much time and patience you have. You sound like you know a lot already, so you should be able to, especially with help.
It depends how much work you have put into installing extra software and getting updates and getting all your settings how you like them. If those are brand new installs and not too much has been done yet it will be quicker to just delete then and install again. What will you decide?

Lots of people like to try our Ubuntu, Kubuntu and Xubuntu, I multiple boot  older versions of Ubuntu with newer versions too. There is nothing wrong with that, multiple booting is fun. :)

Yes, you had a good idea to make a seperate /boot partition but there is a better way to do that.
It is much better to install each operating system in one piece, independant of other systems. 
The a best way is  to make a small partition, format it ext2 or ext3, and leave it empty.
Install one operating system and ignore the small boot partition, just install the operating system all in its own partition and install grub to (hd0).
Then install another operating system and do the same thing again. (All in one partition, and install grub to (hd0), overwriting the MBR again.
It is okay for both operating systems to share the same swap area.
[Mount the separate small partition]("http://users.bigpond.net.au/hermanzone/p10.htm"), which will be your grub partition, and copy your /boot directory to it. (From the last operating system you installed). You still keep the /boot partition in the operating system there to use by the operating system, just make a copy of it, don't delete it, you will still need it.
[Get a grub shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") ('sudo grub'), and root grub to the small new grub partition. setup grub to (hd0) from there. Quit the grub shell. 
Open the menu.lst and delete the OS entries. [Replace them with configfile boot entries]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems"). Save and close. Now you will have a seperate Grub partition and it will call up the menu.lst of each opertating system you select. It will let each system take care of its own kernels and update its own menu.lst. I can tell you in more details if you need, just ask.

I even have a seperate grub partition with [Super Grub]("http://supergrub.forjamari.linex.org/") in it, here's how I did that,                                 [How to Install Super Grub USB Disk in a Hard Disk Partition]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk_in_a_Hard_Disk")
That's probably no good for general everyday use though, so I don't expect too many other people to want that. It's just to show you what is possible.

Enjoy Ubuntu and have fun, install as many Ubuntu versions and flavors as you like,
Regards, Herman :)

---

### Post by jmvidalvia on 2007-02-18
Thank you very much for your help!
Let me explain what I have, as I am not sure to modify everything as you mention...
Lets say (*):
Partition1> Kubuntu (/ +/home +/boot)
Partition2> Ubuntu (/ + /home)
Partition3> Xubuntu (/)
Partition4> /home for Xubuntu
Partition5> /boot for Ubuntu and Xubuntu
(I avoid to mention swap, XP, etc)

Now everything works, although I have to edit my grub every time I upgrade the kernel versions.
Can say my grub is hand-made!
Would you really re-install it?
Many thanks for your help!

(*) I know this is a strange configuration, but I've been learning step by step, and this is one of the consecuences.
:-)

---

### Post by Herman on 2007-02-19
>  Now everything works, although I have to edit my grub every time I upgrade the kernel versions.
Can say my grub is hand-made!
Would you really re-install it? Hello jmvidalvia,
No, don't re-install it if you have it working okay. I was thinking you were not happy with it the way it was. If you like it the way it is then just keep it that way. It will be fine.  There are lots of ways to set things up that will work okay. 
Regards, Herman :)

---

### Post by adrian15 on 2007-02-19
> **Herman said:**
>  I even have a seperate grub partition with [Super Grub]("http://supergrub.forjamari.linex.org/") in it, here's how I did that,                                 [How to Install Super Grub USB Disk in a Hard Disk Partition]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk")
That's probably no good for general everyday use though, so I don't expect too many other people to want that. It's just to show you what is possible.


I suppose you're talking about a normal hard disk not an usb one.
I suppose you do not use the usbshift command don't you?

adrian15

---

### Post by jmvidalvia on 2007-02-19
Yes.
It's my normal hard disk.
I don't use usbshift command
Thank you!

---

### Post by adrian15 on 2007-02-19
> **Herman said:**
> Now you will have a seperate Grub partition and it will call up the menu.lst of each opertating system you select. It will let each system take care of its own kernels and update its own menu.lst.

Humm... If the partitions where distros are installed are ext3 I recommend to use root (hd0,X) and setup (hd0,X) to install their own grub in the same partition boot sector.

Then from the common /boot you can put entries like:

title fedora menu
rootnoverify (hd0,1)
chainloader +1
boot

title xubuntu menu
rootnoverify (hd0,3)
chainloader +1
boot


The configfile /boot/grub/menu.lst idea is great I prefer this one because you can use silly boot loaders that know how to boot from a given partition but do not understand the menu.lst files.

adrian15

---

### Post by adrian15 on 2007-02-19
> **jmvidalvia said:**
> Yes.
It's my normal hard disk.
I don't use usbshift command
Thank you!

:) I was quoting Herman not you. :)

adrian15

---

### Post by jmvidalvia on 2007-02-19
:) 
Thanks anyway...

---

### Post by Herman on 2007-02-19
@ adrian15, I'm sorry but something was wrong with the link I had there originally, '[How to Install Super Grub USB Disk in a Hard Disk Partition]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk_in_a_Hard_Disk")' bit it's fixed now. About USB shift all I can say is 'Boot Linux' works from sgd_usb_0.9577 installed in a partition.

@ jmvidalvia, I need a little more time to think if you are waiting for me.  So you want to fix it so you don't have to manually update your kernel entry for Ubuntu, but Xubuntu now owns the menu.lst file, is that correct? Because Xubuntu was installed after Ubuntu, so it has probably overwritten everything in the shared /boot partition.
I am thinking of copying the menu.lst file and renaming it some other name and making it belong to Ubuntu. Then both operating systems can have their own menu with their own automagic kernels list. Then we use a configfile command to switch from Kubuntu's menu.lst to Ubuntu's menu. But I don't want to do anything yet, I would rather think about that for a while first in case I think of a problem with that idea. I don't want to cause you any more problems than you have already. Maybe I will make up some experiments first and test if that idea is a good one or not. But that is what I am thinking will be the simplest solution. 

Regards, Herman :)

---

### Post by jmvidalvia on 2007-02-19
@Herman
Thank you very much for your ideas.
Actually,  as my system is now running I don't need any urgent solution.
I think it would be nice to have something like an "independent grub", but don't take this as a priority.
Many thanks again for your work!

---

### Post by soul_rebel on 2007-02-19
Best thing to do is making one of the installation use grub on its own partition instead of the hard drive first sector. Than you can simply chainload the second grub. It's like booting windows...

---

### Post by Herman on 2007-02-19
I don't think my first idea will work, I tried an experiment copying a menu,lst file and renaming it menu.lstb, and made a configfile entry in menu.lst to bring up the menu from menu.lstb. My menu.lstb has boot entries changed so that it would boot Ubuntu (hypothetically). It also an entry that configfiles back to the the Xubuntu menu.lst. That part works well, so far so good.
However, I don't think that when Ubuntu gets a kernel update and runs update-grub, that it will look for a file called menu.lstb. I would need to learn more to manage to be able to accomplish that. 
> Best thing to do is making one of the installation use grub on its own partition instead of the hard drive first sector. Than you can simply chainload the second grub. It's like booting windows... Yes, I think it would be only as little bit more work, but a more well known solution to edit your /etc/fstab in Ubuntu and make the /boot partition not mounted by Ubuntu as a /boot partition anymore. Mount it as a data partition instead and copy the /boot directory into Ubuntu and set it up as Ubuntu's own boot directory, in /. Then install Grub to the first sector of the partition and chainload it as adrian15 and soul_rebel are suggesting, I think they are correct.
I'm glad you aren't in a hurry.  I want to try some experiments pretty soon after I install a setup something similar to yours. I should be able to give you better help then, but it will take me a little time. You don't need to wait though, unless you want to. But I think your question is an interesting one and I want to see if I find out what is the very best way to solve it. I am curious. 
Regards, Herman

---

### Post by Herman on 2007-02-23
> I don't think my first idea will work, I tried an experiment copying a menu,lst file and renaming it menu.lstb, and made a configfile entry in menu.lst to bring up the menu from menu.lstb. My menu.lstb has boot entries changed so that it would boot Ubuntu (hypothetically). It also an entry that configfiles back to the the Xubuntu menu.lst. That part works well, so far so good.
However, I don't think that when Ubuntu gets a kernel update and runs update-grub, that it will look for a file called menu.lstb. I would need to learn more to manage to be able to accomplish that. Hello jmvidalvia,
I am back to let you now that I have tested my first idea and found that it seems to be working very nicely for me so far. :)

I already had an established Ubuntu Edgy installation in the test computer, and I then installed Kubuntu Dapper with a separate /boot partition. Then I installed Xubuntu EdgyEft to a new partition with Xubuntu's boot to the same /boot partition as Kubuntu's without formatting it. As I expected, any files with the same filenames were overwritten.

To try out my first idea, I did as explained already and copied my menu.lst file and renamed the new copy menu.lstb. 

The one called menu.lst will belong to Kubuntu in my case, so I have changed the three entries in the automagic kernels list to boot Kubuntu. I edited menu.lst with an entry to boot Ubuntu as well, which for me is my stand-alone system, in a single partition. I used a [configfile boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile"), but you could use a [chainloader boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader") just as well if you prefer. 
I also added a configfile entry titled Xubuntu to point to menu.lstb, which will be Xubuntu's grub menu. This means I can skip from Kubuntu's grub menu to Xubuntu's grub menu and back to Ubuntu's grub menu when I am booting, (if I can't decide which system to boot or something). :) (He-he).

I edited menu.lstb, which belongs to Xubuntu with entries to boot Kubuntu and Ubuntu by making configfile entries referring to their menu.lst files. 


Now to make update-grub look for menu.lstb and automatically update it when a new kernel is installed there is a file in /sbin called update-grub.
```
sudo mousepad /sbin/update-grub
```You should use 'sudo gedit', not 'mousepad', if you are using Ubuntu when you do this, or 'sudo kwrite' or 'sudo Kate' in KDE (Kubuntu).
[CENTER]/SNIP/
[/CENTER]
```

    removabledevice="$(echo "$1" | sed -e 's%\([sh]d[a-z]\)[0-9]*$%\1%' -e 's%\(fd[0-9]*\)$%\1%' -e 's%/part[0-9]*$%/disc%' -e 's%\(c[0-7]d[0-9]*\).*$%\1%' -e 's%^/dev/%%g')"
        if [ -e "/sys/block/$removabledevice/removable" ]; then
                if [ "$(cat /sys/block/$removabledevice/removable)" != "0" ]; then
                        echo "/dev/$removabledevice"
                        return
                fi
        fi
    echo ""
}

## Configuration Options
# directory's to look for the grub installation and the menu file
grub_dirs="/boot/grub /boot/boot/grub"

# The grub installation directory
grub_dir=$(find_grub_dir)

# Full path to the menu.lst
**[COLOR=Red] menu_file=$grub_dir/menu.lstb[/COLOR]**

# the device for the / filesystem
root_device=$(find_root_device)
root_device_2_6=$(convert_kernel26 "$root_device")

# the device for the /boot filesystem
boot_device=$(find_device "/boot")

# Full path to the device.map
device_map=$grub_dir/device.map

# Default kernel options, overidden by the kopt statement in the menufile.
kopt="root=$(awk '$2 == "/" {print $1}' /etc/fstab) ro"

# Title
**[COLOR=Red] title="Xubuntu"[/COLOR]**

# should update-grub remember the default entry
updatedefaultentry="false"

```[LEFT][CENTER]/SNIP/
[/CENTER]

[/LEFT]
 In /sbin/update-grub, if we scroll down to about 1/4 of the way down from the top, there are a couple of lines that looks like this,
```
# Full path to the menu.lst
menu_file=$grub_dir/menu.lst
```I changed that to,
```
# Full path to the menu.lst
menu_file=$grub_dir/menu.lstb
```I also changed something a few lines further down, I changed where it says,
```
# Title
title="Ubuntu"
```and I made it,
```
# Title
title="Xubuntu"
```The later change is not so important, but it makes the menu have the correct title when update-grub is run instead of having them all called Ubuntu. We can have Kubuntu called Kubuntu and Xubuntu called Xubuntu in our grub menus automatically now that we know how.

It is important also to edit our kopt lines in our menu.lstb with the correct partition UUID numbers. These need to be changed to match the UUID numbers in our /etc/fstab files for the / (root) partition.
More info on editing our kopt line in /boot/grub/menu.st is here, [kopt= (kernel options)]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt")
More information about filesystem UUID numbers is here,[                     About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

After it was all set up and all three systems were booting the way I wanted, I updated my Kubuntu OS, but it did not recieve a kernel update. I am fairly certain it will work okay when it does, because Kubuntu owns menu.lst, and I'm not expecting any problems updating that one.
Then I updated Xubuntu, which owns menu.lstb, and everything went smoothly. I was not aware of receiving any kernel update, but when I rebooted and checked menu.lstb, it had kernel entries that weren't there before. I'm not certain, but I suspect that they are just the kernel for Kubuntu Dapper, I imagine that one must have been detected and added automatically somehow.
To test things a little bit further, I ran sudo update-grub in my Xubuntu install ```
sudo update-grub
``` Feedback from sudo update-grub is here,
```
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lstb
Searching for splash image ... found: (hd0,5)/Kubuntusplash.xpm.gz

Found kernel: /vmlinuz-2.6.17-10-generic
Found kernel: /vmlinuz-2.6.15-18-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lstb ... done
``` I forgot to mention that I also added my own splashimages for each operating system to the appropriate grub menus. You can download your Ubuntu, Kubuntu and Xubuntu splashimage here if you are interested, [Add a splashimage to the GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")

Finally, I must tell you that this is still experimental,  so you should be wary and use your own good judgement about whether you want to try the same thing yourself. I would not want to cause anyone to have any problems because they try this and it turns out to be a bad idea for them. It seems to be working well for me so far and I am very optimistic about it. Only time will tell, (unless someone who has experience with this can add a comment here). It seems to me to be the best answer I will be able to come up with to your question of how to have two operating systems share one /boot partition and have kernel updates automatically added to our grub menus.

Good luck and all the best with it, Regards, Herman :)

---

### Post by jmvidalvia on 2007-02-23
Hello Herman, 

Many thanks for your nice work.
I must have some time available to try this, as it sounds very convinient.
I will first make a complete backup of my system!
Thanks again!

---

### Post by Herman on 2007-02-23
Okay jmvidalvia, and thank you again for the great question, I had fun and learned some new tricks while I was working on it, 
Regards, Herman  :)

---

### Post by adrian15 on 2007-03-05
> **Herman said:**
> Hello jmvidalvia,
I am back to let you now that I have tested my first idea and found that it seems to be working very nicely for me so far. :)

Your idea works... but you need to edit update-grub, rename menu.lst, check I do not know what things about UUIDD but the root and setup commands procedure (install grub to a partition boot sector) does the same thing without too much work.

And you can still add a configfile "link" to the other partition's lst or chainload its grub.

**Anyways, thanks for the trick about editing update-grub and putting another filename for menu.lst. I did not know that one.**

adrian15

---

### Post by Herman on 2007-03-06
> Your idea works... but you need to edit update-grub, rename menu.lst, check I do not know what things about UUIDD but the root and setup commands procedure (install grub to a partition boot sector) does the same thing without too much work. I agree with you, adrian15, I don't see the need for people to use a seperate /boot partition these days and share it between OSes. Actually I always install the operating system all in the one partition. I use a USP, (unlimited power supply), and the ext3 or reiserfs file systems. They feature journalling, so they are not as likely to be corrupted in the event of a power failure as the older ext2 filesystems were. So I don't myself need to use more than one partition per operating system. (And of course, a swap area).

Installing grub the normal way so the main part lives in the operating system's partition would be best. 
A separate grub partition would be okay, one that is not part of any operating system. (As opposed to a /boot partition which is mounted as /boot in /etc/fstab).

This solution is only needed for people who already installed more than one operating systems with the separate /boot that they wanted to share and now they have run into a problem.

Regards, Herman :)

---

