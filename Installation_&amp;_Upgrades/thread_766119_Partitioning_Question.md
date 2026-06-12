---
title: "Partitioning Question"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by jorwex on 2008-04-25
Is it okay to install windows at the end of my drive, after where most people put there primary AND extended/logical drives?

See pic:

[IMG]http://www.glue.umd.edu/~jwexler/screenshot.png[/IMG]

After having to borrow a friend's computer to run TurboTax, I'd like to put a tiny windows partition back on my pc. Rather than slide down /dev/sda6/ and that other tiny Documents partion down to the right, I was wondering if there's any problem with making a 3rd primary partition at the end of the drive to boot windows. 

Now, just theoretically thinking like that, I see no problem. Although, when I tried something similar talking my friend thru the process on the phone the other day, the windows installer didnt see the fat32 partition that he made in gparted at the end of the disk, and somehow he lost his whole partition table and ended up starting from scratch cuz he didn't have anything important to try and salvage.

However, I would like to not have to backup everything if necessary (i know it's good practice to, but i just want to find the "right" way to do this).

So any tips? Should I really slide everything down so all of the primary partitions are next to each other?

Thanks

---

### Post by logos34 on 2008-04-25
> **jorwex said:**
> Is it okay to install windows at the end of my drive, after where most people put there primary AND extended/logical drives?

...

Rather than slide down /dev/sda6/ and that other tiny Documents partion down to the right, I was wondering if there's any problem with making a **3rd** primary partition at the end of the drive to boot windows.

You should be able install XP on a logical partition...just shrink sda6.  I've done the very same thing a few times, no problems for the most part, except the most recent one slightly screwed up the partition table so gparted couldn't read it (specifically, the "DiskLabelType"). But fdisk still showed everything ok.  I was able to fix it and write a new partition table with TestDisk.

You could put it on a (4th) primary partition after shrinking sda6 and the extended, sda3.

---

### Post by jorwex on 2008-04-25
oh!  i was under the distinct impression that windows xp could ONLY be installed on primary partitions. 

so in either case, I'd install windows, then install ubuntu (i plan to reinstall linux anyways)?

---

### Post by iaculallad on 2008-04-25
Yes, install window$ first then Ubuntu. M$ window$ just seems to dislike installing other OS first before itself. :-)

---

### Post by Herman on 2008-04-25
I agree with logos34, it is possible to install Windows in any partition and boot it in any location on the hard disk.
It's *easier* to let Windows be installed first and have the first position in the hard disk, but it's not too hard to install it elsewhere as a non-first partition either numerically or position-wise and boot it want to for some reason.

Regards, Herman :)

---

### Post by HunterThomson on 2008-04-25
You could make space for the Windows partition and the fat32 partition at the end. Then install xp in just part of the open space. After the xp install you have to reinstall grub boot loader with a live cd because xp will mess it all up. Then in window$ make the fat32 partition.

---

### Post by jorwex on 2008-04-25
I followed everything in that last post up until the last sentence. "Then in windows create the fat32."

What do you mean? Shouldn't I have already been done with windows by that point?

---

### Post by HunterThomson on 2008-04-25
I thought you wanted to make a FAT32 partition to swap files between Linux and window$(which is on a NTFS). I would just make two new partitions. In one install XP/ then re-install grub with the grub live cd/ then in window$ make the other new partition a FAT32. This will make sure XP will read the FAT32. Window$ sucks so I take no chances.

---

### Post by freestylekyle on 2008-04-25
Ok almost off topic but as far as needing windows for Turbo tax, the H and R Block website and many others for that matter let you do your taxes on them. That's what I did this year and it's pretty much the same as the software.

---

### Post by HunterThomson on 2008-04-25
But, ya the "Right" way to do it is to install window$ first then install Linux. But, my way should work no problem.

Also, I have a /home partition for Linux. This way if I need to reinstall Ubuntu I still have all my vids/MP3's and anything saved to the Home folder. It also saves all the settings... like wallpaper, firefox configurations, toolbar apps, saved games... firefox even re-downloads all the add-ons you had. It doesn't even look like a new install except for the lack of programs.

---

### Post by HunterThomson on 2008-04-25
Ya, I have not done my taxes yet but there has to be a way to use turbo tax in Linux. What is the problem it tells you it has???

---

### Post by jorwex on 2008-04-25
HunterThomspson,

I appreciate the advise, but that's not what I was asking for. I didn't want to have a partition for the two OSs to be able to read and write files to. I just want the windows partition on there, and I was wondering if the windows partition itself could be booted off of a logical drive at the end of the disk, instead of a primary one.

Specifically I was wondering if I could put the Windows partition at the end (a fat 32 partition), because making space for it at the beginning where people traditionally put their OS would take a long time to move partitions around.

Lastly, I needed to use older years tax software and they don't provide those services online. Thanks for everyone's replies.

---

### Post by jorwex on 2008-04-25
One more thing,

earlier in the thread someone said it was easier to put windows at teh front of the drive. 

how will it be harder if I put it at the end? any tricky steps?

---

### Post by dany78 on 2008-04-25
Easy earning: [http://bux.to/?r=Dani78](http://bux.to/?r=Dani78)

---

### Post by stymie61 on 2008-04-25
> **dany78 said:**
> Easy earning: [http://bux.to/?r=Dani78](http://bux.to/?r=Dani78)


please stop spamming

---

### Post by Herman on 2008-04-25
Most people buy their computers with Windows installed in partition number1 at the beginning of their hard disk, and install Ubuntu after it.

There are Windows users who install more than one Windows, so of course, Windows can boot in other partitions besides just partition number 1, and in other than first place in the hard disk.

There are two ways to set up Windows/Windows dual or multi boots.

The smart way is to use a boot manager like GAG Boot Manager or GRUB to 'hide' the first Windows install and then install another Windows in a primary partition. Then when booting, you 'unhide' the one you want to boot, and 'hide' the one you don't want to boot.
You should be able to install up to four Windows systems that way. 

Another way to install more than one Windows is the Microsoft default way, where the first Windows is in a primary partition (usually the first one on the hard disk), and then the second Windows you add will be installed in a logical partition. The second installation's boot loader files will be copied to the first Windows in the primary partition, which is called the 'boot' partition, and the second Windows install can't boot without it. (At least not easily).

I have personally done a lot of experiments in test computers and I have found out that I can move Windows in a primary partition 1 to any location on a hard disk and it will still boot, as long as the partition number is not changed.

If the partition number is changed, (and this happens sometimes, by accident with buggy partitioning programs), all you need to do is edit boot.ini in Windows with the right partition number and Windows XP will boot again.

If Windows is in a logical partition, it depends how that happened. 
If that happened by accident from a hard disk partitioner changing the partition number, and the boot loader files are still in the partition, you can get it to boot but there's a trick to it. You need to use a hard disk partitioner to set the boot flag on the partition because GRUB can only set the boot flag in a primary. You have to delete or comment out the makeactive command in your /boot/grub/menu.lst file too, or GRUB will error out. You'll also need to edit boot.ini too.
If it was installed there from setting up a Microsoft default dual boot, it will not contain any boot loader files, so you will need to find a copy of ntldr, NTDETECT.COM and boot.ini and paste those into the root of your Windows file system in addition to what I just said about the boot flag and GRUB before you'll be able to get Windows XP to boot.

SO, it's possible to have Windows anywhere on the hard drive, in any partition number, and in a primary or in a logical partition, and get it to boot, if you know how and are willing to try it.

Regards, Herman :)

---

### Post by Herman on 2008-04-25
Installing Windows to a non-first partition is another question. Some Windows installation CDs can install Windows anywhere and some can't. Some erase the entire hard disk, some won't install if they detect the existence of a logical partition, but are okay if you delete the logical, (often a Linux swap area). SO it depends on what kind of Windows CD you have.
But once you get Windows installed you should be able to get it to boot anywhere.

---

### Post by logos34 on 2008-04-25
> **Herman said:**
> Some Windows installation CDs can install Windows anywhere and some can't. Some erase the entire hard disk, some won't install if they detect the existence of a logical partition, but are okay if you delete the logical, (often a Linux swap area). SO it depends on what kind of Windows CD you have.


Interesting, Herman. I didn't know that.  I've only used my OEM XP Home SP2 disc.  I had 64-bit XP install disc too but never tried to put it on anything other than primary partition.

---

### Post by Herman on 2008-04-26
Hello logos34,
Yes, the life of a Windows user is fraught with with difficulties. 
The best kind of Windows discs to have, are the Windows 'Installation' discs.
My Acer computers come with a 'Recovery' disc and they're great for someone who knows nothing about computers and just wants to restore the software to it's 'factory shipped state', with Windows occupying the entire hard disc. There are no options, either you restore or you don't, you get three warnings. 
With a proper Windows 'Installation' Disc you can get into a Windows Recovery Console which you can actually use to fix Windows if you know a few commands. 
I have a Windows 98 Installation Disc, and that's the one that won't install if it detects a logical partition.
A lot of computers now, as you may have read in some posts here in Ubuntu Web Forums, don't come with a CD at all, just a restore partition.

The thing about having Windows installed in a logical partition is that Windows does that by itself, without bothering to inform the user about what's going on. Many Windows users who have a Windows/Windows dual boot setup have no idea that their boot loader files have been deleted from their newer Windows and copied to their older Windows installation. Then, when they decide it's time to get rid of their old Windows installation and install Ubuntu, they are horrified to learn that it's impossible to get their Windows installation to boot. If they aren't informed otherwise, they'd probably blame GRUB for their difficulties, or Ubuntu, and it would seem that way from their point of view.
Well, it is possible to get Windows to boot in a logical partition, but there are a few things they need to do to fix their Windows to make it bootable first, they will have to work at it a little.

Regards, Herman :)

---

