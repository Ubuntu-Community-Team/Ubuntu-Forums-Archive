---
title: "[SOLVED] dual boot 2 harddrives 2 linux distros"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by jtravnick on 2008-01-01
First off I would like to say so far I really like what I'm seeing with ubuntu 7.10. I'm coming over from Fedora. I wont go into what problems I'm having over there as thats for Fedoras forum. I will say I tried a couple of other distros (Mepis,Debian) was not impressed at all with them. Had all kinds of different problems with them. Almost didn't try ubuntu at all but am glad I did.

So far everything has worked out of the box. Loved the fact ubuntu saw my nvidia card at first boot and asked if i wanted to install the drivers for it.

So heres where I'm at right now I have two harddrives first one has ubuntu installed and loading. the second harddrive has Fedora 8. Right now if I want to go from one to the other I have to enter the bios and switch what harddrive to boot.. I know there is a way to get grub to do this just havnt done a dual boot since Fedora 6 and that was with windows. 

As far as I know grub for ubuntu is on the MBR of the first harddrive I thought all I would have to do is put something in menu.lst to point to the second harddrive to get it to boot that one but I cant seam to get it right. One of the things thats killing me is all I can seam to find is how to dual boot with windows even the books I have here all they cover is with windows.

Don't know if you need this but here is my fdisk from ubuntu:
jim@jim-desktop:~$ sudo fdisk -l
[sudo] password for jim:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e09c8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d899d89

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          25      200781   83  Linux
/dev/hdb2              26       14593   117017460   8e  Linux LVM
jim@jim-desktop:~$ 

As you can see Fedora is using LVM I don't believe ubuntu is but I have been known to be wrong before expecaly when it comes to linux.

Thanks for your time
Jim

---

### Post by logos34 on 2008-01-01
I'd use the [configfile format]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").  So add an entry for Fedora to ubuntu's menu.lst:
> 
title        Fedora
configfile   (hd1,0)/boot/grub/grub.cfg

(Or '.../boot/grub/menu.lst' if that's what Fedora uses now)

add:
to mount fedora partition in ubuntu, see [this]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by jtravnick on 2008-01-01
ok tried using both grub.conf and menu.lst as both are in Fedoras grub folder both times I get:
**error 15 File not Found**

So even though I can find grub when I'm in Fedora I'm assuming its not where I'm telling ubuntu's grub.

Will work on this more tomorrow been a long day for me.

Dont know if this matters but originally the first harddrive had Fedora7 than installed Fedora8 on the second harddrive when I did the install of 8 I did not unplug the drive that had 7 witch now has ubuntu on it instead of 7 come to think of it I didn't unplug the second harddrive when I installed ubuntu.

---

### Post by logos34 on 2008-01-01
> **jtravnick said:**
> Dont know if this matters but originally the first harddrive had Fedora7 than installed Fedora8 on the second harddrive when I did the install of 8 I did not unplug the drive that had 7 witch now has ubuntu on it instead of 7 come to think of it I didn't unplug the second harddrive when I installed ubuntu.

You're gonna have to run that by me one more time.

Is the path correct?  Perhaps it's /grub/grub.conf or /grub/menu.lst instead? (on the other hand you've no doubt checked this)

---

### Post by rsambuca on 2008-01-01
If you are on Ubuntu right now, you can just mount your fedora drive and look in the /boot directory to see the name of the file to put in your ubuntu menu.lst file.

---

### Post by jtravnick on 2008-01-01
OK the path is /boot/grub/grub.conf at least thats what I type when pulling it up in gedit.

Originally I was trying to get a game to run in Fedora8 well after one of there updates the game stopped working so messed around and really messed the system up. So figured hey I got a spare harddrive put it in made it the first harddrive than did a fresh install of Fedora7 than one what is now the second harddrive did a fresh install of Fedora8. Well could not get the game to work on ether system thats when I started looking around at other distros after messing with a couple and just didn't like how they where. Came to ubuntu liked what I saw, plus the game that started all this works :)

So anyways when I did the install of Fedora8 I left the harddrive witch had 7 on it plugged in also when I installed the other distros I never unplugged the drive with 8 on it. 

So as of right now I have ubuntu on harddrive one and Fedora8 on harddrive two. If I go into the bios and tell it to boot harddrive two Fedora boots fine. Go back in and tell it to boot drive one and ubuntu boots.

Hope I covered everything as of right now all I need is to just be able to make my choice in grub and I will be a happy camper.

---

### Post by rsambuca on 2008-01-02
> **jtravnick said:**
> OK the path is /boot/grub/grub.conf at least thats what I type when pulling it up in gedit.

Originally I was trying to get a game to run in Fedora8 well after one of there updates the game stopped working so messed around and really messed the system up. So figured hey I got a spare harddrive put it in made it the first harddrive than did a fresh install of Fedora7 than one what is now the second harddrive did a fresh install of Fedora8. Well could not get the game to work on ether system thats when I started looking around at other distros after messing with a couple and just didn't like how they where. Came to ubuntu liked what I saw, plus the game that started all this works :)

So anyways when I did the install of Fedora8 I left the harddrive witch had 7 on it plugged in also when I installed the other distros I never unplugged the drive with 8 on it. 

So as of right now I have ubuntu on harddrive one and Fedora8 on harddrive two. If I go into the bios and tell it to boot harddrive two Fedora boots fine. Go back in and tell it to boot drive one and ubuntu boots.

Hope I covered everything as of right now all I need is to just be able to make my choice in grub and I will be a happy camper.

Since Ubuntu's grub menu is controlling things, you should just be able to add this to your menu.lst to add Fedora:

```
gksudo gedit /boot/grub/menu.lst
```
```
title  Fedora
root  (hd1,0)
chainloader +1
```

If that doesn't work, then you can either try the configfile command that logos gave you, or put in the specific kernel lines.  Let us know how this goes.

---

### Post by jtravnick on 2008-01-02
ok here is what I'm getting with the following commands:

 title Fedora
configfile (hd1,0)/boot/grub/grub.cfg

 title Fedora
configfile (hd1,0)/boot/grub/grub.conf

 title Fedora
configfile (hd1,0)/boot/grub/menu.lst

title Fedora
root (hd1,0)
kernel /boot/vmlinuz ro root=/dev/hdb1 quiet 

I get **ERROR 15 File not Found**


With the following command:

title  Fedora
root  (hd1,0)
chainloader +1

I get **ERROR 13 Invalid or Unsupported Executable Format**

---

### Post by rsambuca on 2008-01-02
Can you list the files that are on your Fedora /boot partition?

---

### Post by jtravnick on 2008-01-02
Ok now I'm assuming that when I am in CLI and I do cd /boot that is taking me to my boot partition. here is what I get:

[root@localhost boot]# ls
config-2.6.23.1-42.fc8      memtest86+-1.70
config-2.6.23.9-85.fc8      System.map-2.6.23.1-42.fc8
grub                        System.map-2.6.23.9-85.fc8
initrd-2.6.23.1-42.fc8.img  vmlinuz-2.6.23.1-42.fc8
initrd-2.6.23.9-85.fc8.img  vmlinuz-2.6.23.9-85.fc8
lost+found
[root@localhost boot]# 

grub and lost+found are folders this is what is in the grub folder:

[root@localhost boot]# cd /boot/grub
[root@localhost grub]# ls
device.map     grub.conf~        reiserfs_stage1_5  vstafs_stage1_5
e2fs_stage1_5  iso9660_stage1_5  splash.xpm.gz      xfs_stage1_5
fat_stage1_5   jfs_stage1_5      stage1
ffs_stage1_5   menu.lst          stage2
grub.conf      minix_stage1_5    ufs2_stage1_5
[root@localhost grub]# 

I had to boot to Fedora to get this as right now not to sure about trying mounting it from ubuntu. Figure work on one problem at a time.

Jim

---

### Post by rsambuca on 2008-01-02
Just copy the entry for Fedora from the grub.conf file into your Ubuntu grub menu.lst.  Can you try and mount the Fedora drives from ubuntu?  The reason I wanted to see that is so we know exactly what is on each partition hdb1 and hdb2.

---

### Post by jtravnick on 2008-01-02
ok will work on getting it mounted will come in handy anyway since thats where all my music is.

---

### Post by rsambuca on 2008-01-03
> **jtravnick said:**
> ok will work on getting it mounted will come in handy anyway since thats where all my music is.

It shouldn't be that difficult.  Just create a directory to mount it to, and then mount it.

1.  sudo mkdir /Fedora1
2.  sudo mkdir /Fedora2
3.  mount /dev/hdb1 /Fedora1
4.  mount /dev/hdb2 /Fedora2

I am not sure if the LVM hdb2 will work, but it would help to see what is on /dev/hdb1

---

### Post by jtravnick on 2008-01-03
Allrighty got it working. After following the walk through link for mounting the other harddrive given early on in this thread. I than pulled up the grub.conf from Fedora and copy and pasted it into ubuntu's menu.lst. At first it did not work again gave me the Error 15 than this morning I took a look at it again and noticed this line:

root		 (hd0,0)

Changed it to read:

root		 (hd1,0)

And all is well. Though after booting to Fedora than restarting the system I did notice something odd when it started loading ubuntu it said something about hd1 booting 26 times without being checked and it was going to check it. Not really sure what it said as I'm not totally awake yet. Once it finished this it than went on and booted up. Also this boot is the first time I've see it run down the list of what it was doing like mounting file system, starting my video card things like that. Is this normal with ubuntu? I'm not a total noob to linux been using fedora since 5 but fedora is the only distro I've used up till now.

As for the mounting of the LVM dont look like thats going to happen but I can work on it at a latter date and can start a new thread on it  but just so as not to leave it hanging here this is what I get when trying to mount it:

jim@jim-desktop:~$ sudo mount /dev/hdb2 /Fedora2
mount: unknown filesystem type 'LVM2_member'
jim@jim-desktop:~$ 

Thanks for the help Now just have one simple questen I noticed here threads can be maked as fixed how does one do that or does the admin do it?

Jim

---

### Post by rsambuca on 2008-01-03
Glad you got it working.  Just a couple of quick notes for you:  You will probably have to update the grub menu.lst the next time that Fedora does a kernel update, because that won't be done automatically.  Also, the fsck is done automatically every 20 - 30 boots.  You can mark the thread as solved from the "Tread Tools" Section.

---

### Post by logos34 on 2008-01-03
> **jtravnick said:**
> gave me the Error 15 than this morning I took a look at it again and noticed this line:

root		 (hd0,0)

Changed it to read:

root		 (hd1,0)

And all is well.

Ah, so that's why it wouldn't chainload from ubuntu grub....I'll have to remember that.  (although that should have occurred to me).

Good work, rsambuca! Glad it's working for you now, jtravnick.  Enjoy 'bun2

---

