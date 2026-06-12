---
title: "How do I remove second unwanted installation of 10.04 on dual boot (2 hdd) XP/Ubuntu"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by columbus2012 on 2010-10-05
Hi! all - my first post here - if I've picked the wrong sub forum for this mods please move.  

I have searched the Faq's but either it's not there or I'm asking the wrong question.

I’ve managed to get myself in a bit of a hole through  fears of destroying my WinXP on a new dual boot installation.  I’ve been using Ubuntu (10.04 lts) alone on an old machine which died, so I thought I’d just move the hdd to my main machine & dual boot it with XP. 

I booted from the 10.04 lts CD to set this up, I let it do as it suggested & assumed it would see the existing Ubuntu installation & modify it to dual boot with Win XP. Which it did **except **I now have two instances of 10.04 on the second hdd as it added a second partition for the new. Leaving the already installed 10.04 alone. 
I saw no options other than the advanced partitioning which I did not look at.  

How please can I correct this & go back to having just one instance of 10.04 on the Ubuntu disk to dual boot to – I am sure there must be an easy way.  I have nothing on the Ubuntu disk I need to preserve. 
I know nothing about Linux command line. So you will have to explain all if that is the way.  

Thanks in advance  :KS

---

### Post by krishnandu.sarkar on 2010-10-05
You should have just update the GRUB. Why did you even try to install it again..??

Delete the partition of 1st instance and boot using second instance. Then run sudo update-grub in terminal.

If anything goes wrong boot using the Live CD and refer [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to restore your GRUB.

---

### Post by columbus2012 on 2010-10-05
> **krishnandu.sarkar said:**
> You should have just update the GRUB. Why did you even try to install it again..??

Because I am a newby to linux as my post said, and the 10.04 installer was supposed to be intelligent. I did ask for the easy solution.

So what is GRUB & how do I update it? (I guess *you *also had to start somewhere)

I was using DOS back in the late 70's/80' so had some command line experience now rusty.

> Delete the partition of 1st instance and boot using second instance.How do I do that in Ubuntu please.

 > Then run sudo update-grub in terminal.

If anything goes wrong boot using the Live CD and refer [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to restore your GRUB.

---

### Post by Elfy on 2010-10-05
Which one do you wish to keep? The one on the transplanted hdd or the new one? 

First thing I would do is run this command - it will list the drives and partitions - it'll give people a chance to see what the current layout is of drives and partitions.

```
sudo fdisk -l
```

Most of the command line stuff could be done with graphical tools - but it is often quicker to get the information via a command - also it is generally desktop agnostic - ie you only need one command rather than a list of different places to look in different desktops (ubuntu /kubuntu /xubuntu for instance all have different menus and tools)

If you want to know what something does - don't be afraid to ask :)

Ps - the advanced/manual partition option would have allowed you to install over the original. Running some other commmands would have let you install a bootloader so you could boot it.

---

### Post by columbus2012 on 2010-10-05
OK! **forestpiskie**                thanks for a helpful start! it lists this;

desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf60bf60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6a2f6a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4914    39468091   83  Linux
/dev/sdb2            4914        9729    38679137+   5  Extended
/dev/sdb5            9495        9729     1887606   82  Linux swap / Solaris
/dev/sdb6            4914        9301    35233792   83  Linux
/dev/sdb7            9301        9494     1556480   82  Linux swap / Solaris
   

Partition table entries are not in disk order

> Ps - the advanced/manual partition option would have allowed you to  install over the original. Running some other commmands would have let  you install a bootloader so you could boot it.Too worried about killing my Win XP installation at the time :shock:

I don't care which I keep, the one at the start of the disk maybe - if it is easier to wipe the disk & start again there is nothing on it I am bothered about I've backed all else up.

---

### Post by Elfy on 2010-10-05
It's been a long day - meant to ask you to get df -h as well. But no matter ... this is MY df -h 

> Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Red"]/dev/sda6 [/COLOR]             18G  4.5G   12G  28% [COLOR="Red"]/[/COLOR]**
none                  1.5G  264K  1.5G   1% /dev
none                  1.5G  512K  1.5G   1% /dev/shm
none                  1.5G  116K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                   18G  4.5G   12G  28% /var/lib/ureadahead/debugfs
/dev/sdb1             917G  239G  669G  27% /mnt/sysmedia
/dev/sda7              48G  7.9G   39G  17% /mnt/spare

Now you can see that sda6 is mounted on / - this is my installed ubuntu - I do not want to remove this. 
(Well sometimes I do, but that's another story)

Now your fdisk output shows linux partitions on 

/dev/sdb1 * 1 4914 39468091 83 Linux
/dev/sdb6 4914 9301 35233792 83 Linux

At the moment we're not worried about the swap partitions.

If you ran df -h from within ubuntu - it would tell you either

/dev/sdb1           some numbers  /
or 
/dev/sdb6           some numbers  /

The one that df -h says is on / is the one you are running. 

You can safely remove the other if that is the one you wish to remove.

In fact you will be able to remove the unmounted one using gparted (once you've installed it) though you will need to turn swap off probably.



Another thing that you could do is run 

```
sudo update-grub
```

This _should_ add the 'other' install to the boot list.


Edit - in light of > I don't care which I keep, the one at the start of the disk maybe - if it is easier to wipe the disk & start again there is nothing on it I am bothered about I've backed all else up. The easiest thing is to remove the one that is not mounted :) (see df -h etc. )  It does make a difference though as to whether it's a logical partition. If you;re not sure run df -h and post it here

---

### Post by columbus2012 on 2010-10-05
:~$ sudo df -h shows this

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              34G  2.7G   29G   9% /
none                 1003M  300K 1003M   1% /dev
none                 1007M  324K 1007M   1% /dev/shm
none                 1007M   88K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw


> The easiest thing is to remove the one that is not mounted
sorry how? you're going to have to lead me by the hand - I do learn fast & sometimes even remember it tomorrow :)

And yes you are right it is late an hour more so here,  worse for old farts like me,  best to continue mañana :)

---

### Post by krishnandu.sarkar on 2010-10-05
Are you getting Windows..??

Then boot from Windows and delete one of the partition. Right click on My Computer > Select Manage > Go to Disk Management. Now delete one of the Ubuntu Partition.

Now reboot, if everything runs fine boot into Ubuntu and run sudo update-grub from terminal. Applications > Accessories > Terminal.

If you don't see the boot menu on reboot, boot using the Ubuntu live CD. Wait don't install it again. Just try it. And follow the tutorial I posted above to restore your GRUB.

BTW GRUB is the bootloader that you are using.

---

### Post by Elfy on 2010-10-05
Install gparted - you can find it in the software centre, synaptic or install it in a terminal with ```
sudo apt-get install gparted
```

You can find it once installed in the System Admin menu - obviously it is a partition editor - you can do damage if you are not careful (measure twice - cut once here ;) )

Once it is opem - using the drop down box in the top right (see screenie) pick the right drive first - which is sdb 

Once it has refreshed you will see the partitions on that drive - sdb1 shouldn't be mounted - it will not have a padlock symbol - this means you can work with it.

Right click and delete or format it. Then apply.

All done.


That though will not add the space to your current install - to do that is slightly more convoluted - as then you would have to do this from a livecd. It will also take longer to accomplish. Deleting a partition as above will be quicker than either typing or reading the post ;)

A reinstall using the whole of sdb would be quicker probably than resizing partitions (added some links below for resizing). Though if you choose that option be careful not to install to the wrong disk.

---

### Post by krishnandu.sarkar on 2010-10-05
> **forestpiskie said:**
> a reinstall using the whole of sdb would be quicker probably than resizing partitions. Though if you choose that option be careful not to install to the wrong disk.

+1

That would be much better option I think.

---

### Post by Elfy on 2010-10-05
2 excellent links to resources

[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by columbus2012 on 2010-10-06
> **forestpiskie said:**
> Install gparted - you can find it in the software centre, synaptic or install it in a terminal with ```
sudo apt-get install gparted
```You can find it once installed in the System Admin menu - obviously it is a partition editor - you can do damage if you are not careful (measure twice - cut once here ;) )

Once it is opem - using the drop down box in the top right (see screenie) pick the right drive first - which is sdb



Once it has refreshed you will see the partitions on that drive - sdb1 shouldn't be mounted - it will not have a padlock symbol - this means you can work with it. 


OK again thanks **forestpiskie** 
Would I be better mounting sdb1 as it is marked as boot, ( I get the  choice of either of the two or win at boot) then removing sdb2 which I assume is  the second (new) installation.  - Screen grab below




> Right click and delete or format it. Then apply.

All done.


That though will not add the space to your current install - to do that is slightly more convoluted - as then you would have to do this from a livecd. It will also take longer to accomplish. Deleting a partition as above will be quicker than either typing or reading the post ;)

A reinstall using the whole of sdb would be quicker probably than resizing partitions added some links below for resizing**.**        Though if you choose that option be careful not to install to the wrong disk. I guess I should get a book to learn the Linux syntax! can you recommend one? - I'm happy using terminal just don't know the language yet. In the short time I had sampled Ubuntu I just used it as graphical fo my bank acc's etc. as it is supposed to be virus bullet proof.

---

### Post by columbus2012 on 2010-10-06
OK! the new install seemed the easiest way to go,  so I have to admit I gave up and resorted to something I know & understand. I wiped the Hdd with DOS! - there I said it! :) and did a new install to the empty disk.

However, now I am clearly aware of what sda & sdb _actually_ stand for I realize I could have used the live CD installer.  sda & sdb is not intuitive to a DOS / Windows user so did not take the chance first time that I may destroy my Win installation.

Thanks for the help guys!!  :P

---

### Post by Greekbiggles on 2010-10-06
Hi all,

I too am an ex-pat with a double dose of Ubuntu!  I started on DOS (5, I think) back in the '80s and over the last couple of years have got so fed up with Windows I decided to convert.  My old Advent laptop got a new lease of life with Mandrake at first before I realised Ubuntu was the way forward.  After a few weeks with just a few problems that were easily sorted, I went for the big one on my home-built desktop but as a dual-boot with Win7 in case of problems (I did say it was home-built).

The install went well but I could not get the Grub screen on restart and had to use the Windows rescue disk to get the PC started on Windows (but only in DOS).  For Ubuntu I had to use the install disk 'try-out' mode.

Another go with the Ubuntu disk resulted in another 10.4 install, despite me trying to overwrite the first.  After a few days looking at several choices of Ubuntu + Win7 on the Grub menu I decided to remove all record of Ubuntu from the PC (using Win7) and do another install on a freshly partitioned disk (I'm using a 120 internal and two external HDDs of 1TB and 500 Gb).  The same result.  I binned the lot by reinstalling Ubuntu over the top of Windows and am now just running Ubuntu.

As a complete Ubuntu newbie I know there would have been a way round the problem and help from several good people to find it but there's something satisfying in hacking it yourself!

I've learnt a lot in the last month - not least of which is that life without MS Office is not too bad and my PC and Laptop have never been more stable.

Good luck, Columbus2012.

---

