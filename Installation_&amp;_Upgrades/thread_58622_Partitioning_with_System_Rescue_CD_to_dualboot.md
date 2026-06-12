---
title: "Partitioning with System Rescue CD to dualboot"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by presentt on 2005-08-20
Hello,

I'm trying to set up my PC to dualboot WinXP Pro SP2 and Ubuntu Linux.  I read on UbuntuLinux.org that to do that, I need to repartition my harddrive using the tool QTParted on the "System Rescue CD."

I downloaded the ISO for the System Rescue CD (version 0.2.15),  and burned it to a  disc.  Then I defragged my harddrive, put in the System Rescue CD ("CD" from now on...) and rebooted my PC.

When I got the "Boot:" message, I hit enter like the instructions on UbuntuLinux.org said, and let it boot.  That's where I hit some problems.

The boot hung at the message "hda: host protected area => 1"

I don't know what this means, and I was fairly patient (I let it sit for two hours while I did other stuff).

Can someone help me get the CD to boot so I can use QTParted and repartition my drive?  Thank you.

---

### Post by Storm Rider on 2005-08-20
You don't need the resuce cd !  Put the Ubuntu cd in your drive and reboot.  It will resize your Windows drive for you.  You'll have the option to select the default partition size or adjust it.

---

### Post by presentt on 2005-08-21
I'm new to this, but [https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo") says
"The Ubuntu installer does not yet include support for resizing NTFS partitions..."

Doesn't WinXP use NTFS filesystem, and if there is only 1 partition on my drive, wouldn't the whole drive use NTFS?

Thanks.

---

### Post by nad on 2005-08-21
"hda: host protected area => 1" indicates that your hard driive is write protected.

This may be in bios (boot sector protection or password protected hard drive) or an encrypted filesystem that will need to be unencrypted before you do anything with the filesystem or partition.

---

### Post by presentt on 2005-08-21
I use a Dell Dimension 8300, and I haven't manually encrypted my HD. Do Dells normally come encrypted, and if I can't unencrypt it, will that prevent me from booting the System Rescue CD and consequently Ubuntu?  [crossing fingers...]

Also, I'm fairly certain my drive is *not* write-protected (at least, as I know the definition), because I have always been able to save, delete, defrag, overwrite, etc. files on it.  However, this is through Windows, so is it possible that it is still write-protected?

Thanks.

---

### Post by nad on 2005-08-21
I remember reading a post that mentioned a "well known issue" regarding grub, dell and the new no exec (?) feature.

For the life of me I can't find any reference to it. I'll keep looking. In the meantime... anyone else?

---

### Post by chrisod on 2005-08-21
I've got a Dell 600 M that came with XP preinstalled. I use a linux system rescue disk to repartition the hard drive, and then installed Ubuntu with no problems. However, due to user error, I do have about 10 GB unusable, something about a 4 partition maximum on PC hard drives, Neither Windows dscmgmt or Qparted or the system resuce disk can do anything with the lost space.

I imagine Partion Magic can merger that space back into a partion, but I'm trying to avoid spending $30 on software I'll use once.

If anybody has any ideas I'm listening.

---

### Post by presentt on 2005-08-21
Wow, sorry Storm Rider.  I did some more research, and found that page I cited refers to an older version of Ubuntu...the new installer supports NTFS repartitioning.

Thanks for the help!

Although it's no longer a priority for me, I'd still like to get the System Rescue CD up and running.  Any ideas?

---

