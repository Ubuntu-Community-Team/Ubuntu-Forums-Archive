---
title: "Ditching Windows, Loading Ubuntu 6.10"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by Daneeka on 2006-12-07
Hello there. :)

My Windows XP has been playing up like a dog lately, so I finally decided to make the switch!

However, while I have a sound knowledge of computery things, I am no genius - so, before I wreck my computer I thought I'd ask you more knowledgable folk for any hints and tips first.

I am running Windows XP Home edition (Version 2002 - Service Pack 2) with an AMD AthlonXP 2000+, 1.67 GHz, 512MB of RAM.
Graphics is NVIDIA GeForce2 MX/MX 400. (Not sure if there is any other relevant info?)

I'm planning on backing up all the stuff I need, and then... I'm not sure what the next step is?

Put the Ubuntu CD in and tell it to install?

Are there any common mistakes new users make in installing Ubuntu?

And any recommendations for running it? (programs to use to make my life easier, etc...)

Any help would be SUPER appreciated x 8 on it's side.
My Windows is totally munted. Haha.

Thanks again, Tom.

---

### Post by bernied on 2006-12-07
Some boring advice:
- try a few live cds - see how linux works, see if you can access your windows partition and data
- see how much disk space you have and whether both OSes will fit on the same disk. Work out how to resize partitions (this might be challenging if windows is using the ntfs filesystem).
- buy a cheap hard-drive, install linux on that, then you don't need to lose your windows install. You can change which disk boots through the bios.
- 6.10 is not considered stable yet, don't expect it to be. 6.06 is brilliant, and much more stable.
- make sure you have a contigency - like a live cd that can get you on the internet, for when you wreck both your windows and ubuntu (because you will probably ignore most of this advice, like I would)
- have fun

---

### Post by PietreWitobi on 2006-12-07
Hey Tom,

Once you've got your data backed up, Ubuntu pretty much comes with a lot of the stuff you need.  Update Managers, Office programs, media player, etc.  There are a couple of things you may want to look at depending on what you do with your computer.

Media Plugins that you'd prolly like to have, check out:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It'll get you all set on restricted media formats they can't legally put out in the release.

As For apps equivalent to those you might find in Windows, I know there is a thread around here somewhere.  I'll find it and get back to you.

---

### Post by Daneeka on 2006-12-07
> **bernied said:**
> Some boring advice:
- try a few live cds - see how linux works, see if you can access your windows partition and data

I have been running 6.10 off of a CD for the last few days... seems to work really well, but I can't seem to access any of my HDD... I figured this was just because I was running it off a CD?
Maybe I'm just not looking in the right places..?

> - see how much disk space you have and whether both OSes will fit on the same disk. Work out how to resize partitions (this might be challenging if windows is using the ntfs filesystem).
- buy a cheap hard-drive, install linux on that, then you don't need to lose your windows install. You can change which disk boots through the bios.

I don't really want to run both, though... I'd rather just use one of them exclusively... I do have a legit copy of XP, and the one that is currently installed DESPERATELY needs to be formatted, regardless.

> - 6.10 is not considered stable yet, don't expect it to be. 6.06 is brilliant, and much more stable.

Oh, really? So should I download and use 6.06 instead then? Especially as a new user?

> - make sure you have a contigency - like a live cd that can get you on the internet, for when you wreck both your windows and ubuntu (because you will probably ignore most of this advice, like I would)

Hahaha, definately! :mrgreen: 


> - have fun

Thanks heaps, Bernie!

---

### Post by PietreWitobi on 2006-12-07
6.06 will still give you a head ache for a while - especially if you want to get deep into the linux... uh... "jive".  But remember it's a learning process.

I just upgraded to 6.10, so I'm having a few hardware support issues, but it feels a lot like 6.06.

Just try 6.06, then once you get comfortable, you can upgrade or reinstall to 6.10.

And as for Dual boot, I do it on an 80 Gig HD, and it's rather nice.  If you do any gaming at all you'll prolly want to be able to run windows.  I don't use wine (a Windows emulator), but I hear it's a pain.

I've honestly found that in Windows it's easiest to just Virus Scan, Adware Scan, Disk Cleanup, then Defrag - It keeps it running well enough to run games.

---

### Post by PietreWitobi on 2006-12-07
Argh.  Can't Find it.

Just ask around for an equivalent program, and someone will reply.

---

### Post by Daneeka on 2006-12-07
I don't really game much, tbh. :)

I use alot of music / video stuff, and browsing the internet mostly, which I hear Linux can cater for.

Is 6.06 really tricky? The problem with that would be that my whole family (13 year old little brother and parents) use the computer too, and they already are always asking me ridiculous questions about how to use stuff... so if it's very tricky, I might just try to stick with this version, if it's not *too* unstable...


A quick question: If I'm running it off the CD right now, should I be able to access my HDD? All I get when I click on "Places > Computer" is 'Floppy Drive', 'CDROM/DVDROM Drive', 'CDRW Drive' and 'Filesystem'... none of which seem to contain my HDD stuff.

PS Thanks heaps you guys!

---

### Post by bernied on 2006-12-07
I didn't say don't use 6.10 - it seems pretty good to me, just don't expect it to be perfect. I think it's pretty close to being a stable release and in my experience it's generally easier to do a clean new install of ubuntu than it is to upgrade from one release to another (6.06 = Dapper, 6.10 = Edgy). The KDE/kubuntu version of Edgy has some excellent improvements over Dapper.

I use Kubuntu, so it won't be exactly the same, but you should be able to get to your windows partition somewhere in the GUI. In kubuntu, its in the System Menu, under Storage Devices. Or, in a terminal, try 
```
sudo fdisk -l
```to see where your partitions are, then have a look at 
```
man mount
```and
```
man fstab
```
You will need to create a 'mountpoint' - this is just a directory, and you would do something like
```
sudo mkdir /mnt/winsucks
```then you'd have to work out how to mount it, but be very careful if it's ntfs

Do some reading on ubuntu philosophy - it will help you to understand why the third party drivers and media codecs are not included in the basic install. I recommend Automatix for installing these (but don't break the law!!)

[http://www.ubuntu.com/ubuntu/philosophy](http://www.ubuntu.com/ubuntu/philosophy)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

---

### Post by ]Nbx*cmD[ on 2006-12-07
Since nobody mentioned it yet I'll do it: INSTALL AUTOMATIX! If it's your first gnu/linux system it will make your life much easier, and it it's not, it'll help you saving some time :)

Go to [www.getautomatix.com](www.getautomatix.com) and follow the installation instructions for your distribution (Ubuntu 6.10).

I forgot about window$ lots of years ago, no micro$oft software entered my home anymore, and I'm also a gamer. Don't worry about games, you can find wonderful ones for gnu/linux as well. Look at [www.linux-gamers.net](www.linux-gamers.net)

Well... I can play quake 3 without any problem, much better than it "worked" in window$. You can find all ID games, as well as some loki games (soldier of fortune, kohan...) and lots (i mean LOTS) of opensource and free games, which have nothing to envy to the propietary and paid ones :)

Good luck and welcome to the opensource and friendship users community :)

---

### Post by PietreWitobi on 2006-12-07
If your whole family is going to be using this I HIGHLY suggest you keep XP.

I haven't used the 6.10 liveCD, but if it comes with the same partitioner as 6.06 did (which I'm sure of), then You can very easily partition your hard drive.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

That Document might shed some light on schemes.

No Ubuntu is all that tricky, but there is a pretty steep learning curve to all things Computive.  If you're willing to learn - you will.  But your family sounds like mine in that they're perfectly wiling to let you be the computer guy and fix what goes wrong.

In that case, keep Windows around, so they can boot to it and feel comfortable in a "safe" environment.  As dearly as I hold open-source to my heart, I really think that having the familiar conventions is going to make the transition easier on your family and therefore easier on you.

Let yourself get better at manipulating an installed version, fixing bugs, etc... then let your family have you there as the local "expert."

GRUB is great for dual booting, and you can even configure it to be pretty and auto boot to Windows (So your family can skip the interface and you can deal with the menu).

Er... I dunno about the live CD.  I've tried it before, but I was less versed on the ol' Ubuntu at the time, so I failed regardless

---

### Post by Unterseeboot_234 on 2006-12-07
Well, I've been banging around in ubuntu now for a couple of months and I enjoy computers again. The LiveCD has been my best friend. Make sure you can run the computer from LiveCD, log onto the internet and just about any problem you're having can be fixed. The MAIN difference is Linux info is online and most of the M$ stuff is an out-of-date book somewhere.

---

### Post by Daneeka on 2006-12-07
Well, it's all gone down the crapper now...
I managed to backup my stuff, but now I can't even load the LiveCD.

I keep getting the error "The greeter application appears to be crashing. Attempting to use a different one." and then it still doesn't work.

I checked that the integrity is all good, and it was... I dunno.

But I have to sleep now.
Thanks again for all your help. :)

I'll be back soon. It's all very stressful. hahaha.

---

### Post by Sidster on 2006-12-07
Hi

I went through exactly the same ordeal about 3 years ago. My starting point was Mandriva. It was when they just changed their name from Mandrake Linux. I couldn't get it to work the first few times and was very frustrated. Looking back I wish somebody had told me all the things I know now but I've come to realise that it wouldn't have made a difference. I needed to discover it all for myself. That doesn't stop me from trying to impart my limited Linux know-how with anybody who'll listen however. Anyhow, If you really get stuck just take a deep breath and search the forums. In my experience pretty much every issue I've had was somewhere on the forums. If it ain't on the forums it'll definitely be somewhere google can find it. Keep going dude.:p After 3 years I'm finally getting to the point where I'm more comfortable with Ubuntu than Windows. Hang in there cause the reward is worth it.

On a side note. What do you forumites think about creating a thread with "Things noobs often overlook when moving to Linux/Ubuntu" or "Things noobs wish someone had told them before moving to Linux/Ubuntu"

I think it could be pretty helpful. Anyhoo, just thinking out loud:)

---

### Post by Daneeka on 2006-12-11
Hi again! I'm trying to load from the Live CD but it keeps asking for a password? I have no idea, I never set one up?

It's really wierd. It was working fine a few days ago, but now I just CANNOT get it to work.

Anyone have any idea why this is happening?

 I can't figure it out. Thanks. :)

---

### Post by Daneeka on 2006-12-11
It finally works! Yay!

---

### Post by Daneeka on 2006-12-11
One more quick question:

If my HDD is partitioned using NTFS, why is that a problem, and how can I change this?

Thanks!

---

### Post by bernied on 2006-12-11
This is how I understand the ntfs problem (someone tell me if I'm wrong):
NTFS is a proprietary filesystem, which means it was developed by Microsoft for Microsoft and they haven't released the details of how it actually works to anyone else. So when linux developers want to use ntfs, they have to reverse-engineer. So they have to figure out what's going on when ntfs is used in Windows, then try to imitate that in linux, then see if the result is compatible with Windows. This takes a long time and is not a very effective way to make software. So the ntfs drivers have been a long time coming and they've been buggy along the way. But I think I'm a bit behind the times on this and ntfs works in linux now. But I still don't trust it.

An easy way to avoid sharing the ntfs partition is to have a partition designed specifically for sharing between windows and linux. I use FAT32 filesystem for these partitions, because it works very well in both OSes. So, on windows this would look like another hard-drive. You can also use ext2 or ext3, but you need to install some software in Windows (I don't know the details).

You might also copy the entire contents of your ntfs partition to another location, reformat the ntfs partition as FAT32, then copy the files back, but I don't recommend this as there are so many ways that a tiny mistake could result in you losing the lot.
EDIT: ignore this last bit, or at least do some more research - I doubt it would work at all even if you don't make any mistakes, because I think Windows would get mighty confused at you changing its filesystem. Only other alternative is to re-install windows into a FAT32 filesystem, also a huge pain.

---

### Post by scrooge_74 on 2006-12-11
If you don't need windows on that PC, do as I did: completely wipe out the drive and let Gparted take care of the partinioning and the filesystem.

Maybe just tell Gparted that you want /home to be in a different partition just to be safe in case in the future you have some problems with installation

---

### Post by bulldog on 2006-12-11
Correction on the NTFS thing.
Ubuntu,and other distro's too,can **read** NTFS file system perfectly,so you can copy your data to your ubuntu partition.
But **writing** to a NTFS file system isn't supported natively,but there are drivers which can make Linux write to a NTFS disk.

This last option,the writing,is a little bit of a risk,it can destroy your NTFS.

But if you want to keep your windows,defrag it several times,than resize the partition so you get some room for ubuntu.
It depends on what you want to do with ubuntu,installing a lot of software,downloading a bunch of DVD's,how much space you should need.

For a test install for surfing and mailing and install some software you have enough space,when you have 15-20GB.
Use 10GB for the /  [root] partition
Use 1GB for the swap partition
Make the rest your /home.

---

