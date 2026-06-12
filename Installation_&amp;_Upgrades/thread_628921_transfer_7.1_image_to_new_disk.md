---
title: "transfer 7.1 image to new disk"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by calldrin on 2007-12-01
I have my 7.10 completely configured on my hard drive.(and working just like I want it to)

Now I need to install this configured version on to a different drive.
I know I could reinstall and then reconfigure everything and lose all my emails (evolution) and contacts.... so this is not really a good option.

Is there a way to make a image copy and install it onto my drive?

Or is there anyway to do a backup of all my changes and files to reinstall on to a NEW 7.10 install?

Please advise what would the best/fastest/easiest way!

The new drive will be a dual boot with XP.

I have done this in windows using acronus (sp).

Thanks to all that provided answers to my "dumb" question in the past :-)

Chuck

PS: I need simple step my step instructions. :-(

---

### Post by logos34 on 2007-12-01
Partimage is what most people use.  (it's in the repos)

Partimage
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

dd command
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

Clonezilla
[http://www.linux.com/feature/115208](http://www.linux.com/feature/115208)

You might also consider backup preferences for gnome.

sudo apt-get install gnome-reset

It handles:

-mail, calendar and addressbook
-Nautilus
-Look & Feel
-Gnome panel

I have it and was going to try it out yesterday before I transferred /home dir to a separate partition, but forgot. (I wish I had because my gnme preferences got lost in the transfer)

---

### Post by calldrin on 2007-12-02
> **logos34 said:**
> Partimage is what most people use.  (it's in the repos)

Partimage
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

dd command
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

Clonezilla
[http://www.linux.com/feature/115208](http://www.linux.com/feature/115208)

You might also consider backup preferences for gnome.

sudo apt-get install gnome-reset

It handles:

-mail, calendar and addressbook
-Nautilus
-Look & Feel
-Gnome panel

I have it and was going to try it out yesterday before I transferred /home dir to a separate partition, but forgot. (I wish I had because my gnme preferences got lost in the transfer)
Thanks for the ideas..
I have spent 8 hrs today trying to do a clone/image to install on my other hard drive.
Most of this time was trying to get Clonezilla to work. I think I finally got a image saved, but now can't for the life of me figure out how to get into my new drive.
All the commands are so foreign to me as a windows user. The sda, sdb, sda1, sdb1, hdb, sde, etc,etc is driving me nuts. The target drive is NTSF as C: and D: C: is XP and D: is empty. When I try to install the image, Clonezilla wants to know where to install. I don't know and can't find out what C: or D: is called in Linux.
I'm so discouraged that I'm about ready to give up. Really can it be that hard to make a clone and install it?
I've done it in windows in a matter of a few minutes.
If I had any idea it would take up my whole day, I would have just started from the begining and spent the time reinstalling all the add on programs that I have.
If I could find someone near me, I would pay them to do this "nasty" task :-(
Thanks for reading my VENTing..
Chuck

---

### Post by logos34 on 2007-12-02
> **calldrin said:**
> I think I finally got a image saved, but now can't for the life of me figure out how to get into my new drive.
... The target drive is NTSF as C: and D: C: is XP and D: is empty. When I try to install the image, Clonezilla wants to know where to install. I don't know and can't find out what C: or D: is called in Linux.

So, you saved/copied the image to the other drive or not?  If so, you then need to [reinstall Grub bootloade]("http://ubuntuforums.org/showthread.php?t=224351")r to the mbr so you can get into it.

You can't copy an ext3 filesystem image onto an ntfs partition.  The target/destination needs to be mounted (you have to create a mount point--can't write to it unless it is), and you have to put in the correct path (it's easy to get this part wrong)

---

### Post by calldrin on 2007-12-02
> **logos34 said:**
> So, you saved/copied the image to the other drive or not?  If so, you then need to [reinstall Grub bootloade]("http://ubuntuforums.org/showthread.php?t=224351")r to the mbr so you can get into it.

You can't copy an ext3 filesystem image onto an ntfs partition.  The target/destination needs to be mounted (you have to create a mount point--can't write to it unless it is), and you have to put in the correct path (it's easy to get this part wrong)

What I did was save the image to a external usb drive. This way I have a fail safe copy. My problem is that when I try to install the image using Clonezilla, it wants me to identify which drive to install to. This is a problem because I don't which drive is D: (C: is XP)
I don't understand what you mean about mounting the target drive and MBR ??
Sorry about my lack of understanding of what I guess should be a "simple" concept.

Again thanks,
Chuck

---

### Post by logos34 on 2007-12-03
Cloning the partition or drive does NOT include the bootloader.  So you need to reinstall it using the link I gave you after you copy it to the new drive.

On the clonezilla live cd you need to 'mkdir' to create a mount point for the new/destination partition.  Then mount it and type in the path to it so clonezilla knows where to restore to.  

sudo fdisk -l 

lists all the partitions

---

### Post by calldrin on 2007-12-03
> **logos34 said:**
> Cloning the partition or drive does NOT include the bootloader.  So you need to reinstall it using the link I gave you after you copy it to the new drive.

On the clonezilla live cd you need to 'mkdir' to create a mount point for the new/destination partition.  Then mount it and type in the path to it so clonezilla knows where to restore to.  

sudo fdisk -l 

lists all the partitions

I want to thank you and others that tried to help me ;-) ..
BUT .. I screwed up my system so bad I had to reformat my drive, reinstall XP and reinstall a fresh copy of 7.10.  All this only took about 5-6 hrs ;-(
At least it is now working again!
What have I learned? :
Trying to work in Linux is way above my abilities.  There is just too many assumptions made that the user should "JUST" know how to do these things..
Believe me I had tried to learn to get around in Linux... I have spent well over 100+ hrs. (this is no lie) since I started using Linux several weeks ago. 
What does Linux NEED?
A very simple guide for Dumb, Dumb, Dummies!!
Written with NO assumptions made about any prior Linux knowledge.
I really like Ubuntu and now if I could just learn how to do some of the basic things that are not shown on a menu.
Like, how can I see a visual display of all the file "tree" and a complete list of the installed programs ?
I could go on and on but this is just an example.

Maybe you or someone can point me in the right direction!

Thank you,
Chuck

---

