---
title: "General error mounting filesystems"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Kjeldgaard on 2009-11-21
Hi

I made a fresh install of Karmic because I experienced a lot of problems when I first did the 9.04 -> 9.10 upgrade. And my computer (Asrock ION 330) worked perfect for a week or so! But when I turned it on yesterday it couldn't boot any more. I receive the following error.
```
General error mounting filesystems.
maintenance shell will now be started.
Control-d will terminate this shell and re-try.                      
```I have found some threads on this forum where the problem is solved by editing the /boot/grub/menu.lst file but i don't have this file.

[http://ubuntuforums.org/showthread.php?t=1299666](http://ubuntuforums.org/showthread.php?t=1299666)
[http://ubuntuforums.org/showthread.php?t=1308350](http://ubuntuforums.org/showthread.php?t=1308350)

How do I solve this problem when the menu.lst file is not present?

I don't know what caused the boot problem but I must have installed some updates...

---

### Post by drs305 on 2009-11-21
Since you made a clean install of Karmic you don't have a "menu.lst" file. You now use GRUB 2, which uses a different file system.

We don't have enough information to know if your problem is a GRUB issue or if something else has happened to your system.

Do you get a menu to boot from? If not, try holding down the SHIFT key early in the boot process to see if a menu appears.

There are various ways to boot into the system with G2. Here is a link if the problem is with the boot process itself:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

If you can get into your system using one of the above techniques, run "sudo update-grub" to see if refreshing the G2 menu solves the problem.

---

### Post by Kjeldgaard on 2009-11-21
If I don't do anything I end up at tty screen 1, asking for loign and password.

When I press and hold shift during grrb loading I have these choices:
Ubuntu, Linux 2.5.31-14-generic
Ubuntu, Linux 2.5.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

The grub is version 1.97b4.

If I edit first option (Ubuntu, Linux 2.5.31-14-generic) I get this:
```
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set d7654947-05c4-4645-9b54-d55de7704\
9d0
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d7654947-05c4-4645-9\
b54-d55de77049dp ro  quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
```I have never messed with this stuff before, so I have no idea what to look for.

Thanks in advance.

---

### Post by Kjeldgaard on 2009-11-24
I have not been able to solve my problem yet. So I decided to give some more info.

When I type
```
sudo fdisk -l
```I get
```
Disk /dev/sda: 320 GB,
255 heads, 64 sectors/track,38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e8a14fc
    Device Boot   Start      End         Blocks    Id   System
/dev/sda1   *         1    38913      312568641     5   Extended
/dev/sda5             1      486        3903732    82   Linux swap / solaris
/dev/sda6          1703    38913      298897326    83   Linux
/dev/sda7           487     1702        9767488+   83   linux

```And ```
df -l
```gives
```

Filesystem     1K-blocks       Used   Available  Use% Mounted on
/dev/sda7        9614116    3229780     5895964   36% /
udev              771836        244      771592    1% /dev
none              771836          0      771836    0% /dev/shm
none              771836         56      771780    1% /var/run
none              771836          0      771836    0% /var/lock
none              771836          0      771836    0% /lib/init/rw
/dev/sda6      294206372  267005320    12256188   96% /home

```As mentioned earlier I am not quite sure what to look for. So help is appreciated.

---

### Post by drs305 on 2009-11-24
Everything looks ok with what you have posted, other than you mention 2.5 instead of 2.6, but I assume that is just a typo.

The problem may not be with Grub. When you select the kernel from the menu, does it appear to start loading? That would be a problem with the system and not the menu/grub.

If it boots automatcally and you don't know when the problem occurs, hold down the SHIFT key during the early boot process to see if the menu appears. If/when it does, then choose a kernel and see when the problem occurs. Also, you might try a non-default option to see if another kernel works.

---

### Post by Kjeldgaard on 2009-11-24
> **drs305 said:**
> Everything looks ok with what you have posted, other than you mention 2.5 instead of 2.6, but I assume that is just a typo.

The problem may not be with Grub. When you select the kernel from the menu, does it appear to start loading? That would be a problem with the system and not the menu/grub.

If it boots automatcally and you don't know when the problem occurs, hold down the SHIFT key during the early boot process to see if the menu appears. If/when it does, then choose a kernel and see when the problem occurs. Also, you might try a non-default option to see if another kernel works.

Yes, 2.5 was a typo...

After I installed the newest updates I can now choose between
Ubuntu, Linux 2.5.31-15-generic
 Ubuntu, Linux 2.5.31-15-generic (recovery mode)
Ubuntu, Linux 2.5.31-14-generic
Ubuntu, Linux 2.5.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

but this has not helped me.

If I choose   "Ubuntu, Linux 2.5.31-15-generic (recovery mode)" everything looks fine and I end up in the recovery menu. Here I can choose among
resume, clean, dpkg, grub, netroot and root. If I choose "resume - resume normal boot" I am not receiving any errors and I end up at the tty1 login. After login I write "startx" I get this error:
```

(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

```So now I think it is a gfx driver problem.

---

### Post by drs305 on 2009-11-24
> **Kjeldgaard said:**
> 
So now I think it is a gfx driver problem.

Sounds like it. From the recovery mode can you access the System, Admin, Hardware Drivers and see if any drivers are listed.

There have been some users having problems with the -15 kernel. Can you boot into -14 from the main menu without any problems? You might need to run -14 for a while.

---

### Post by Kjeldgaard on 2009-11-24
I ran the following command
```
     sudo apt-get install linux-headers-generic nvidia-glx-185
```and now it works. After 4 days where I thought it was a boot problem it was a gfx driver problem. Thanks for your guidance.

---

### Post by Fatman_UK on 2009-11-26
I get the "general error mounting filesystems" and emergency console fiasco, though in a different place. What happened in my case:

After a Karmic upgrade from Jaunty, I did a 
```
sudo dpkg-reconfigure xdm
```
to enable xdm as my default greeter. (Gdm *would not* disable the face browser despite my best efforts.) Unfortunately xdm does not start at boot. I have to figure out why. To get into my LXDE session I start xdm manually.
```
sudo /etc/init.d/xdm start
```

On my first attempt, I don't manage to start xdm before this mountall error happens. I have to switch to another console, log in there and start xdm.
```
Ctrl-Alt-F2
```

After that, everything runs fine.

BTW, my graphics card is an ATI. So I don't think it's a graphics driver issue. Perhaps something deeper in the kernel.

---

### Post by tonytraductor on 2010-07-15
I don't understand how anyone can sudo apt-get or sudo aptitude ot sudo dpkg ANYTHING when this mountall error comes up.

I'm getting 
mountall: invalid option: --tmptime=0
General failure to mount filesystems

I get dropped to the root terminal.
Everything appears to be mounted, oddly, but all in READ ONLY,
so I am completely unable to alter anything, dkpg anything, aptitude anything, etc.

I'm kind of lost here.

Also, a googling of the above mountall error (tmptime=0) gives me nothing.

Anyone?

thanks
tony

---

### Post by tonytraductor on 2010-07-15
> **tonytraductor said:**
> I don't understand how anyone can sudo apt-get or sudo aptitude ot sudo dpkg ANYTHING when this mountall error comes up.

I'm getting 
mountall: invalid option: --tmptime=0
General failure to mount filesystems

I get dropped to the root terminal.
Everything appears to be mounted, oddly, but all in READ ONLY,
so I am completely unable to alter anything, dkpg anything, aptitude anything, etc.

I'm kind of lost here.

Also, a googling of the above mountall error (tmptime=0) gives me nothing.

Anyone?

thanks
tony

For some reason, I can't edit my post, so I'm quoting it.

I just wanted to add, I think it's pretty clear here that my issue is not a grub problem.
I imagine there is something in the mountall configs or something that I should be editing, but, of course, since everything it mounted read-only, I can't.
Trying to see if I can get in there using my 9.10 live-usb and edit stuff...
Of course, at this moment, I don't know what needs editing, yet, and, as mentioned, googling my specific error is not helping.
man mountall and mountall --help were completely useless, too.

---

### Post by djberndt on 2010-08-01
@tonytraductor

A friend had the exact same problem in carmic. Couldnt mount anything, or edit anything since since read-only. 

I solved it by typing (in root shell):

mount -n -o remount,rw /
aptitude --configure -a
xinit

this made me login to x and backup all data (since it was an encrypted ext4 with lost password). after that I just reinstalled ubuntu.

Hope it helped =)

---

