---
title: "[SOLVED] Install Jaunty Jackalope on Asus EEE pc......?"
date: 2008-12-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Csongi on 2008-12-31
Does anyone have any ideas how could i install without a  cd rom drive, a  Jaunty Jackalope 9.xxxx Alpha 2 realase operating system on an Asus eee pc.....????? 





While i trying to do with unetbootin its stuck booting up from the flesh drive........




Thanks for any helps:






Csongor Ballay

---

### Post by HotShotDJ on 2008-12-31
> **Csongi said:**
> While i trying to do with unetbootin its stuck booting up from the flesh drive.I have no CLUE what this sentence means.  In any case, Jaunty is a DEVELOPMENT version of Ubuntu and is only recommended for people who know what they are doing and can tolerate frequent bugs and breakage.  I strongly recommend that you try either Hardy (8.04-LTS) or Intrepid (8.10).

---

### Post by Paqman on 2008-12-31
> **HotShotDJ said:**
> I have no CLUE what this sentence means.  

He's using [Unetbootin]("http://lubi.sourceforge.net/unetbootin.html") to create a bootable LiveUSB on a flash drive.

There are highly likely to be bugs of this kind in an alpha release. Try the [Jaunty forum]("http://ubuntuforums.org/forumdisplay.php?f=352") rather than Absolute Beginners, as we really don't support Jaunty installs here.

Installing the latest version of [Ubuntu Eee]("http://www.ubuntu-eee.com/") should give you a very up-to-date system, as it's only a couple of months old.

---

### Post by kansasnoob on 2008-12-31
Holy cow, it's Alpha 2!

Just beginning to take form!

---

### Post by kansasnoob on 2008-12-31
BTW, my point is that no one should be asking questions here about this:

[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

I'm going to ask that this be moved to:

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by HotShotDJ on 2008-12-31
> **Paqman said:**
> He's using [Unetbootin]("http://lubi.sourceforge.net/unetbootin.html") to create a bootable LiveUSB on a flash drive.Ah-HA!  Thank you for the explanation.  Now that I know what the OP was talking about, I still stand by my original recommendation... use one of the released versions of Ubuntu rather than a development version.

---

### Post by Slug71 on 2008-12-31
> **Csongi said:**
> Does anyone have any ideas how could i install without a  cd rom drive, a  Jaunty Jackalope 9.xxxx Alpha 2 realase operating system on an Asus eee pc.....????? 





While i trying to do with unetbootin its stuck booting up from the flesh drive........




Thanks for any helps:






Csongor Ballay

Agreed, you shouldnt be using Jaunty. Jaunty is in Development and is NOT recommended yet unless you have some idea what to do when things break.

I too recommend 8.04 or 8.10.

---

### Post by ronacc on 2008-12-31
or else use onr of the versions made specificly for the EEE . Ubuntu-eee works very well on my eee 4g .
[http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)

---

### Post by Csongi on 2008-12-31
I'm looking for someone who is already successfully installed without a Cd drive.......




Really looking for a step-by step guide......here......








Thanks:




Csongor Ballay

---

### Post by autocrosser on 2008-12-31
And if you really want to go forward with your install---please search the forums first. You will most likely find the information you are looking for with a little work.

---

### Post by jerrylamos on 2009-01-02
> **Csongi said:**
> Does anyone have any ideas how could i install without a  cd rom drive, a  Jaunty Jackalope 9.xxxx Alpha 2 realase operating system on an Asus eee pc.....????
Csongor Ballay

I have no idea what an Asus eee pc is, however many Ubuntu releases can be installed on regular pc's by putting the .iso onto a 1 gb hard drive partition and booting from that, see 
[http://ubuntuforums.org/showthread.php?t=1024328](http://ubuntuforums.org/showthread.php?t=1024328)

Jerry

---

### Post by ronacc on 2009-01-02
@jerrylamos  the eeepc is a netbook (very small compact laptop) it has no cd/dvd drive ,you have to use an external one if you have one, also most have no hard drive only an SSD which could be as small as 2gb it does have 3 usb ports and an sdhc card slot and will boot from those .The eeepc was the first netbook the one that started the netbook craze .

---

### Post by thor2002ro on 2009-01-03
u need to format the usb drive to fat32 to work had the same problem with my Aspire one

---

### Post by chris062689 on 2009-01-03
You people make it too hard sometimes, just use unetbootin!

---

### Post by ronacc on 2009-01-03
chris he tried unetbootin , read the first post this thread . also unetbootin wouldn't work from jaunty earlier, wrong lib version of something I forget what ,I just used my hardy box.

---

### Post by Gina on 2009-01-03
Yes, I've haad problems with unetbootin with Jaunty too.

---

### Post by jerrylamos on 2009-01-03
Jaunty doing fine with jaunty Daily Live Ubuntu, Kubuntu running from 1 gb partitions like they were CD's.  (Xubuntu Jaunty I've never been able to get a desktop running whether it's from CD, USB, or 1 gb partition).

I think you could squeak by with 750 mb partition if you're tight on space.

Make a 1 gb partition.  If gparted isn't installed on your jaunty, then Synaptic or sudo apt-get install gparted.  Achtung!  Use test system and backup anything you want, futzing around with gparted can trash a hard drive instantly!

Use gparted to create a 1 gb partition from resizing or whatever:

sudo gparted
select 1 gb partition
# Achtung!  Note what partition it is, in this case sda10
format ext3
apply
quit

I use rsync to get the latest Daily Build, for example make an executable file:

#filename rsyn or whatever you use
rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/daily-live/current/jaunty-desktop-i386.iso .
rsync -Lvv --progress rsync://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS .
md5sum jaunty-desktop-i386.iso >> MD5SUMS
less MD5SUMS
#

then sudo chmod 777 rsyn

Create CD image on the 1 gb partition, I use an executable file in the same directory as the rsyn:  

# filename LivePartition10 hda(0,9) note these must match gparted
mkdir /tmp/install_cd
sudo mount jaunty-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
#Achtung!  Dangerous - which sda?
sudo mount /dev/sda10 /mnt/installer
sudo cp -r /tmp/install_cd/* /mnt/installer
sudo cp -r /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd
#

of course sudo chmod 777 LivePartition10 or whatever filename you used.

Now update menu.lst to enable booting the CD image:
sudo gedit /boot/grub/menu.lst.  I copy the following file into menu.lst just after the "...Automagic..." line.

#name Livesda10 or whatever you choose, (hd0,9) to match sda10 
title           jaunty Live
root            (hd0,9)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw quiet splash 
initrd          /casper/initrd.gz

title           jaunty Live recovery
root            (hd0,9)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw single 
initrd          /casper/initrd.gz
#

If you don't have a large memory, for example if you have 512 mb, then use ramdisk_size 384000.  It could be smaller I think if you want to play around.  I don't know much about root=/dev/ram.

Enjoy....I've found it pretty quick to do rsyn most days to get the latest daily build, then LivePartition10 to copy it to the CD image on the 1 gb partition.  The exec complains it can't create the directories since they exist already, then goes right on to finish the copy.  Reboot and find out that my launchpad bugs still aren't fixed: 310982 312332

Jerry

---

### Post by ronacc on 2009-01-03
neat idea jerry I'll give it a try .

---

### Post by Csongi on 2009-01-05
Thanks for the accurate description #17..... 





I don't have enough space to copy the jauntuxxxx.iso to the /mnt/installer.......



Do you have any ideas to do while the iso is stays on the  
flash drive?





Thanks:




Csongor  










Csongor

---

### Post by ronacc on 2009-01-06
use a second flash drive or an sdhc card .

---

### Post by Csongi on 2009-01-06
So after then how does .../grub/menu.lst. looks like, if I have sdb1, and sdb2, on a flash drive?



So the sdb1 is the one gig partition i want to boot from this...........





Thanks:






Csongor Ballay




#name Livesda10 or whatever you choose, (hd0,9) to match sda10
title jaunty Live
root (hd0,9)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw quiet splash
initrd /casper/initrd.gz

title jaunty Live recovery
root (hd0,9)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw single
initrd /casper/initrd.gz
#

---

### Post by ronacc on 2009-01-06
what jerry was showing how to do is installing to your harddrive or ssd . what I am talking about is , if you have no room put everything on flash drives , and then install to a flash drive or sdhc . when you install to the flash drive put everything including grub on that flash drive and then when booting push <escape> and your eee will ask you which drvice to boot from , that way you can leave the grub on your ssd alone and not risk bricking your EEE . You have no extrenal cd drive to use to recover incase of a disaster , so I would not let anything mess with the default grub

---

### Post by Csongi on 2009-01-06
I'm closing the thread........



Thanks everyone who is tried to help me!!!!!



Im finally have been unsuccessful to boot up the operating system....


 


Back to my Gutsy 7.1 till the official release is out.



Csongor Ballay

---

### Post by Eclipse. on 2009-01-07
> **Csongi said:**
> I'm closing the thread........



Thanks everyone who is tried to help me!!!!!



Im finally have been unsuccessful to boot up the operating system....


 


Back to my Gutsy 7.1 till the official release is out.



Csongor Ballay

You could go for something like intrepid or hardy which is newer and better supported and actually released.lol

---

### Post by Csongi on 2009-01-07
Ok!



Thanks everyone..........Im already gave up to install it on my computer.




Maybe I'll  try the final edition..........






Thanks for the posts.....(but please never advertise other repositories then Gutsy, and maybe Jaunty at the future here.....)





Thanks:






Csongor Ballay

---

### Post by razar45 on 2009-01-07
why do you



talk like this



i cannot understand



anything you say

---

### Post by Csongi on 2009-01-07
: )!


I'm really using the friendliest small angels voice..........




I dont know where any other conceptions coming from..........





: )





Csongor

---

### Post by ronacc on 2009-01-08
Csongi  your posts look like your <enter> key is sticking and repeating several times , there are wide spaces between each line you type . This looks very strane and makes your posts hard to read . look your first post at the top of this page and compare the lines you typed and the part that it looks like you cut and pasted and you will see what he was asking about .

---

