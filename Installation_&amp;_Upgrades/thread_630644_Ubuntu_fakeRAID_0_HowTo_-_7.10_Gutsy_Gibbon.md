---
title: "Ubuntu fakeRAID 0 HowTo - 7.10 Gutsy Gibbon"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Keldek on 2007-12-03
I pulled most of the info for this HowTo from [COLOR="Blue"][http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation) [/COLOR]though some of these steps didn't work properly for me, so I thought I'd update it. Several steps however are copy/pasted from the above url.

First, my install included dual booting into Windows XP Pro, whose base system is on a 10GB partition located on the RAID 0 set we'll be installing Ubuntu to; but this guide will work even if you don't plan on dual booting.

**_Here are my system specs to give a general idea of how things will go:_**
Asrock AliveNF5-VSTA mobo
AMD Athlon 64 X2 5600+ AM2 processor
2GB DDR2 RAM
Nvidia Geforce 8800GTS vid card
2x 250GB SATAII HDDs in *fake*RAID0
2x 250GB SATAII HDDs in *fake*RAID1
Nvidia onboard RAID controller

[[COLOR="Blue"]Booting to the live CD with Radeon X1800[/COLOR]]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Booting_to_the_live_CD_with_Radeon_X1800")

**_Installation on RAID 0_**

Here's what you need: 
[LIST]
[*]1 [[COLOR="Blue"]Ubuntu 7.10 live desktop CD[/COLOR]]("http://www.ubuntu.com/getubuntu/download"). I used the i386 version (for 32 bit processors), but this guide should work with the AMD64 (for 64 bit processors) version of Gutsy. 
[*]2 An internet connection. There is wonderful wireless support in Gutsy, but you might want to have a wired connection to be safe.
[/LIST]


**_Partitioning and Installation_** 
[LIST]
[*]1 Administration > Software Sources. Check 'Community-maintained Open Source software (universe)'. When prompted to, reload the repositories. 
[*]2 Open a Terminal and type:
```
sudo apt-get install dmraid
```
[/LIST]

Now, the guide I linked above instructs to use gParted to set up your partitions. I tried this countless times only to have gParted crash and burn each time. So we'll go through the partitioning manually.

**Get our RAID devices**:
```
sudo dmraid -r
```

For my setup, I get the following returned:
```
/dev/sda: nvidia, "nvidia_ciaejcff", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_ccbdjacd", mirror, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_ciaejcff", stripe, ok, 488397166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_ccbdjacd", mirror, ok, 488397166 sectors, data@ 0
```
(We'll ignore the mirrored set for now as we won't be using it)

**Create our partitions:**
```
sudo fdisk /dev/mapper/nvidia_ciaejcff
```

This'll open up fdisk for the stripe set. Setting up the partitions in fdisk is fairly straightforward:

Sample:
```
Command (m for help): p
```
Returns
```
                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_ciaejcff1   *           1        1305    10482381    7  HPFS/NTFS
/dev/mapper/nvidia_ciaejcff2            1306       60802   477909652+   5  Extended
/dev/mapper/nvidia_ciaejcff5            1306        2551    10008463+  83  Linux
/dev/mapper/nvidia_ciaejcff6            2552        7532    40009851   83  Linux
/dev/mapper/nvidia_ciaejcff7            7533        8031     4008186   83  Linux

```

[LIST]
[*]1 /dev/mapper/nvidia_ciaejcff1 == Windows Base Partition
[*]2 /dev/mapper/nvidia_ciaejcff2 == Extended
[*]3 /dev/mapper/nvidia_ciaejcff5 == /
[*]4 /dev/mapper/nvidia_ciaejcff6 == /home
[*]5 /dev/mapper/nvidia_ciaejcff7 == /swap
[/LIST]
*Note: Partition numbers 3 & 4 are missing because they're reserved for primary partitions. My setup has 1 primary partition, 1 extended partition (which takes the place of a primary partition) and 3 logical partitions.

If you need help setting up your partitions using fdisk, you can type 'man fdisk' from a separate terminal and read through the documentation. Generally, 'p' prints your proposed partition layout. 'n' creates a new partition (this is pretty straightforward, though you should probably plan out what partitions you want, and what size you want them before modifying your tables.) For each new partition I used the default start blocks, then specified the end blocks by size (ie "+10240M").

Once you're satisfied with your partition layout, do
```
Command (m for help): w
```
to apply the changes, then type 'quit' to exit fdisk

Now we need to create the FileSystem for each partition we created (I don't know why, but the installer would NOT 'format' the FileSystems if I didn't manually create them first.)
```
sudo mkfs.ext3 -t /dev/mapper/nvidia_ciaejcff5

sudo mkfs.ext3 -t /dev/mapper/nvidia_ciaejcff6

sudo mkswap -c /dev/mapper/nvidia_ciaejcff7
```

**_Restart Your Computer_**
Yes, for some reason, the installer would not read my new partitions without rebooting first. From what I've read, doing 'sudo dmraid -r' should refresh the partition layout, but it didn't for me. So we'll go ahead and restart the system and boot back into the Live CD.

Once we're back in the Live CD, we have to install dmraid again:
[LIST]
[*]1 Administration > Software Sources. Check 'Community-maintained Open Source software (universe)'. When prompted to, reload the repositories. 
[*]2 Open a Terminal and type:
```
sudo apt-get install dmraid

sudo dmraid -r
```
[/LIST]

Now that we've rebooted, reinstalled dmraid and made sure dmraid is reading our devices properly, we can go ahead and start installing.

Double click on the 'Install' icon on your desktop and let's begin.
Select the proper settings for your system, then once you get to the partitioner, Select Manual and click Next:

The partitioner will look a bit confusing at first, so I'll explain what needs to be done to ensure you don't wipe your tables and have to start over (like I did a few times before I found the guide linked above lol).

You'll see 2 'sections' for your instance of /dev/mapper/nvidia_ciaejcff.

The First Section will look something like this:
```

> /dev/mapper/nvidia_ciaejcff
      /dev/mapper/nvidia_ciaejcff             10240MB
      /dev/mapper/nvidia_ciaejcff             10240MB
      /dev/mapper/nvidia_ciaejcff             40960MB
      /dev/mapper/nvidia_ciaejcff              4096MB

```

For each entry you see listed in this 'section', you **MUST** right click > Edit partition > Select 'do not use'. If you don't do this for each entry, as soon as you go to write the changes, you'll wipe your current layout and have to start over.

The next 'section' you'll see looks something like this:
```

> /dev/mapper/nvidia_ciaejcff
      /dev/mapper/nvidia_ciaejcff1   HPFS/NTFS                                      10240MB
      /dev/mapper/nvidia_ciaejcff5        Ext3        /mnt/media/nvidia_ciaejcff5   10240MB
      /dev/mapper/nvidia_ciaejcff6        Ext3        /mnt/media/nvidia_ciaejcff6   40960MB
      /dev/mapper/nvidia_ciaejcff7        swap                                       4096MB

```

Change the Mount Points so they look like this:
(right click each numbered partition, select 'edit partition' to change the MountPoint)
```

> /dev/mapper/nvidia_ciaejcff
      /dev/mapper/nvidia_ciaejcff1   HPFS/NTFS                                   10240MB
      /dev/mapper/nvidia_ciaejcff5        Ext3        /                          10240MB
      /dev/mapper/nvidia_ciaejcff6        Ext3        /home                      40960MB
      /dev/mapper/nvidia_ciaejcff7        swap                                    4096MB

```

Now, you can choose to have the installer 'format' the ext3 partitions again, but since they're empty, there's really no need. Be sure to change each numbered Mount Point so they match the partition layout plan you made earlier.

Once you're finished laying out the partitions, continue through the installer until it gives you a critical error saying that grub wasn't installed.

**_Installing GRUB_**

Move some important system stuff over to the new installation of Ubuntu
Note: You may get errors about some of these things already being done for you. That's fine. Just do them all to be safe. I have commented the ones were not necessary for me. replace <RAID_SET_NAME> with the name that you wrote down earlier. The same goes for <PART_NUM>

```
sudo mount -t ext3 /dev/mapper/<RAID_SET_NAME><PARTITION_NUM> /target
```
For me this was "sudo mount -t ext3 /dev/mapper/nvidia_ciaejcff5 /target"
```
sudo mount --bind /dev /target/dev
sudo mount -t proc proc /target/proc    # was already done
sudo mount -t sysfs sysfs /target/sys
```

Copy some necessary files from the live CD over to the new installation of Ubuntu
```
sudo cp /etc/apt/sources.list /target/etc/apt
sudo cp /etc/resolv.conf /target/etc
```

Now point the terminal to start working with your new installation instead of the live CD
```
sudo chroot /target
```

Update the new installation and install dmraid and grub
```
apt-get update
apt-get install dmraid
apt-get install grub    # might already be installed
```

Copy some grub files to the proper directory
```
cp /usr/lib/grub/i386-pc/* /boot/grub
```
Replace "i386" with "x86_64" if you are using the AMD64 live CD

Open grub
```
grub
```

This will take you to the grub command prompt where you will enter the following commands.

```
device (hd0) /dev/mapper/<RAID_SET_NAME>
```
(hd0) represents the first hard drive in my computer, the "raid disk", not the partitions
```
find /boot/grub/stage1
```
Take note of the output of this command. it should be something like "(hd0,4)"
```
root (hd0,4)
```
Change "(hd0,4)" to the output of the last command. What "(hd0,4)" means is "hard drive 1, partition 5".

```
setup (hd0)
quit
```

Now you should be back to the normal terminal (but still "chroot"'ed into the new installation with "sudo chroot /target"). You now need to set up the GRUB configuration file. Run:
```
update-grub

```
When prompted to create a new menu.lst file, enter "y" for yes.

We need to edit the menu.lst file and put some of our own modifications:    
```
sudo nano /boot/grub/menu.lst
```
This will open a command line text editor. To save and exit, press CTRL+X, then press "y", then press "enter"

[LIST]
    [*]1  Now you need to edit menu.lst to be fully set up for your RAID (and your Windows partition if one exists). Scroll to the bottom of the file. You should see some sections talking about "root" and "kernel". Change any occurences of "(hd0,0)" to whatever you entered when you set up grub. Since my <PARTITION_NUM> was 2, I entered replaced "(hd0,0)" with "(hd0,1)" (meaning "hard drive number 1, partition number 2").
    [*]2 If you want to add a section to be able to boot to windows, copy the last section from the snippet below.
    [*]3 Here is what the bottom section of my menu.lst looks like:
[/LIST]
```
## ## End Default Options ##

title           Ubuntu 7.10
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/nvidia_ciaejcff5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/nvidia_ciaejcff5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP
root            (hd0,0)
chainloader     +1
boot
```


**_Finish up_**

You should be able to restart your computer now 

```
sudo shutdown -r now
```
Remove the cd when prompted and you should now be able to boot into your new Install.

---

### Post by Velociraptor on 2007-12-06
Wow, I now have Ubuntu back running on my machine (amd64/dmraid). Thanks for the info!

The only thing i did differently, was in the grub command prompt: "find /grub/stage1" instead of "find /boot/grub/stage1". I think because i have /boot in it's own partition, which gets mounted onto /boot of the root partition.

I also had to manually hack the /etc/fstab, to mount by, e.g., "/dev/mapper/nvidia_bdchaeef8" instead of "UUID=...". With UUID, it wasn't able to mount my home and boot partitions. And so wouldn't let me log on.

---

### Post by pinow on 2007-12-08
This was exactly what I was looking for.

Thanks! =D>

---

### Post by spartan777 on 2007-12-11
excellent how-to, but i'm wondering how to simply *read* my (fake) raid hard drives. i have an asus k8v se deluxe mobo, which has via fake raid. i've never once come close to being able to read from those drives. i have windows installed on them, so i don't want to install to them, just read and write some files.

---

### Post by Velociraptor on 2007-12-12
To read from Windows that is installed on a fakeraid, it should be just a case of installing dmraid, I think:

   sudo apt-get install dmraid

You can then check if dmraid has detected your fakeraid:

   sudo dmraid -r

The fakeraid device should also be listed in /dev/mapper, together with a device for each of the partitions. You then need to mount the partition you want to read from, e.g.,:

   sudo mkdir /windows
   sudo mount /dev/mapper/via_ciaejcff5 /windows

(Sorry I'm not at by Ubuntu machine, but I think that should do the trick.)

---

### Post by kevpatts on 2008-01-10
Thank a lot for this how to. Haven't tried but will VERY tomorrow. Here's another question: can you do the same with RAID 5???

Kevpatts

---

### Post by timbounceback on 2008-01-10
looks like a nice howto, why not move it to the tutorials/howto section?

---

### Post by kevpatts on 2008-01-10
> **kevpatts said:**
> Thank a lot for this how to. Haven't tried but will VERY tomorrow. Here's another question: can you do the same with RAID 5???

Kevpatts

That worked _perfectly_. Some differences I noticed were that I had to restart BEFORE formatting the partitions innstead of after. Apart from that it was spot on. I recommend turning off "keephidden" in the menu.list also if you have a windows partition.

Thanks a million, been trying to do this for about a year.

---

### Post by kevpatts on 2008-01-11
Come to think of it, I'm going to be putting a RAID 5 machine together next week and with this how-to combined with info here: [http://ubuntuforums.org/showthread.php?t=401295](http://ubuntuforums.org/showthread.php?t=401295) i may be able to get it working (although I don't know if it's possible to recompile the kernel at the stage above after doing the "sudo chroot /target" or to patch and recompile dmraid at the same stage.

It's always worth a try!

Kevpatts

---

### Post by Desperate on 2008-01-11
Thanks Keldek for all the typing. I might be able to access my disk after all.
And thank you all for the additional info

More to learn, more to read :)

---

### Post by tad1073 on 2008-01-11
Slot 2 Compaq Smart Array 431 Controller
System Embedded IDE Controler
Slot 3 Compaq Wide/Ultra2 SCSI Controller

after I do sudo dmraid -r the out put is a bunch of errors then No RAID Disk at the end, I would post the results but my cd-rom won't stop spinning and ubuntu becomes unusable I actually have to turn it off wtih the power button.

---

### Post by pokerFace12344321 on 2008-01-13
Make sure your motherboard (1) can handle raid and (2) is set up to do raid.

I was getting the "no raid disk" message a lot.
The message went away when I added a new raid disk through the raid controller utility.
I noticed all these raid guides assume you know to do that. I didn't.

Here's what I did to get rid of the "no raid disk" message:

1. Restarted the computer
2. During the appropriate time in bootup, pressed [CTRL + i] to configure the raid controller (the key sequence might be different on different motherboards). This opens a raid configuration program.
3. Added a new raid array through the program. The program automatically added both my hard drives to the array (this may not be as automatic for different motherboards). Then I exited the configuration program. I added a raid0 array because that's what I want -- your preferences may vary.


Also, in the "peripherals" section of my BIOS, I made sure the hard drives were configured in a RAID array (as opposed to IDE or DCHI). This might only pertain to SATA drives, I'm not sure.
Note: I kept the CD bios setting on the IDE option, otherwise ubuntu would not boot from the CD.

Good luck.

---

### Post by Wolver1n3 on 2008-01-24
Dude You are GOD!!! After following countless FakeRAID HowTo's [that led me to reinstalling Vista 2 times and fixing the MBR like 3 time in between] the simplest one  worked like a charm I feel like I got to donate or something many many thanks to you bro, I pretty much skipped the whole Ubuntu 6.10/7.4 on my home PC because I could not dual boot with Vista/LNX with RAID0 so i was restricted to Ubuntu on my Laptop only but now thanks to you and the people/post that helped you make this so very simple to follow HowTo I am now a happy Ubuntu on RAID0 user **[COLOR="Red"][and Windows user exclusively for gaming][/COLOR]**. It just cant be any more easier then this.

---

### Post by Chavez_Ninja on 2008-01-28
Can you make a raid0 without having any aditional raid cards (just dell motherboard and 2 hd's)?

Thanks

---

### Post by kevpatts on 2008-01-29
it depends on your motherboard but I doubt it on a dell (not in Ireland anyway). The motherboard itself would have to support RAID0 meaning you'd probably need a nVidia nForce 4xx, 5xx or newer board. have a look at the stats of your PC, it would normally specifically say if it supports RAID.

---

### Post by Siyfion on 2008-01-31
My problem is that after doing the "sudo dmraid -r" I get this:

```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 624737856 sectors, data@ 0
/dev/sdb: ddf1, ".ddf1_disks", GROUP, ok, 624737856 sectors, data@ 0
/dev/sdc: ddf1, ".ddf1_disks", GROUP, ok, 489972231 sectors, data@ 0
/dev/sdd: ddf1, ".ddf1_disks", GROUP, ok, 489972231 sectors, data@ 0

```

Now thats all well and good, but it doesn't seem to have realized which drives are in which array. Although I know that the top two are in a Raid 0 and the bottom two are in another Raid 0.

I have posted a thread about this and what I need to do, as I am actually using an Adaptec 1430SA raid card, although it uses HostRAID, which I though dmraid supported!?:confused:

---

### Post by imtheguru on 2008-01-31
> **kevpatts said:**
> it depends on your motherboard but I doubt it on a dell (not in Ireland anyway). The motherboard itself would have to support RAID0 meaning you'd probably need a nVidia nForce 4xx, 5xx or newer board. have a look at the stats of your PC, it would normally specifically say if it supports RAID.

Linux supports softraid though dmraid. There is no need for a raid controller on the motherboard. In fact i'm not sure why the author has gone in for a fakeraid using the  onboard RAID controller when a softraid would've sufficed just as well. Migrating this raid to another controller will be between difficult and impossible.

Perhaps the aim was to mix-n-match operating systems? But, in addition to the natural failure characteristics of raid0, one has gained the possible failure of the hardware raid controller and that of another.

Backup often, hopefully to tape.

---

### Post by Siyfion on 2008-02-01
Hardware RAID does come with it's performance upside's though. :)

---

### Post by PKdoR on 2008-02-03
Well first of thanks for the great HowTo, I gues simmple is better sometimes, I managed to install a fully working RAID0 tripple boot thanks to this HowTo, But I also managed to screw it up after while triying to install GFXBoot, While Grub is probably the best boot loader out there (it'll chaindload a microwave if you got the skills) it does fall aliltle on the dull side. Is there any way you can make a how o for RAID0+GFXBoot or Splashy based on this HowtTo? In the mean time I'll keep using Vanilla GRUB.

---

### Post by skink-in-trees-shade on 2008-02-06
Hello everybody, 

I'm using the guide posted here to install Ubuntu on a RAID0-configured array and it all works just fine until I tell GRUB to find /boot/grub/stage1 (or /grub/stage1), at which point I get an "error 15: file not found" message. 

The personal computer I'm trying to configure is a Dell XPS 420, 2 gigs RAM, Intel core 2 quad core viiv Q6600, dual 250 gb hard disk with intel software RAID.
Could someone help me please? 
 
Thanks in advance, and sorry for my bad english!

---

### Post by Crass Spektakel on 2008-02-08
Based on [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) and 
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0) 
I did setup ubuntu on a Fake-RAID.

It was surprisingly straight forward and deep inside it works well - but the initrd makes a stupid mistake. The RAID gets mapped into /dev/mapper, but everytime with another name. And guess what, Grub can not boot from a wildcard. Its more visible if watched from the rescue shell of the initrd:

on first boot the device is known as /dev/mapper/ddf1_4c53492020202020808626820000000034dd4fb400000a28

and on the next boot os
/dev/mapper/ddf1_4c53492020202020808626820000000034dd4fb500000a28

As you an see the device name contains the pci-id and most likely a start counter and grub can not boot from an unknown device which is changing its name on every boot.

 Any idea?

---

### Post by Siyfion on 2008-02-08
I have set up my "/home" mount as per this guide on a seperate raid disk.. (I have two) However everytime I boot into Ubuntu it doesn't seem to mount the "/home" directory to my "/dev/mapper/ddf1_Slave1" device. So I have to log into a safe terminal, mount, then re-login again.

Ideas?:confused:

---

### Post by kevpatts on 2008-02-11
Hey guys, if I now update my kernel I'm pretty sure I won't be able to boot. is this correct? I'm guessing this because when I installed the Xen kernel I couldn't boot. Do I have to set up grub again before restarting, or maybe dmraid?

kevpatts

---

### Post by @xi0m on 2008-02-16
I can't seem to install dmraid.  I have checked the "community maintained open source software" option and reloaded the repositories.  When I search for dmraid I get no results.  When I try to install it via the command like I receive:
> ubuntu@ubuntu:~$ sudo apt-get install dmraid
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package dmraid
ubuntu@ubuntu:~$

Fedora was able to detect my raid with no problems.  How come Kubuntu can't?

---

### Post by Chris_Z on 2008-02-16
Hi,

I have applied this magnificent guide for RAID 1, everything else being equal. And it works!
(I know, it's slightly off-topic but a success story never the less. And yet I'm a Linux newbie ;-)

H/W: Intel ICH9R SATA RAID Controller, 2 disks with partition layout exactly like in the guide. 

However some slight modifications proved to be necessary. 

One was mentioned earlier in this thread (the name of the raid array given in BIOS is concatenated to whatever is reported by 'sudo dmraid -r', iow whenever the guide refers to <RAID_SET_NAME>, found the correct name by issuing 'ls /dev/mapper' ).

The second one affected the paragraph where the guide refers to 'sections' presented by partitioner and so called First Section. Actually there were four sections, two beginning with /dev/mapper/... and two beginning with /dev/sda... and /dev/sdb...

I have  marked with 'do not use' three of them, leaving alone the section which to largest degree resembled what is shown in the example shown in the guide. Be careful there, it's easy to make mistake here as what you see in partitioner looks quite different from the guide.

Third difference was where you install GRUB and issue 'find /boot/grub/stage1'. 
In my case it returned two drives: (hd0,4) and (hd1,4). I used the first one.

Lastly, do not forget to edit the menu.lst and edit kopt=root=/dev/mapper/... and groot=(...).
I also had to edit /etc/fstab to get rid of UUID= because Ubuntu won't boot otherwise.
Be careful as any spelling mistake there will render the whole volume being ReadOnly after reboot. 

Hope this helps someone.

Best!
/Chris Z.

---

### Post by glushkov on 2008-02-17
After following this tutorial I rebooted and I get a grub screen saying:

Error 17: Cannot mount selected partition
Press any key to continue...

Then the usual GRUB login screen appears, and when selecting Ubuntu, again the same Error 17 appears..

Any idea how I can fix this? :confused:

---

### Post by dldeskins on 2008-03-10
Keldek,

Thank you so very much for your effort.  Your very detailed instructions allowed me to put Ubuntu on my old server, specs:
3U server
Intel motherboard with dual PIII 1.8 ghz, 2gig ram
On board Promise FastTrak 100 raid controller
2 Ultra ATA 100 120gig hdd

I had been using this machine for a home file server and web development box.  This was an "inherited" box that I have had about 3 1/2 years and had windows 2000 server.  Someone configured it for me with Redhat 9.0 (he tried to put Redhat Enterprise on it, but had problems with the FastTrak100).  It worked well for me, but I wanted to be able to update, etc.

When I got it installed, I was amazed at how fast it started up and ran.  But i am having some issues.

1.  When I go to the terminal with my regular username, it has so odd stuff going on.  The prompt doesn;t have my username@machine, but only the $.  Also, there is no autocomplete with the tab.  (I created a separate user, and everything is normal).  Suggestions?
2.  Under System>Administration, "Synaptic Package Manager" is not an option.  When I try to add it to the menu (and Services,Software Sources,etc) through main menu, the box unchecks itself when I check it.  Suggestions?

Thank you again!!
Don

---

### Post by iandotcom on 2008-04-14
I got my own problem, but theres how you can fix one of the problems someone had above me.

> **@xi0m said:**
> I can't seem to install dmraid.  I have checked the "community maintained open source software" option and reloaded the repositories.  When I search for dmraid I get no results.  When I try to install it via the command like I receive:


Fedora was able to detect my raid with no problems.  How come Kubuntu can't?

I had this problem too.

I solved it by doing the following. Make your you're chrooted into the new install as it says on this tutorial. In the terminal, type in the following:

```

sudo nano /etc/apt/sources.list

```

This will bring up the sources.list in the terminal and will allow you to edit it.

There are two lines which have a single # before them, the comments on that file will show you where they are. All you need to do is move to these lines and delete the #'s. This will allow apt-get to use the source list which dmraid is found on.

Once done, press CTRL + O, then hit return. Then press CTRL + X to close the editor.

You should then be able to continue the steps in the tutorial. I hope this helps.

Anywho, here is my question.. I have followed the tutorial through, but when I come to boot, I am able to choose the correct OS but when the Ubuntu splash screen appears there is no progress on the progress bar shown.

Does anyone have any ideas?

---

### Post by Siyfion on 2008-04-14
Try loading it with the no splash option on, and then look at the text output. :)

---

### Post by ghostic on 2008-04-16
I jest not so? without chroot does not make sense to continue the installation ..

ubuntu 7.10 x64 live cd

```
ubuntu@ubuntu:~$ sudo apt-get install dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dmraid
0 upgraded, 1 newly installed, 0 to remove and 90 not upgraded.
Need to get 201kB of archives.
After unpacking 729kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com gutsy/universe dmraid 1.0.0.rc13-2ubuntu5 [201kB]
Fetched 201kB in 0s (268kB/s)  
Selecting previously deselected package dmraid.
(Reading database ... 90254 files and directories currently installed.)
Unpacking dmraid (from .../dmraid_1.0.0.rc13-2ubuntu5_amd64.deb) ...
Setting up dmraid (1.0.0.rc13-2ubuntu5) ...
 * Setting up DMRAID devices...                                          [ OK ] 
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

ubuntu@ubuntu:~$ sudo mount -t reiserfs /dev/mapper/nvidia_aaeebgjd5 /target
mount: mount point /target does not exist

ubuntu@ubuntu:~$ sudo mkdir /target

ubuntu@ubuntu:~$ sudo mount -t reiserfs /dev/mapper/nvidia_aaeebgjd5 /target

ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev
mount: mount point /target/dev does not exist

ubuntu@ubuntu:~$ sudo mkdir /target/dev

ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev

ubuntu@ubuntu:~$ sudo mount -t proc proc /target/proc
mount: mount point /target/proc does not exist

ubuntu@ubuntu:~$ sudo mkdir /target/proc

ubuntu@ubuntu:~$ sudo mount -t sysfs sysfs /target/sys
mount: mount point /target/sys does not exist

ubuntu@ubuntu:~$ sudo mkdir /target/sys

ubuntu@ubuntu:~$ sudo mount -t sysfs sysfs /target/sys

ubuntu@ubuntu:~$ sudo cp /etc/apt/sources.list /target/etc/apt
cp: accessing `/target/etc/apt': Not a directory

ubuntu@ubuntu:~$ sudo mkdir /target/etc

ubuntu@ubuntu:~$ sudo mkdir /target/etc/apt

ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /target/etc

ubuntu@ubuntu:~$ sudo chroot /target
chroot: cannot run command `/bin/bash': No such file or directory
```

---

### Post by jimclarke on 2008-04-19
Hmm somewhere my attempt went astray and it setup like a normal drive. I need to reread the instructions and try again. 

Asus K8N4-E Deluxe motherboard
Sempron 3400+ 64 Bit
1GB DDR Ram
2 x Seagate 6B300S0 300GB Sata HD
Nvidia Raid0
ATI R550 PCI-E Video
8.04 RC Hardy Heron

Linux knowledge> zero

Maybe I'll move the drives down to the Sil 3114 controller and try again

Hey, this is a good way to learn.:lolflag:

---

### Post by Herbert_Vaucanson on 2008-04-29
Hi all!

First of all, thanks for the guide.

In second place, I have a problem: I am installing Ubuntu 8 mimiking the guide.

I install dmraid (sudo apt-get install dmraid; sudo dmraid -r) and see the array, then I partition it as I like (sudo fdisk /dev/mapper/mambojamboarrayname), reboot (reinstalling dmraid) and proceed to successfully format the disks.

Afterwards I shut down (must-get-sleep) and today I pick up where I left. I boot, install and launch dmraid, I get the correct array name at the dmraid nstallation but the /dev/mapper directory is EMPTY, with the exception of something called "control". Yep, no device map. As I look at the drives through the graphic navigator, I see them doubled (I have a mirroring setup) but no array.

Any ideas how Bad Things happened?

P.S.: I got a Gigabyte p35ds3r mobo, Intel Ich9r chipset, and WinXP squatting on the array confortably enough to boot without a curse.

---

### Post by Muhahahahaz on 2008-05-04
Hi, I seem to be having problems getting dmraid to work.  I already have Vista Ultimate 64-bit installed on a 150GB partition of my 2x320GB Raid 0, so the Raid is working, from Window's point-of-view.

When I get to the "dmraid -r" step, this is what I get:

```
root@ubuntu:~# dmraid -r
/dev/sdb: isw, "isw_djdechbidg", GROUP, ok, 625142446 sectors, data@ 0
/dev/sda: isw, "isw_caidcfifff", GROUP, ok, 625142446 sectors, data@ 0
root@ubuntu:~# dmraid -ay
ERROR: isw device for volume "Volume0" broken on /dev/sdb in RAID set "isw_djdechbidg_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_djdechbidg_Volume0" [1/2] on /dev/sdb
ERROR: isw device for volume "Volume0" broken on /dev/sda in RAID set "isw_caidcfifff_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_caidcfifff_Volume0" [1/2] on /dev/sda
root@ubuntu:~# cd /dev/mapper/
root@ubuntu:/dev/mapper# ls
control
root@ubuntu:/dev/mapper#
```

As you can see, "dmraid -r" seems to give two different Raid names, and "dmraid -ay" simply fails.  It doesn't mount any Raid 0 device at all.  Help! :(

I have nothing important on my Raid (separate 750GB HDD for storage), so believe me, I have tried so many times of reinstalling in different ways to get this working, but I simply can't seem to make it work. :(

---

### Post by Muhahahahaz on 2008-05-04
> **Herbert_Vaucanson said:**
> Hi all!

First of all, thanks for the guide.

In second place, I have a problem: I am installing Ubuntu 8 mimiking the guide.

I install dmraid (sudo apt-get install dmraid; sudo dmraid -r) and see the array, then I partition it as I like (sudo fdisk /dev/mapper/mambojamboarrayname), reboot (reinstalling dmraid) and proceed to successfully format the disks.

Afterwards I shut down (must-get-sleep) and today I pick up where I left. I boot, install and launch dmraid, I get the correct array name at the dmraid nstallation but the /dev/mapper directory is EMPTY, with the exception of something called "control". Yep, no device map. As I look at the drives through the graphic navigator, I see them doubled (I have a mirroring setup) but no array.

Any ideas how Bad Things happened?

P.S.: I got a Gigabyte p35ds3r mobo, Intel Ich9r chipset, and WinXP squatting on the array confortably enough to boot without a curse.

What do "dmraid -r" and "dmraid -ay" say?

I have the same board, btw. :)

---

### Post by Muhahahahaz on 2008-05-04
Ok, so check this out.  I deleted the Raid, but "dmraid -r" still gives me this:

```
root@ubuntu:/dev/mapper# dmraid -r
/dev/sda: isw, "isw_caidcfifff", GROUP, ok, 625142446 sectors, data@ 0
root@ubuntu:/dev/mapper#
```

I've tried formatting both disks, etc., but I can't get this phantom Raid to go away!  Any ideas?

---

### Post by Muhahahahaz on 2008-05-04
I finally got rid of the Phatom Raid! :D

It's dangerous to go alone, use this:

```
dmraid -rE
```

I haven't installed anything yet, but I finally got it to do something that I wanted!  Apparently there was some "metadata" left on the Raid, even though I had told the Intel setup to delete the Raid.  The above command deletes all of the Raid metadata, thankfully.  Gah, that was so annoying. :rolleyes:

Anyways, now to see if I can follow the guide.  I should be able to, since I almost did once... but then there were problems...

---

### Post by rygle on 2008-05-16
> **Muhahahahaz said:**
> 
I finally got rid of the Phantom Raid! :D

It's dangerous to go alone, use this:
```
dmraid -rE
```


Doesn't that kill the whole raid array? Do you have to install Windows again? I'm not game to try that option.

Rygle

---

### Post by talsemgeest on 2008-07-15
Thank you for everything, this is an absolutely brilliant thread, thank you for your help.

---

