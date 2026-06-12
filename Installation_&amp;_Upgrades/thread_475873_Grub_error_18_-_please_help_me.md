---
title: "Grub error 18 - please help me"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by conducteur on 2007-06-16
Hello,

until last week everything was fine with Xubuntu on an old PC (Pentium II 400 MHZ) but then the old 20 GB hard drive died...

So I bought a new 250 GB hard drive and installed Xubuntu... but it wouldn't install properly. It either refuses to install the programs any further than 6% or, if I'm successful, it makes me reboot and then displays "grub error 18".

I know what error 18 means and I read several posts about what to do, but nothing works. Is there any reliable (and not too complex) way for me to solve this?

Thanks in advance.

---

### Post by floke on 2007-06-16
How long are you leaving it at 6%? My installs have hung there for a while before moving on.

---

### Post by logos34 on 2007-06-16
> **conducteur said:**
> Hello,

until last week everything was fine with Xubuntu on an old PC (Pentium II 400 MHZ) but then the old 20 GB hard drive died...

So I bought a new 250 GB hard drive and installed Xubuntu... but it wouldn't install properly. It either refuses to install the programs any further than 6% or, if I'm successful, it makes me reboot and then displays "grub error 18".

I know what error 18 means and I read several posts about what to do, but nothing works. Is there any reliable (and not too complex) way for me to solve this?

Thanks in advance.

You might see if there is a bios update for that machine (the latest of which is probably a good many years old).  Your bios is likely running up against cylinder limits.  You can also reinstall but this time create a 50-100MB /boot partition at the front of the disk, then / and /swap.  See if it allows you to get throught the setup and reboot successfully this time.

Read this on[ error 18.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

---

### Post by conducteur on 2007-06-16
Many thanks but I have already tried the 100 MB boot partition. Maybe I made a mistake somewhere though, and this is what I'm trying to understand.

Is there a partition that I must make bootable? Which one? The "boot" one, the "/" one or the third one?

Thanks in advance for your help.

---

### Post by logos34 on 2007-06-16
> **conducteur said:**
> Many thanks but I have already tried the 100 MB boot partition. Maybe I made a mistake somewhere though, and this is what I'm trying to understand.

Is there a partition that I must make bootable? Which one? The "boot" one, the "/" one or the third one?

Thanks in advance for your help.

I believe you want the /boot partition flagged bootable '*'--grub should point to that because that's where menu.lst is.

---

### Post by Pumalite on 2007-06-16
> **logos34 said:**
> I believe you want the /boot partition flagged bootable '*'--grub should point to that because that's where menu.lst is.

Use the guided method and give the entire disk to Ubuntu.

---

### Post by conducteur on 2007-06-16
Thanks for your quick reaction to my message.

Here is what the partition manager says:

IDE 1 master (hda)
n°1      primary     98,7 MB     B  f  ext3     /boot
n°2      primary     50  GB            f  ext3     /
n°3      primary     1.2  GB           f  swap   swap
n°4      primary      20 GB            f  ext3     /home

Just a question: should all of these partitions be primary or should some be logical?


Thanks in advance

---

### Post by conducteur on 2007-06-16
Pumalite,

giving the entire disk to Xubuntu is what I tried first, but it looks like my bios is way too old to accept a 250 GB disk

---

### Post by logos34 on 2007-06-16
> **conducteur said:**
> Thanks for your quick reaction to my message.

Here is what the partition manager says:

IDE 1 master (hda)
n°1      primary     98,7 MB     B  f  ext3     /boot
n°2      primary     50  GB            f  ext3     /
n°3      primary     1.2  GB           f  swap   swap
n°4      primary      20 GB            f  ext3     /home

Just a question: should all of these partitions be primary or should some be logical?


Thanks in advance

All primary is just fine, except that's the limit - 4 primaries.  to add more you'd have to convert, say, /home into a logical partition inside an extended partition (the latter of which you could subdivide however you desire).

---

### Post by conducteur on 2007-06-16
Well, I've managed to get past the "installing base system" step but the next one, "choosing and installing software", which suggested installing localized versions, has just ended up in failure and a red screen which read that a step of the configuration process has failed.

What can I do?

---

### Post by conducteur on 2007-06-16
There is more bad news,

Chroot LTSP has failed, and so have "installing" grub and "installing LILO" which I tried as an alternative.

This really looks bad. Any ideas?

---

### Post by conducteur on 2007-06-16
Actually Grub seems to be trying to install on a hd0 disk whereas mine is hda. Could this be why Grub refuses to install?

But then Lilo suggested to install on hda and it also failed...

Any suggestions, as I'm really stuck now?

---

### Post by logos34 on 2007-06-16
hd0 = /dev/hda.  hd0 is grub-speak for the first drive detected in the bios.  If you had two disks the next one would be 'hd1' and so on...You could try manually specifying 'dev/hda' but since they're one and the same I'm not sure that'll help...You do have old hardware exept for the drive, how much memory?  Have no idea why it was working before and not now, nor why some installs finish while others do not.

afterthought: try putting grub on the /boot partition rather than MBR (master boot record)...so specify '/dev/hda1'.

---

### Post by conducteur on 2007-06-16
I have 384 MB RAM but I really think that the problem comes from the new HD being very recent and the old one being very old... just as old as the rest of the hardware, in particular the bios.

---

### Post by logos34 on 2007-06-16
yeah, 384mb is plenty for xubuntu.

Are you using the same cd to install this time as you did before?  Even so, is it possible there's some corrupted files in it, or did you do the md5sum AND cd integrity check?

Not sure what else to suggest.

edit: check that the BIOS settings for the drive are correct.  Should be set for 'auto(detect)' or something similar...or jsut experiment with whatever other options it gives you (LBA, CHS, etc).

---

### Post by Pumalite on 2007-06-16
> **logos34 said:**
> yeah, 384mb is plenty for xubuntu.

Are you using the same cd to install this time as you did before?  Even so, is it possible there's some corrupted files in it, or did you do the md5sum AND cd integrity check?

Not sure what else to suggest.

edit: check that the BIOS settings for the drive are correct.  Should be set for 'auto(detect)' or something similar...or jsut experiment with whatever other options it gives you (LBA, CHS, etc).

You could do a number of thing, but that depends on what you have on your system and how you partitioned your hard drive. I suggest updating your BIOS. Also why don't you post some more info; like fdisk -l , As root 'blkd' , cat /etc/fstab. Also tell us more about your hardware. If you install again and get a GRUB error, then try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by JimNSB on 2007-06-16
> **conducteur said:**
> Well, I've managed to get past the "installing base system" step but the next one, "choosing and installing software", which suggested installing localized versions, has just ended up in failure and a red screen which read that a step of the configuration process has failed.

What can I do?

Sorry, no answer ...but some sympathy: the _exact_ same thing just happened during my install!
-used GParted to create and format these partitions in the free-space following my Win2k partition:
[LIST]
[*][COLOR="Blue"]/[/COLOR] (primary, ext3)
[*]extended partition with [COLOR="Blue"]/windows[/COLOR] (FAT32) and [COLOR="Blue"]/home[/COLOR] (ext3)
[*][COLOR="Blue"]swap file[/COLOR]
[/LIST]

-used the alternate CD to complete the partition setup and then install
-install went OK till "*choosing and installing software*"
-I retried that step a couple times, then selected the next step (GRUB) which seemed to install
-selected 'finish'
-on reboot I chose Ubuntu from the GRUB menu, but it didn't start-up ...just a prompt: (computername)@(username)$

I'm going to try a 'repair' using the alternate CD (FYI: md5 checked out)....

---

