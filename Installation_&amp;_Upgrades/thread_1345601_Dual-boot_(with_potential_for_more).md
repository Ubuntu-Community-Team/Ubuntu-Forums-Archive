---
title: "Dual-boot (with potential for more)"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Narusegawa on 2009-12-04
I find the most confusing part of installing is bootloader and partitioning unfortunately.

At the moment I have 3 physical sata drives.

1) Windows 7 (partition0) + Data (partition1)
2) Windows Page File (partition0) + MP3's (partition1)
3) Blank, new

I'd like to dual-boot Windows 7 with Ubuntu to start with. Later on I'll be adding possibly more OS's (maybe more Window's ones due to career) I've seen some advice against GRUB2 saying it pretty much doesn't let you configure much yourself and is bad for more than 2 OS's, so thought I'd add that here, but I would like to use it if it can do what I want.

Can GRUB2 work okay with multiple OS's?

Should I make a /boot seperately so that other OS's don't splat it.

If install GRUB to drive 3 (into a /boot) do I need to change the boot order of my drives (I suspect I do) to put drive 3 first?

How can I then chainload from drive 3 back to drive 1 for Windows 7? (Do I also need to change BCD malarky to keep the nt bootloader working)

At some point I may need to re-install Win7 but doing so will override the MBR, I'd like to set this up to minimize problems with doing that.

Thanks in advance!

---

### Post by darkod on 2009-12-04
As far as I've seen grub2 is working just fine. There are moments where you have to tweak or custom adjust but usually with strange kind of setups.

More or less you answered all your questions in a correct way.
Yes, put drive3 first in boot order before starting to install ubuntu (and grub2 with it). On the last screen of the install, before clicking Install, click on Advanced button and check where is it suggesting to install grub2. Make sure it's the ubuntu drive. Previously on step 4, the partitioning step, make sure you note which drive is which, for example drive3 might be /dev/sdc as you expect but it might not be, Ubuntu might order the drives differently. It's not a problem, just make sure you note how is drive3 called and on the last step in Advanced options make sure grub2 is installed there.
No need for separate /boot partition. In fact, it's usually better not to have it unless you specifically need it.
If you re-install win7 it would usually put the windows bootloader on it's own disk so grub2 should not be destroyed. But to make sure, you can put disk1 first in boot order before reinstalling win7 and it should put the bootloader there. Then switch the order back to drive3. And after you reinstall even if grub2 is not deleted, you will need to run the update-grub command because the win7 drive will likely be formatted again and with new info. But that's nothing to worry about, lets not invent problems before they happen :)

---

### Post by Narusegawa on 2009-12-04
Thanks. The only reason I considered a /boot was in the event I had another distro installed aswell, I didn't want to have to start maintaining 2 sets of grub. But thinking about it, aslong as the one on the ubuntu drive can point to the kernel on the other... it should be okay anyway.

I just wanted to make sure before I screwed things up. :)

Will Grub2 find the Win7 by itself?

I think the only think I need to look at now is how to change that BCD stuff once I change the boot order.


Edit: Actually thinking about this... I might move the Data from drive 1 to drive 3, and use that space for Ubuntu instead. Therefore keeping both OS's on a single drive.

---

### Post by audiomick on 2009-12-04
Apart from the Ubuntu documentation:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

this just turned up in the "General Help" section of the forum:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

I have no idea how good it is, but at first glance it looks great.

---

### Post by darkod on 2009-12-04
Yes, grub2 finds win7 even on different drive.
And as far as another distro is concerned, you will not have to maintain two grubs, you just instruct in advanced options when installing the second distro not to install bootloader. Then you just update ubuntu grub2 which should also find the other distro automatically.
If you have separate /boot and you use it for two distros you can actually get into trouble sometimes because not always they use same principle.

I'm not sure about what BCD stuff you are talking about? You leave the windows bootloader alone and boot with grub2 once you have ubuntu installed too. Windows can't see it by default, it can with special procedures but why do that when you have grub2 which can boot both.

---

### Post by oldfred on 2009-12-04
I have always liked the idea of an operating system on every drive and that operating system set up in the MBR of that drive. 

Since Ubuntu/grub easily finds other operating systems I make it the first drive in BIOS so it boots and finds the other systems. If I ever have a problem with that drive I can switch drive order and still boot. If all the operating systems are on one drive, then if that drive fails the only way to boot is a liveCD or bootable USB (which I also have just incase;)).

---

### Post by Narusegawa on 2009-12-07
I had a huge amount of problems with GRUB, it wouldn't find any partitions inside an extended partition once it rebooted.

I originally had this (I don't have exact gb sizes but you get the idea), oh and (pri) means Primary partition.

```

24gb Win7 (Pri)
| Extended Partition begins
|4gb SWAP 
|50gb Ext3 /
|150gb NTFS Data

```

It would only show hd(0) and hd(0,1) in grub's rescue mode ls command, and would give me "no such partition" when booting up. Only a LiveCD could be booted at this point. Several tries with the help of #ubuntu and no-one could get this working or figure why it wouldn't see past hd(0,1). So I did my own thing below based on oldskool knowledge hehe

Although I've been told to not use a /boot seperately as thats a bit oldskool. I had to.

In the end I had this and it works a treat now. It took gparted the better part of a day to re-arrange my partitions and data, and I know a 1gb /boot is a lot, but I figured I'd rather be safe than run out of space.

```

1gb ext2 /boot (Pri)
24gb Win7 (Pri)
4gb SWAP (Pri)
50gb Ext3 / (Pri)
| Extended Partition begins
|150gb NTFS Data

```

I am getting a new drive this week and the 150gb NTFS partition is being moved over to that at which point I can extended the ext3 partition to the end of the drive (to the right, so should be easy right?)

---

