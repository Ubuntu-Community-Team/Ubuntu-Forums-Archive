---
title: "How can I tell if Ubuntu is installed on an extended partition/switch to a primary?"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by sirspazzolot on 2010-09-23
I'm dualbooting 10.04 with Vista and I think that my Ubuntu installation is on an extended partition, thus making it unrecognizable by the Chameleon bootloader.

Is there a way to get my Ubuntu installation onto a primary partition, whether it be moving the installation somehow or switching the partition type? I don't mind file damage or loss; I don't have anything important.

I guess if need be I can just uninstall Ubuntu and reinstall it, but that would take a lot more time. How would I safely uninstall/reinstall Ubuntu on a primary partition while leaving my Vista installation boot-able? Vista is on my C: Drive, and I believe I have a 15GB extended partition with Ubuntu installed and a D: drive that should have no OSs installed on it.

Thanks in advance. :)

---

### Post by woodmaster on 2010-09-23
in a terminal

```
sudo apt-get install gparted
```

when you run this app it will load all your partitions on all disks and tell you if they are primary or logical and provide you a convenient gui to modify them

---

### Post by sirspazzolot on 2010-09-23
I have gparted. Does it really just let you change it to a primary partition? I'm on Vista ATM for homework so I can't check.

---

### Post by wilee-nilee on 2010-09-23
> **sirspazzolot said:**
> I have gparted. Does it really just let you change it to a primary partition? I'm on Vista ATM for homework so I can't check.

Not if it is mounted!!!

You need a live cd, but this sounds apple so be careful and get help from a apple user.

---

### Post by sirspazzolot on 2010-09-23
Alright. [http://img834.imageshack.us/img834/263/gparted.png](http://img834.imageshack.us/img834/263/gparted.png) That's a picture of my partition setup, if it's needed. Can Ubuntu even run on a primary partition? The extended partition is divided into the swap thing and then storage. It sounds like I can't make it just one partition, can I? Meh. I'll try it.

---

### Post by sirspazzolot on 2010-09-23
Oh, and where is GRUB? If I switch it to a primary partition will that break my ability to boot into Vista or Ubuntu?

---

### Post by wilee-nilee on 2010-09-23
> **sirspazzolot said:**
> Oh, and where is GRUB? If I switch it to a primary partition will that break my ability to boot into Vista or Ubuntu?

Linux will run in a primary. If you make another primary though you will have no swap room, that will be the max 4 primary partitions. This is okay though if you have enough ram, but you wont have a usable hibernate or suspend . I think you can acyually build those in the Ubuntu install rather then in partitions, I just don't know how, or the use.

When you install ubuntu it will put its bootloader in the mbr, I assume; that's the usual place though, so you just have to know where to go from there to get your bootloader working. I am not familiar with putting the grub bootloader in the partition, I use it it the mbr to boot all the other OS. There are others who are familiar though.

Is sda1 a recovery? as sda2 has the boot flag. If this is just straight MS the grub bootloader installed may just boot you in to the other OS hard to say.

---

### Post by sirspazzolot on 2010-09-23
Shoot. I have to somehow merge my C: and D: drives. Those are the two NTFS ones. Any ideas how?
And I have no idea what that FAT32 partition is. How would I go about mounting it? mount -t /dev/sda1 did nothing.

---

### Post by sirspazzolot on 2010-09-23
"mount -t dev/sda1 /media/cdrom0 did nothing"*** sorry, forgot that last part.

---

### Post by wilee-nilee on 2010-09-23
Why don't you run the bootscript in my signature, in code tags as described, or just click on the # in the reply panel; for the text, from running the script. 

This will give us the lowdown. Do you have a backup of the Vista. or a install disc? I think sda1 is a recovery partition.

---

### Post by sirspazzolot on 2010-09-23
Yes, it's a recovery partition, I googled the name and apparently it's fairly common. I don't have a vista backup or any recovery CDs but do you think that moving the partition to unallocated space on my external drive would make sense, and then if the need ever arises I could just move it back to my laptop and use it? I'm thinking if I move it, then I could delete it off my laptop and then copy the contents of my D: drive to my external drive, delete D, put important stuff on an expanded C:, and have unallocated space left over for my next install. Does that make sense to you?

---

### Post by wilee-nilee on 2010-09-23
> **sirspazzolot said:**
> Yes, it's a recovery partition, I googled the name and apparently it's fairly common. I don't have a vista backup or any recovery CDs but do you think that moving the partition to unallocated space on my external drive would make sense, and then if the need ever arises I could just move it back to my laptop and use it? I'm thinking if I move it, then I could delete it off my laptop and then copy the contents of my D: drive to my external drive, delete D, put important stuff on an expanded C:, and have unallocated space left over for my next install. Does that make sense to you?

As it is now, I suspect it is a door stopper so to speak. Getting it to trigger a actual recovery would probably be difficult. So I would, if it was me call the computer maker, and see what a straight install disc or the oem set would be, mine for XP was 20$. Does this recovery show in the bootloader you have, it seems you had no idea it was there.

Run the script though at least for yourself and look at the sda1 partition at the top for any boot files and if you see the correct files in the sda3 OS that is the boot.

You can just copy paste in a reply with the # to trigger in code tags for me to have a look if needed, at the script.

---

### Post by wilee-nilee on 2010-09-23
If I understand the use of the Chameleon bootloader it is installed in your MS setup to boot OSX. If you don't have OSX any more, this may be just be loading the grub boot loader to the mbr, and everything is working without any tweaking. You have to know which grub, and how to do it, and **I wouldn't recommend this really myself without looking at the boot script, though.**

Reloading the original MS bootloader is easy as well with a recovery disc available on line. This is a very small 160MB or so boot disc to the vista recovery gui.

---

### Post by srs5694 on 2010-09-23
I see you double-posted your proble. (The other thread is [here.](http://ubuntuforums.org/showthread.php?t=1580680)) This is discouraged. Perhaps a moderator could merge the threads....

---

### Post by wilee-nilee on 2010-09-23
> **srs5694 said:**
> I see you double-posted your proble. (The other thread is [here.](http://ubuntuforums.org/showthread.php?t=1580680)) This is discouraged. Perhaps a moderator could merge the threads....

LOL thanks, carry on.:confused:

---

### Post by sirspazzolot on 2010-09-23
> **srs5694 said:**
> I see you double-posted your proble. (The other thread is [here.](http://ubuntuforums.org/showthread.php?t=1580680)) This is discouraged. Perhaps a moderator could merge the threads....
Heheh... Sorry... Well the other thread was updated so I guess I can let this one die and since there's a link to the other one in here... I don't know. Maybe I should just be banned or something.

---

