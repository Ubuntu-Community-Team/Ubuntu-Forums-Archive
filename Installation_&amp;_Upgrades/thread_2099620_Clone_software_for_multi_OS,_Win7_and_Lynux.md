---
title: "Clone software for multi OS, Win7 and Lynux"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by starstreams on 2012-12-30
I have an SSD hard drive with two partitions, one running Win7 and Lubuntu on the other side. Both operating systems are running great under this laptop. Is there any thing (even if I need to buy it) that can clone an entire drive, along with all the boot loaders but that also supports SSD hard drives? The windows 7 image clone sucks. I'm looking for something that will create a start up disk, format the way I left the system ..ect and restore it back to the exact state I cloned it as. The biggest issues with most of the clone software I've seen is lack of support for SSD hardware and none windows boot loaders.

---

### Post by alenis on 2012-12-30
Clonezilla should do everything you need.

---

### Post by starstreams on 2012-12-30
Hi alenis
Would **dd** handle SSD drives as well as Clonezilla? It seems less involved, and I think the low level approach would capture an identical image of all partitions. But I've never used either to compare. I had been reading about dd just a wile ago before I read your post, It seems simple, but no mention about SSD drives.
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

Edit, I just found some videos on Clonezilla, this should help!
Thanks for mentioning the software

---

### Post by starstreams on 2012-12-30
Sorry to bump this, but I'm getting the same errors as about 100 other people and don't know enough to make heads or tails out of any of the recommendations.
Note: this is a new install of Lubunu, and Windows7 only one day old.

I tried the Debian based CloneZilla as well as the Ubuntu Clone Live CD's and both give the same Modprob error.

[COLOR=#ff0000]modprobe module crc32c not found in module.dep
[/COLOR][COLOR=#ff0000]Partclone bitmap error Syntex 1
[/COLOR]
So I ran CloneZilla a second time, this time choose the 2nd option     to _check file system for errors and fix interactively_. Now, according to the verify test, all partitions, (that includes NTFS and EXT4) were successful and are restorable. ..according to the CloneZilla wizard.

But should I be concerned about the Modprobe error? or could that have been fixed by the file system check? I don't understand what this means with reguard to CloneZilla

**EDIT:**
I tried running CloneZilla on an only Windows machine today and I still get the modprobe error above.

---

### Post by Mark Phelps on 2012-12-31
I recently cloned all the partitions on my SSD to a larger SSD -- and used Macrium Reflect (Windows app) to do that.  So, I know it can handle SSDs.

---

### Post by The Spectre on 2012-12-31
Give this one a try...

Redo Backup & Recovery
[http://redobackup.org](http://redobackup.org)

---

### Post by starstreams on 2012-12-31
Thanks guys, do they do multiple mixed partitions? I didn't see any mention of that on their features page. Like if you have an NTFS partition and another with EXT4?

I'd still like to know what these CloneZilla errors means though. It looks like a lot of people recommend CloneZills so I'm wondering if I should stick with that. Again, the new issue I face now is whether or not I can just ignore these modprobe errors "even though the image tested successfully". 

Seeing that I get the error even when I run CloneZilla on an (all windows machine) indicates that it's looking for something and not finding it. The error is understandable with regard to the fact that the live CD wouldn't find a Modprobe directory on a windows machine since the CD(s) "were" built from Debian/Ubuntu. But even when I ran CloneZilla on my Linux / Win7 machine I still got the error. Something is not right. And why does it even care about configuration directory's if it's job is to clone a drive sector by sector at the hardware level. This makes no sense to me?

Anyone please?

---

### Post by orb9220 on 2013-01-01
Like mentioned Redo Backup uses same engine as Clonezilla just less advanced features and less confusing to use. Was really easy to use.

Backed up a triple boot Win7,Winxp, & Linux Mint 14 Cinnamon a few days ago and pointed it to an external usb drive folder. Took about 40 mins.

Today had to do a complete restore. And did a complete restored of all 4 partitions. 2 nfts and 2 ext4 in 20 mins.

Glad I did get around downloading the 250mb iso and burn to CD. Just boot with it. Also has many extra tools and even internet connect to downloaded needs if warranted.
.

---

### Post by sudodus on 2013-01-01
> **starstreams said:**
> Thanks guys, do they do multiple mixed partitions? I didn't see any mention of that on their features page. Like if you have an NTFS partition and another with EXT4?

I'd still like to know what these CloneZilla errors means though. It looks like a lot of people recommend CloneZills so I'm wondering if I should stick with that. Again, the new issue I face now is whether or not I can just ignore these modprobe errors "even though the image tested successfully". 

Seeing that I get the error even when I run CloneZilla on an (all windows machine) indicates that it's looking for something and not finding it. The error is understandable with regard to the fact that the live CD wouldn't find a Modprobe directory on a windows machine since the CD(s) "were" built from Debian/Ubuntu. But even when I ran CloneZilla on my Linux / Win7 machine I still got the error. Something is not right. And why does it even care about configuration directory's if it's job is to clone a drive sector by sector at the hardware level. This makes no sense to me?

Anyone please?

I use Clonezilla and I'm happy with it. I prefer the stable releases (not the ubuntu-version named ones). I have also found that on SSD drives, it is often necessary to check and repair the file system (I think Clonezilla uses e2fsck on linux ext file systems)

Don't worry so much about that modprobe error. The important information is, that all partitions should be successfully cloned/imaged and restorable.

If you cloned the drive, test the clone: connect it and boot from it. Check that several important things work as they should!

And if you made an image: Get a drive of at least the same size as the original one and restore the file system from the image to that new hard drive, connect it and boot from it. Check that several important things work as they should.

---

### Post by sudodus on 2013-01-01
> **starstreams said:**
> Hi alenis
Would **dd** handle SSD drives as well as Clonezilla? It seems less involved, and I think the low level approach would capture an identical image of all partitions. But I've never used either to compare. I had been reading about dd just a wile ago before I read your post, It seems simple, but no mention about SSD drives.
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

Edit, I just found some videos on Clonezilla, this should help!
Thanks for mentioning the software
dd certainly works on SSD drives, USB pendrives etc as well as on HDDs and CD-roms. But it is nick-named 'disk destroyer' because it does what you tell it to do without asking nasty questions. It won't guess that you actually wanted to do something else. And it clones everyting on the drive. You can compress an image piping the dd output via gzip.

Clonezilla asks twice. And it is smart enough to read only the parts of the drive, where there are files, and skip empty parts, which makes it faster. When making an image, Clonezilla will compress the data.

---

### Post by starstreams on 2013-01-01
Thanks for all the input and great advice everyone!
[COLOR=Blue]*sudodus*[/COLOR], [COLOR=Blue]*orb9220*[/COLOR], [COLOR=Blue]*The Spectre*[/COLOR], [COLOR=Blue]*Mark Phelps*[/COLOR], [COLOR=Blue]*alenis*[/COLOR] ..and anyone I missed!

I had found this video which really helped for CloneZilla:
*note: I watched it on my Win machine since Adobe decided to drop flash support for Linux and I haven't found a good alternative plug in for Firefox and Chrome sucks*.
```
https://www.youtube.com/watch?v=490n_VoldUg
```
Redo Backup sounds interesting also for something quick, something I can also send to family and friends who won't get as involved as I will. This was a good comparison. It looks like it does the job too. 
```
http://blog.gambliser.com/2012/01/redo-backup-and-clonezilla-direct-comparison/
```

Either way, I've got plenty of hard drive space to keep backups from all of them.
Again, Thanks for all the support confirming all the choices out there!

---

### Post by sudodus on 2013-01-01
> **starstreams said:**
> Thanks for all the input and great advice everyone!
[COLOR=Blue]*sudodus*[/COLOR], [COLOR=Blue]*orb9220*[/COLOR], [COLOR=Blue]*The Spectre*[/COLOR], [COLOR=Blue]*Mark Phelps*[/COLOR], [COLOR=Blue]*alenis*[/COLOR] ..and anyone I missed!

I had found this video which really helped for CloneZilla:
*note: I watched it on my Win machine since Adobe decided to drop flash support for Linux and I haven't found a good alternative plug in for Firefox and Chrome sucks*.
```
https://www.youtube.com/watch?v=490n_VoldUg
```
Redo Backup sounds interesting also for something quick, something I can also send to family and friends who won't get as involved as I will. This was a good comparison. It looks like it does the job too. 
```
http://blog.gambliser.com/2012/01/redo-backup-and-clonezilla-direct-comparison/
```

Either way, I've got plenty of hard drive space to keep backups from all of them.
Again, Thanks for all the support confirming all the choices out there!
You are welcome :-)

Try to install flashplayer with flashplugin-installer
```
sudo apt-get install flashplugin-installer
```

Edit: Read more about it and install using Synaptic

---

### Post by starstreams on 2013-01-08
Thanks for the flash tip sudodus!

By the way, I tried both CloneZilla, and Redo. 
Both images tested fine. And although I have not tried running a restore test on Clonezill (which I'm sure will work) I did restore my entire system the other day with Redo. It worked like a charm. This computer had Win7-NTFS and Linux- EXT4 partitions. Everything seemed to restore as It was left. 

Now that I now the restore works, I'm going to start breaking things..haha :p

---

