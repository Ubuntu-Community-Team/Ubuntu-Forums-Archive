---
title: "Backing up my harddrive after install"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by ERRRIMMAD on 2013-05-19
I recently crashed my Ubuntu system, it seems too hard to recover to bother so I'm just going to reinstall.

Luckily I split my OS and my user files on different drives, IE music, videos, downloads.

I'm looking at Deja Dup as a method of backing my system up, but I need to know how much trouble I can get in and still back myself out?

For example, can I crash the system like I just did, then reinstall Ubuntu, reinstall Deja Dup, and completely restore to the point I was at, updates, drivers, apps and all?

Or will I have to use a drive clone for something like that? 

Obviously my mistake was not making backing my system up my #1 priority.

---

### Post by sudodus on 2013-05-19
I'm glad you  split your OS and your user files on different drive, and that your user files survived :-)

It is possible to restore a system from a backup with Deja Dup, but I have not used it myself. I have large data partitions (like you) and small system partitions, and I make images of the system partitions (or the whole drive) with Clonezilla. It works well for me, but I know that other people prefer backup systems like Deja Dup.

The important thing is that you decide what suits for you, that you make the backup, and that you check that it really works to restore from the backup. Of course, the most important thing is to have a backup of your personal data (user files). And those data are usually well compressed already, so you can have plain copies of them, easy to see and check.

The backup should be in a separate drive or in a separate computer. If the backup copy is in another house, your family pictures will be save in case of a fire.

---

### Post by ERRRIMMAD on 2013-05-19
> **sudodus said:**
> I'm glad you  split your OS and your user files on different drive, and that your user files survived :-)

It is possible to restore a system from a backup with Deja Dup, but I have not used it myself. I have large data partitions (like you) and small system partitions, and I make images of the system partitions (or the whole drive) with Clonezilla. It works well for me, but I know that other people prefer backup systems like Deja Dup.

The important thing is that you decide what suits for you, that you make the backup, and that you check that it really works to restore from the backup. Of course, the most important thing is to have a backup of your personal data (user files). And those data are usually well compressed already, so you can have plain copies of them, easy to see and check.

The backup should be in a separate drive or in a separate computer. If the backup copy is in another house, your family pictures will be save in case of a fire.

I was looking into Clonezilla, mind if I ask a couple questions about it?

I want to install Clonezilla to an  internal hard drive so I can dual boot it along side Ubuntu 12.04.  meaning so when I boot grub it offers me Ubuntu or Clonezilla as  options.
 I do not want to have to use a USB thumb for this or a CD/DVD as I do  not want to put un wanted wear and tear on my optical drive every time I  want to back up Ubuntu.
 I was hoping to put it on the same 256gb SSD drive as Ubuntu but just make two partitions, can this work?
 If not I also have a second rotating drive 1TB I could partition, I  wanted to back up the cloned image to the 1TB drive, will I need to  partition to 256gb on the rotating drive? I want to use the rest of the  1TB drive so I don't want the whole thing used as a backup for the  cloned image.
 I also use the rotating drive as an extension of the SSD drive,  meaning I have all user files on this drive as well as a swap system  should I ever need it.
 I do not however want Clonezilla to back up the SSD and rotating  drive, only the SSD, I imagine Clonezilla will only back up partitions  you tell it to back up, and it will not read my system files in Ubuntu  and see I use the TB drive as an extension of the SSD and try and back  up the TB drive as well.

---

### Post by jamesisin on 2013-05-19
Clonezilla is a tiny cloning utility.  I run it at work from a USB drive constantly.  There should be no reason to create a version of this on a HDD as a boot option.  In fact I have Clonezilla and several other utilities on a bootable USB drive created using a Windows application called Yumi, and I run Clonezilla entirely from RAM anyway (I just load it from the USB drive and remove that drive).

Clonezilla can be used to save or restore entire drives or individual partitions.  A complete build of Windows 7 with Office and all that crap (taking up, say, 40 GB of HDD space on a 200 GB drive) might yield a Clonezilla image of about 18 GB.  That *image* you should certainly write to a HDD somewhere.  You could connect to that drive internally on your machine, externally perhaps through USB, or across your network.

---

### Post by Mark Phelps on 2013-05-19
IF you go to the Clonezilla website, they have instructions for how to boot from an ISO stored on your drive.  

I do this myself so I  can select Clonezilla from the GRUB menu, boot into it, and use it to do backups and/or restores.

---

### Post by sudodus on 2013-05-19
I have Clonezilla on USB as well as CD, and use whatever suits for backing up each particular computer.

And it is also possible to boot from the iso file. However, I'm not sure you can make an image of the whole drive, where the Clonezilla iso file is located.

So there are many ways to do it :-)

---

