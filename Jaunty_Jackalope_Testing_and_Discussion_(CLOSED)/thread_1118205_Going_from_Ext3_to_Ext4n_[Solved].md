---
title: "Going from Ext3 to Ext4n [Solved]"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by linuxuser21 on 2009-04-06
First of all, is there any benefit in doing it?
Second if there is, How?
I'm going to be upgrading via the Upgrade Manager when Jaunty comes out.  I've put a lot of blood, sweat and tears into this desktop so I want to keep everything, just upgraded.

---

### Post by SunnyRabbiera on 2009-04-06
Nah, if Ext3 works stick with it.
EXT4 offers no real security improvements over EXT3, and its certain that EXT3 will be around for a while.
EXT2 is still around, and its been around since 1993 and is still a valid FS...
EXT3 will be around for a while too.

---

### Post by linuxuser21 on 2009-04-06
> **SunnyRabbiera said:**
> Nah, if Ext3 works stick with it.
EXT4 offers no real security improvements over EXT3, and its certain that EXT3 will be around for a while.
EXT2 is still around, and its been around since 1993 and is still a valid FS...
EXT3 will be around for a while too.

Okay.  That's what I'll do then.  It isn't faster or anything like that then?

---

### Post by monkeyKata on 2009-04-06
> **SunnyRabbiera said:**
> Nah, if Ext3 works stick with it.
EXT4 offers no real security improvements over EXT3, and its certain that EXT3 will be around for a while.
EXT2 is still around, and its been around since 1993 and is still a valid FS...
EXT3 will be around for a while too.

Well, doesn't ext4 give a speed increase?  I haven't tried it but people posting Jaunty testimonials seem to notice it.

And could he change to ext4 by doing an update, or would he have to install fresh or partition or something?

---

### Post by linuxuser21 on 2009-04-06
> **monkeyKata said:**
> Well, doesn't ext4 give a speed increase?  I haven't tried it but people posting Jaunty testimonials seem to notice it.

And could he change to ext4 by doing an update, or would he have to install fresh or partition or something?

That's what I'm wondering.  I don't think that you can just get it by doing the update though.  After all, it is a whole filesystem.

I am not doing a fresh install... Too much work has gone into this computer.  lol.  The reason that I am interested in it is because I've heard that it's significantly faster as well.

---

### Post by monkeyKata on 2009-04-06
> **linuxuser21 said:**
> That's what I'm wondering.  I don't think that you can just get it by doing the update though.  After all, it is a whole filesystem.

I am not doing a fresh install... Too much work has gone into this computer.  lol.  The reason that I am interested in it is because I've heard that it's significantly faster as well.

yeah I'm in a similar boat.  I didn't have to go through much to get my setup working, but I have a bunch of files I can't back up at the moment and don't want to lose, though I'd like to check out ext4.

And I think you're right a new file system has got to require a fresh install/formatting/partition.

But you know speed is supposedly Jaunty's thing, maybe it's noticeable even sticking with ext3.

---

### Post by linuxuser21 on 2009-04-06
> **monkeyKata said:**
> yeah I'm in a similar boat.  I didn't have to go through much to get my setup working, but I have a bunch of files I can't back up at the moment and don't want to lose, though I'd like to check out ext4.

And I think you're right a new file system has got to require a fresh install/formatting/partition.

But you know speed is supposedly Jaunty's thing, maybe it's noticeable even sticking with ext3.

Woo! I'm excited for Jaunty to come out.  lol.  The way I'm thinking if I did want to do it is by:
1. Move everything to my friend's 1tb external hard drive
2. Make internal HDD Ext4
3. Move everything back to internal HDD

Possible?

---

### Post by whoop on 2009-04-06
I have upgraded my intrepid (running ext3) to jaunty a while ago (when it was still in alpha6 stage). I have also converted my existing ext3 FS to ext4. I just ran into one problem which was quite easy to solve.

I guess you want the info so here it is:

How to convert the file system to ext4 (in jaunty)!
Here's what I did:

Booted jaunty live-cd on a system running jaunty and ext3 (on /dev/sda1 in my case), opened a terminal:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```
In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes).

I later got into some trouble because the distribution upgrade does not seem to install the new grub stage. So I did the following to refresh grub (again from a live-cd):
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```

You can probably do both things in one session.

It's been running sweet ever since.

---

### Post by linuxuser21 on 2009-04-06
Oh wow, thanks.  That didn't just reformat it then?

---

### Post by whoop on 2009-04-06
> **linuxuser21 said:**
> Oh wow, thanks.  That didn't just reformat it then?

Nope, not sure if you are kidding :lolflag:, the entire operation just takes a few minutes and all data is preserved. It's off course always advised to make a backup.

---

### Post by linuxuser21 on 2009-04-06
No, I wasn't kidding.  Did you notice a big difference between Ext3 & Ext4 then?

---

### Post by whoop on 2009-04-06
> **linuxuser21 said:**
> Woo! I'm excited for Jaunty to come out.  lol.  The way I'm thinking if I did want to do it is by:
1. Move everything to my friend's 1tb external hard drive
2. Make internal HDD Ext4
3. Move everything back to internal HDD

Possible?

Possibly (although I think it is error prone) . You'll have to change "ext3" to "ext4" in /etc/fstab after you did that or the system will not know that the partition is running in ext4 mode. Moving all files could also be risky because of permissions. Maybe you could do it by archiving everything using tar with the p flag so you preserve permissions. You would also have to copy everything back using a live-cd or something because you will not be able to copy everything back while the partition is being run from. I could well be forgetting something crucial here although I do not think so.

---

### Post by linuxuser21 on 2009-04-06
See, that's what I was wondering.  I think I might try it the way you told me with the code.  That should prevent any of those issues shouldn't it?

---

### Post by whoop on 2009-04-06
> **linuxuser21 said:**
> No, I wasn't kidding.  Did you notice a big difference between Ext3 & Ext4 then?
That's impossible to say (in my case). My jaunty(ext4) seems faster than when I was running intrepid(ext3). I don't really think you can use that as a comparison.

What I could/should have done is do some benchmarks before the file system conversion, both in jaunty. But I didn't, sorry.
Luckily, there are always bored people around that do useful stuff:lolflag:.
Looksy here for some benchmarks:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)

---

### Post by whoop on 2009-04-06
> **linuxuser21 said:**
> See, that's what I was wondering.  I think I might try it the way you told me with the code.  That should prevent any of those issues shouldn't it?

Yep, although you still have to change "ext3" to "ext4" in fstab, but that was stated in my little tutorial.

---

### Post by linuxuser21 on 2009-04-06
> **whoop said:**
> Looksy here for some benchmarks:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)

Wow, from these statistics, I think I do want to go with Ext4.

---

### Post by linuxuser21 on 2009-04-06
> **whoop said:**
> Yep, although you still have to change "ext3" to "ext4" in fstab, but that was stated in my little tutorial.

Basically, all that entails is just changing every "Ext3" to "Ext4" then?

---

### Post by whoop on 2009-04-06
> **linuxuser21 said:**
> Basically, all that entails is just changing every "Ext3" to "Ext4" then?

Well only for the partitions you actually convert.

---

### Post by linuxuser21 on 2009-04-06
> **whoop said:**
> Well only for the partitions you actually convert.

Well, that would be the whole thing then (except for Swap).

---

### Post by whoop on 2009-04-06
> **linuxuser21 said:**
> Well, that would be the whole thing then (except for Swap).
If you don't have a separate user or boot partition then, yes. swap you leave as is off course.

---

### Post by linuxuser21 on 2009-04-06
> **whoop said:**
> If you don't have a separate user or boot partition then, yes. swap you leave as is off course.

Nope, just Ubuntu on my system.

---

### Post by michaeljanssen on 2009-04-07
> **whoop said:**
> I have upgraded my intrepid (running ext3) to jaunty a while ago (when it was still in alpha6 stage). I have also converted my existing ext3 FS to ext4. I just ran into one problem which was quite easy to solve.

I guess you want the info so here it is:

How to convert the file system to ext4 (in jaunty)!
Here's what I did:

Booted jaunty live-cd on a system running jaunty and ext3 (on /dev/sda1 in my case), opened a terminal:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```
In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes).

I later got into some trouble because the distribution upgrade does not seem to install the new grub stage. So I did the following to refresh grub (again from a live-cd):
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```

You can probably do both things in one session.

It's been running sweet ever since.

oh my...i am having a total brainfart...i am currently at the fstab stage...and i cant figure out how to save the changes...

---

### Post by michaeljanssen on 2009-04-07
lol...nm...brainfart ended...:lolflag:

---

### Post by linuxuser21 on 2009-04-07
It work for you then?

---

### Post by teseglet on 2009-04-07
I followed the instructions above and... wow!  I have one of those $199 Everex specials from several years ago with a 1.5Mhz processor so my system has always seemed a bit remedial (although I have upgraded the video card, RAM and power supply)... a bit slow to boot, a bit slow to launch programs, slight stutters on Rhythmbox songs when launching other apps, etc...  Jaunty with EXT3 helped a quite a bit on performance vs. Intrepid but the EXT4 upgrade I just did makes my system as quick, smooth and polished as my wifes Windows system with twice the processor. Obviously I'm balancing the risk of these purported system crash/data loss episodes with EXT4 but based on the results I've experienced so far I'm glad I took the plunge.  I have rebooted 5 times just to savor the speed.  It really feels like I've upgraded my hardware.  All the prior issues I mention above are GONE!  So far, so good.

---

### Post by linuxuser21 on 2009-04-07
Oh wow, I think I'm just going to do it and quit being so scared about loosing stuff.

---

### Post by Lord_Phoenix_Rus on 2009-04-08
Hello all,
I've updated today my Ubuntu 8.10 to 9.04 using "update-manager -d" command it went well, I've installed all updates before upgrading OS. After process completed I've loaded successfully, installed update for Wine, worked for half an hour, restarted again and then converted FS to ext4 by editing fstab file. Restarted successfully and worked for another hour. After next reboot I started getting this message during load:

Boot from (hd0,0) ext4
Error 24: Attempt to access block outside partition
Press any key to continue...

What happened and anyway I can fix it? Any help is appreciated. Thanks in advance.

---

### Post by whoop on 2009-04-08
> **michaeljanssen said:**
> oh my...i am having a total brainfart...i am currently at the fstab stage...and i cant figure out how to save the changes...

If you opened fstab with nano hit Ctrl+x, then hit "y", then hit Enter (after making the desired changes). If you can't figure that out you can also open fstab with:
```

gksudo gedit /mnt/etc/fstab

```
instead of
```

nano /mnt/etc/fstab

```

---

### Post by whoop on 2009-04-08
> **Lord_Phoenix_Rus said:**
> Hello all,
I've updated today my Ubuntu 8.10 to 9.04 using "update-manager -d" command it went well, I've installed all updates before upgrading OS. After process completed I've loaded successfully, installed update for Wine, worked for half an hour, restarted again and then converted FS to ext4 by editing fstab file. Restarted successfully and worked for another hour. After next reboot I started getting this message during load:

Boot from (hd0,0) ext4
Error 24: Attempt to access block outside partition
Press any key to continue...

What happened and anyway I can fix it? Any help is appreciated. Thanks in advance.

Did you try to convert your file system by only changing "ext3" to "ext4" in fstab? If that is the case you forgot a few steps.
My previous post:[http://ubuntuforums.org/showpost.php?p=7026195&postcount=8](http://ubuntuforums.org/showpost.php?p=7026195&postcount=8) contains all the steps I took to convert my file system to ext4.
If you do think you did it correctly it could be that you made a mistake with updating grub; maybe you forgot the last step:
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```
I have read in another post that someone got the same grub error number and fixed it the same way: [http://ubuntuforums.org/showpost.php?p=6977150&postcount=1](http://ubuntuforums.org/showpost.php?p=6977150&postcount=1)
The only difference is that he chrooted and I used mount.

---

### Post by GARoss on 2009-04-11
> **whoop said:**
> I have upgraded my intrepid (running ext3) to jaunty a while ago (when it was still in alpha6 stage). I have also converted my existing ext3 FS to ext4. I just ran into one problem which was quite easy to solve.

I guess you want the info so here it is:

How to convert the file system to ext4 (in jaunty)!
Here's what I did:

Booted jaunty live-cd on a system running jaunty and ext3 (on /dev/sda1 in my case), opened a terminal:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```
In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes).

I later got into some trouble because the distribution upgrade does not seem to install the new grub stage. So I did the following to refresh grub (again from a live-cd):
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```

You can probably do both things in one session.

It's been running sweet ever since.


Quote:
Originally Posted by michaeljanssen View Post
oh my...i am having a total brainfart...i am currently at the fstab stage...and i cant figure out how to save the changes...
If you opened fstab with nano hit Ctrl+x, then hit "y", then hit Enter (after making the desired changes). If you can't figure that out you can also open fstab with:
Code:

gksudo gedit /mnt/etc/fstab

instead of
Code:

nano /mnt/etc/fstab

I had my share of brainfarts, too, until I used **gksudo gedit /mnt/etc/fstab**.:lolflag: I'm getting up there in years & this added quite a few grey hairs to my already grey head! But, success!:guitar:
Thanks

---

### Post by linuxuser21 on 2009-04-12
I got everything done except for changing Ext3 to Ext4 in fstab.  When I open it, it is just blank.  P.S. I am using Gedit.  If you prefer me to use Nano, please just guide me through it.

---

### Post by linuxuser21 on 2009-04-12
Never mind, I realized that the live CD that I'm using (7.10.  It's the only one that I have that will detect my hard drives) cannot read it if it is in Ext4.

---

### Post by linuxuser21 on 2009-04-12
Okay, I need to know how to change it back to Ext3.  Apparently I did it to one of my other hard drives.  I got this message:

---

### Post by zika on 2009-04-13
> **GARoss said:**
> I had my share of brainfarts, too, until I used **gksudo gedit /mnt/etc/fstab**.:lolflag: I'm getting up there in years & this added quite a few grey hairs to my already grey head! But, success!:guitar:
Thanks

gksu gedit /etc/fstab ... ;)

---

### Post by whoop on 2009-04-13
> **linuxuser21 said:**
> Never mind, I realized that the live CD that I'm using (7.10.  It's the only one that I have that will detect my hard drives) cannot read it if it is in Ext4.
Try mounting it in ext3 mode.

---

### Post by whoop on 2009-04-13
> **linuxuser21 said:**
> Okay, I need to know how to change it back to Ext3.  Apparently I did it to one of my other hard drives.  I got this message:
Which version of ubuntu are you using? jaunty should be able to read ext4 file system by default.

---

### Post by linuxuser21 on 2009-04-13
> **whoop said:**
> Try mounting it in ext3 mode.

That's what I did.  In the end I had to change it back though.

---

### Post by linuxuser21 on 2009-04-13
> **whoop said:**
> Which version of ubuntu are you using? jaunty should be able to read ext4 file system by default.

8.10.  I know now it can't read Ex4, that's why I had to change it back.

---

### Post by linuxuser21 on 2009-04-13
This is what I did to change it back to Ext3; but it still gives me that message:
```
sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext3 /dev/sda1 /mnt
gksudo gedit /mnt/etc/fstab
```

---

### Post by whoop on 2009-04-13
> **linuxuser21 said:**
> This is what I did to change it back to Ext3; but it still gives me that message:
```
sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext3 /dev/sda1 /mnt
gksudo gedit /mnt/etc/fstab
```
Did you change it back to ext3 in fstab?

---

### Post by whoop on 2009-04-13
> **linuxuser21 said:**
> 8.10.  I know now it can't read Ex4, that's why I had to change it back.

You could off course upgrade to 9.04, you will probably be able to read it then.

---

### Post by linuxuser21 on 2009-04-13
> **whoop said:**
> Did you change it back to ext3 in fstab?

Yes I did.  I still got this error though.

---

### Post by linuxuser21 on 2009-04-13
> **whoop said:**
> You could off course upgrade to 9.04, you will probably be able to read it then.

Yeah, I think I'm going to download the 9.04 live CD and change it back and/or get the information I need from the hard drive.

---

### Post by vaskark on 2009-04-19
> **whoop said:**
> I have upgraded my intrepid (running ext3) to jaunty a while ago (when it was still in alpha6 stage). I have also converted my existing ext3 FS to ext4. I just ran into one problem which was quite easy to solve.

I guess you want the info so here it is:

How to convert the file system to ext4 (in jaunty)!
Here's what I did:

Booted jaunty live-cd on a system running jaunty and ext3 (on /dev/sda1 in my case), opened a terminal:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes).

I later got into some trouble because the distribution upgrade does not seem to install the new grub stage. So I did the following to refresh grub (again from a live-cd):
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```You can probably do both things in one session.

It's been running sweet ever since.

I took this advice and tried to convert my ubuntu jaunty partition (sda2) to ext4. I ran into some problems though:

root@ubuntu:~$ mount -t ext4 /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Now it says that the partition I'm trying to convert is an unknown type (in Partition Editor, that is).

Can someone offer any advice? Thanks. I guess I'm stuck on the live cd for now :)

Edit: I got impatient and just reformatted. Holy is it ever fast!

---

### Post by skillllllz on 2009-04-21
***UPDATE****
Never mind folks. I had a typo in the mount options and it was causing the error. Whoops!

[COLOR=SlateGray]
> **vaskark said:**
> I took this advice and tried to convert my ubuntu jaunty partition (sda2) to ext4. I ran into some problems though:

root@ubuntu:~$ mount -t ext4 /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm getting the same error. I followed the instructions in this thread exactly. Please help.[/COLOR]

---

