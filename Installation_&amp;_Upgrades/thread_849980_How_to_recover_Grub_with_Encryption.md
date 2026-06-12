---
title: "How to recover Grub with Encryption"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Margus81 on 2008-07-05
I made the default disc encryption install with ubuntu alternate CD. I do not have the live cd.

I do not know suddenly grub sais error 17.

I can go to repair mode with the cd, but to reinstall grub I have to do partition...

Partition manager says I do not have a root mount point...

I do not know what I can to, that I keep all the data. 

The installer asks me for the password, and then I can even use command line...
so I can change directories and see my Home folder...

So the system understands everything, I don#t know why cant I simply repair Grub...

---

### Post by Herman on 2008-07-05
First, is there anything unusual you can remember happening just before you began getting GRUB Error 17?
There are lots of different ways you can get GRUB Error 17, and one or two of them are adding a new hard disk or switching your hard disks around in your BIOS.
So, sometimes you can cure GRUB Error 17 by plugging your hard disks in again (into different SATA ports maybe, or if they're IDE, change the jumper settings, or by changing the hard disk boot priority in the BIOS.
You might not need to do anything inside the operating system if you are lucky.

If that doesn't work, I have a link here to some instructions that can help you use the Live CD to gain access to your encrypted system. 
Ubuntu Geek: [Rescue an encrypted LUKS LVM volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html").
Probably the same thing would also work from a USB Ubuntu installation or Ubuntu installed in another partition if you only have the 'Alternate' CD, or maybe if you're skilled enough, you might be able to adapt those instructions for use with the 'Alternate' CD. (I'm only guessing that might work, I haven't tried it).
> The installer asks me for the password, and then I can even use command line...
so I can change directories and see my Home folder...Oh, maybe I'm wrong and you already have access to all your files?


Here are a couple more links that might help you, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") (rescue your Linux system with a Live CD), and [Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17").

I hope something there will help you, I hope you can use those links to help you repair your GRUB or at least rescue all your data.

EDIT: Maybe it just needs a file system check, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem"), that sometimes solves GRUB Error 17.

Regards, Herman :)

---

### Post by Margus81 on 2008-07-05
Thank You, Herman! You are a wonderful person!

>First, is there anything unusual you can remember happening just before >you began getting GRUB Error 17?

I think only this could have caused that:

I DO have always a backup on my USB Stick, which is Truecrypt encrypted.
But I needed it to share files with a friend of mine.

So I tried to format it to fat32.

sudo umount /dev/sdb1
sudo mkfs.vfat /dev/sdb1

sdb1 has to be the USB, because it comes when I put it in, and also Truecrypt says it, when I want to do device encryption.

After the command nothing happened actually! The USB wasn't formatted and I could still mount it with TC. 

But the computer worked just fine. I shut it down, went to the friend and formatted the USB-stick.

After coming back - surprise - grub error 17.

...
<Ubuntu Geek: Rescue an encrypted LUKS LVM volume.

thank you! That saved my data. I went to a friend, burnt the live cd.

After that I could start experimenting...

>
>Quote:
>The installer asks me for the password, and then I can even use command >line...
>so I can change directories and see my Home folder...
>Oh, maybe I'm wrong and you already have access to all your files?

Yes, when I inserted the alternate cd, and chose recover broken system, it asked for the password and mounted the encrypted volume.
Then I had to choose the root mount point (or something like that)
and I could "Launch Shell"

I didn't know what to do there...but I could wonder around my disc and see the files...

>Here are a couple more links that might help you, Mount a Ubuntu ext3 or >reiserfs filesystem (rescue your Linux system with a Live CD), and Grub >error 17.

Thank you! I tried to recover Grub, but no good... I am sure, it was a minor issue, but too complicated for me. It gave error 15 then... After searching the file...

I think the unencrypted disc was messed up...cause the 
sudo e2fsck -C0 -p -f -v /dev/sda2

said it was so small the partition, nothing to check. It asked, I am sure I use it...


So I though I could get away with reinstalling the base system. I repartitioned the unencrypted partition and tried to reinstall the base system. But just before the end, I gave me linux kernel error.

So I changed the filesystem to ext2...then, heck with it. 

Reinstalled whole linux. And restored the data I saved earlier.

Thanks!

---

