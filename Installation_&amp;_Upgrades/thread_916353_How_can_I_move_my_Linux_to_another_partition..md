---
title: "How can I move my Linux to another partition."
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by gandalf2000 on 2008-09-10
I have Ubuntu set up on the master hard disk dual booting with XP (which I almost never use).  Now, I want to move the Linux to the slave disk (which is newer and much bigger) but don't know how.  I tried to follow a how to using "dd", whatever that is, and it wrote something to the target partition but what it wrote is twice the size of what I was trying to move.  Not only that but now I can't access that partition.  I guess I will run gparted and delete that partition and then set it up again.  But how can I migrate the Ubuntu os to the other disk?

---

### Post by Pumalite on 2008-09-10
You can use clonezilla:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by gandalf2000 on 2008-09-14
Thank you for answering, Puma.  I have been busy and unable to acknowledge your reply.  I have downloaded and tried twice with Clonzilla as you suggested but I must be doing something wrong.  After it is finished I can't access the partition that it was put on.  It shows up in gparted as ext3 with a warning triangle and exclamation point but that is the only place it shows.  I suppose I will have to edit the grub after it is done which means a live boot to do.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi gandalf2000,

This is how I would do it :

- Boot ubuntu livecd

- Format your new drive with the partition editor.

- Mount both your old and new partitions (using icons on the desktop or sudo mount).

- Copy linux to your new partition with sudo cp -a /media/oldpartition/* /media/newpartition/

- Use a ubuntu recover grub manual, this one for example [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

- That's it, may it help

Edit :

Don't use use it, that's what I would do, but I forgot an important afterstep. Here a copy/paste from below.

It involves modifying the /etc/fstab to match the new filesystem's uuids, doing the same to /boot/grub/menu.lst, setting up grub in mbr, changing root(X,Y)-related entries in grub's config, rebuild auto-generated entries with update-grub, dynamically modifying grub's entries at boot time or using chroot ... basically things that would fly way over your head unless you understand what I am saying and can change them yourself (in short, change uuids where relevant, change grub's config, reinstall grub in mbr, boot, use update-grub).

---

### Post by Pumalite on 2008-09-14
Before you do anything; post:
sudo fdisk -lu

---

### Post by gandalf2000 on 2008-09-15
Ok, let's see if I can post this.


bob@gandalf:~$ sudo fdisk -lu
[sudo] password for bob: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22892288

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    11627279     5813608+   b  W95 FAT32
/dev/sda2   *    11627280   113914079    51143400    7  HPFS/NTFS
/dev/sda3       113914080   114292079      189000   82  Linux swap / Solaris
/dev/sda4       114292080   156355919    21031920    5  Extended
/dev/sda5       114292143   154511279    20109568+  83  Linux
/dev/sda6       154511343   156355919      922288+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8004b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   106237844    53118891    b  W95 FAT32
/dev/sdb2       106237845   209423339    51592747+  83  Linux
/dev/sdb3       209423340   270855899    30716280   83  Linux
/dev/sdb4       270855900   488392064   108768082+  83  Linux
bob@gandalf:~$ 



I want to move it from sda5 to sdb2.  I will not do anything till I hear comments.  I know sda is a bit of a mess and it is also the original drive and the master.  If I can move Ubuntu onto sdb2 I can then clean up the master and know that Ubuntu is safe on the newer drive.  I almost never boot to Windoz anymore

---

### Post by Pumalite on 2008-09-15
Much better off saving data and doing a clen install on top of the other.
Go 'Manual' and choose the appropriate partition.

---

### Post by caljohnsmith on 2008-09-15
I think you have nothing to lose by trying Yannik's method; from the Live CD do:
```
sudo mkdir /media/sda5
sudo mkdir /media/sdb2
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sdb2 /media/sdb2
sudo cp -a /media/sda5/* /media/sdb2/.
```
Once you have it all moved over, you'll need to change the UUIDs in your Grub's menu.lst, and also the UUIDs in the /etc/fstab (and there's just a few other files you would need to change if you use your computer's "suspend" or "hibernate" features). I think you should give it a try as I know someone else who used the above strategy, and it worked perfectly for them.

If you don't want to try the above method, then certainly Pumalite's idea of doing a complete reinstall would work.

---

### Post by Yannick Le Saint kyncani on 2008-09-15
> **caljohnsmith said:**
> I think you have nothing to lose by trying Yannik's method;

Yeah, it basically just involves a file copy, nothing to be scared about.

Of course, don't screw up the partitionning/formatting steps or you're in for a world of trouble. <- be extra careful here.

As always, if in doubt, make a backup.

---

### Post by Ghliofris on 2008-09-15
I did a backup, then a clean install. After that did a restore. It's really the same thing as copying over, just the backup program dose it for you.

---

### Post by gandalf2000 on 2008-09-19
Ok, it's been interesting but I still don't have it done.  I downloaded Clonezilla Live and burned it to CD and tried to do it that way a number of times (lost count) thinking it must be something I am doing wrong and it probably is but I tried different settings and nada.  I had to reformat a few times after trying Clonezilla.  Tried the file copy and that seemed to go fine but I couldn't get it to boot, messed up grub something awful a couple of times but I managed to fix that by doing a new install of Ubuntu to the partition where I want.  Did that a few times (it's a wonder the CDROM drive hasn't quit on me) and tried something else I found on the forums that also didn't work. 

So, where I am now is back where I started but with a bootable Ubuntu on the partition where I want it.  I can boot my original Ubuntu, the new install Ubuntu or Windoz.  Think at this stage I might try to do a backup of settings and files and put them on the new install.  That won't get me the programs that are on this install but I guess it will be fun starting over (again!!!) customizing my Ubuntu.  Alright, now, how do I backup settings and files?  I'll do a search on the forums, I'm sure it has been covered a number of times.  Thanks for trying guys, sometimes I think that this computer just doesn't like me.

---

### Post by robert shearer on 2008-09-19
You could install aptoncd to your old install then use it to do a backup of your apt-cache (all your old programs) to a cd.

Then install aptoncd to your new installation and use it to restore the programs from the cd.

It is so long ago that I cannot recall if I found the 'aptoncd' program in Synaptic or downloaded it and used the deb installer.You may have to try both.

---

### Post by Pumalite on 2008-09-19
To backup and Restore (take your pick):
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by hijk867 on 2008-09-19
[&#23454;&#39564;&#20202;](http://www.golink.com.cn) &#36816;&#21160;&#20013;&#29289;&#20307;&#30340;&#21152;&#36895;&#24230;&#26159;&#30001;&#20110;[&#20256;&#24863;&#22120;&#23454;&#39564;&#20202;](http://www.golink.com.cn) &#21463;&#21040;&#37325;&#21147;&#30340;&#20316;&#29992;&#25152;&#33268;&#65292;&#22240;&#27492;&#20063;&#31216;&#20026;[&#20256;&#24863;&#22120;&#23454;&#39564;&#20202;](http://www.golink.com.cn/docc/prodmain.asp?productid=58&typenames=) &#21152;&#36895;&#24230;&#65292;&#24120;&#29992;g&#34920;&#31034;&#12290;[&#20256;&#24863;&#22120;&#23454;&#39564;&#20202;](http://www.golink.com.cn/docc/prodmain.asp?productid=32&typenames=)&#21152;&#36895;&#24230;&#30340;&#26041;&#21521;&#24635;&#26159;&#31446;&#30452;&#21521;&#19979;&#65292;&#23427;&#30340;&#25968;&#20540;&#21487;&#30001;&#23454;&#39564;&#27979;&#23450;&#12290; &#29233;&#32654;&#30340;&#22899;&#24615;&#30475;&#30475;[&#38889;&#22269;SZ&#22899;&#35013;](http://www.myshez.com),&#38750;&#24120;&#19981;&#38169;&#22114;...

---

### Post by Yannick Le Saint kyncani on 2008-09-19
> **gandalf2000 said:**
> Ok, it's been interesting but I still don't have it done.

Hi gandalf2000, ok, I'll try something very simple ( I think ). However, I have never tested it and it may not perfectly work. It should be safe though, assuming you don't do something very stupid.

Here it is :

- First install ubuntu and login.

- Open a file browser "#1" and go to /home/yourusername.

- Open the disc which contains your previous data in another file browser "#2" and go the the /media/thediscwithyourpreviousdata/home/yourusername/ which contain the files you want moved.

- In browser #2, select view -> show hidden files. That's very important as those hidden files contain your application settings.

- *Copy* everything from #2 to #1, *not* the other way around (this is where there is room to make something very stupid). Overwrite everything.

- Reboot.

- Log in, reinstall the applications you had installed.

- Reboot, that should be it.


Let me know how this works :)

---

### Post by gandalf2000 on 2008-09-25
Thanks again guys.  Yannick, I did what you wanted me to and it worked as far as getting my stuff there but now I have to download and install all the applications again.  I was hoping to avoid the bandwidth usage and then I have to set up my printer/scanner again and that I was definitely hoping to avoid.  However, it seems I have no other way to do it as I can't get it right with anything else.

Ok, just reread Robert Shearers post and I guess I don't need to download all the apps again, great.  I'll get on that today.

---

### Post by Yannick Le Saint kyncani on 2008-09-25
Yeah, I read my post again, which clone the entire system to another disk, and I forgot one step.

It involves modifying the /etc/fstab to match the new filesystem's uuids, doing the same to /boot/grub/menu.lst, setting up grub in mbr, changing root(X,Y)-related entries in grub's config, rebuild auto-generated entries with update-grub, dynamically modifying grub's entries at boot time or using chroot ... basically things that would fly way over your head unless you understand what I am saying and can change them yourself (in short, change uuids where relevant, change grub's config, reinstall grub in mbr, boot, use update-grub).

So I think reinstalling your apps and maybe apply a tweak or two again may prove simpler for you.

---

### Post by gandalf2000 on 2008-09-26
Well, I did a fresh install to the partition where I wanted it (again, how many times is that now.....) then copied from Home in the original to the new and then "aptoncd" from the original to the new.  I now have most of the original working.  Some of the apps didn't come over with "aptoncd" and will have to be installed separately and the printer/scanner (Brother) has to be set up again so, not too much of a struggle.  

Yannick, you were right.  Most of what you said in your last post went straight over the top.  By the way, I may have figured out what I was doing wrong with "partimage".  Came across a How To here [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) and it has pictures!!!  If only I had seen that awhile ago.  Ah well, not going to mess with what I have now till I know more about what I'm doing.  Once again, thanks guys.

---

### Post by davidryder on 2008-09-26
There is nothing special about moving your installation to another drive. Copy all the folders from one drive to another (preserving ownership and permissions) and edit your GRUB menu list to boot to the new drive.

---

### Post by Pumalite on 2008-09-26
Make an image of your system and store it on an external drive. Then proceed with the move.(if you have chosen to move your partition)

---

### Post by Milleman on 2008-09-26
> **Yannick Le Saint kyncani said:**
> Hi gandalf2000,
...
It involves modifying the /etc/fstab to match the new filesystem's uuids, doing the same to /boot/grub/menu.lst, setting up grub in mbr, changing root(X,Y)-related entries in grub's config... 


How do I get the UUID from an extra attached harddisk?

---

### Post by gandalf2000 on 2008-10-07
Well, I have now lost the ability to boot anything with this computer.  I couldn't do what I wanted to do even trying what everything you guys suggested so I made a clean install and set that up and moved the file I wanted.  I then installed Fedora 9 on another partition and didn't like it so installed Xubuntu over that and lost the boot.  Strange things began to happen.  Sometimes I could boot and the Xubuntu splash came up but it boot to my old Ubuntu partition. Did a reinstall and lost everything.  Then I started playing with the grub files, what a mess.  Now I can't boot into anything.  Occasionally SuperGrubDisk will get me in to my old Ubuntu like now.   Helllllp.

---

### Post by gandalf2000 on 2008-10-08
Got it.  I have been doing a lot of searching in the past few days, as you can imagine, and finally came across the answer on these forums.  Thanks go to AmericanYellow for his simple solution.  The hard disk boot order in BIOS was incorrect.  Once I corrected this I got my boot back.  Beauty, now I can go play some more.  Well, that is how we learn, isn't it.  Think I will make a dedicated boot partition, that way I will know were my boots should be. ](*,)

---

