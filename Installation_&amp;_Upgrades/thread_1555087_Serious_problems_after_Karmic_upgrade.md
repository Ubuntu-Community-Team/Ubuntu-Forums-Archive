---
title: "Serious problems after Karmic upgrade"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Mandala 13 on 2010-08-17
Hi,

I have been using Ubuntu for a while now, always looking for the distro that would work best with my old laptop. Hardy, for instance, makes everything work but with low performance. Intrepid, the same with a bit more performance. Jaunty, with excellent performance but with no sound at all. And Karmic, with even better performance, but with no wireless.

But after experimenting some problems with Intrepid, which I was using, I decided that I might as well try fixing the wireless problem in Karmic. So, this past days I have been upgrading and trying to make it work. At the end, I had three problems:

1- Wireless worked randomly. I end up using Wicd and in Hardware Drivers, it show Madwifi as activated even when there was no Madwifi at all (I compiled and then unistalll it 'cause it didn't work at all). 
2- Wired internet didn't work all the time and it was pretty much as random as the wireless, but with more chances.
3- Even when I have 3 distros and their discs that work and are shown in other computers (for intrepid, Jaunty and Karmic) none of them loaded in my computer.

The point was that after all these problems, I thought that maybe I was better off with Intrepid after all. But I couldn't find the chance to install it because, as point 3 said, discs really didn't loaded as if there was nothing at all. But I really needed to format the computer 'cause I need it for work so in a wave of frustration and anger (Yeap, that's me, anger against my "creation", lol) installed gparted and was playing with it while being inside Karmic. I thought that there was no chance that I would be able to do anything at all because I needed to use some live cd for unmounting and formatting any partition at all. Well, I was wrong.

What happened, I'm not sure. But as far as I know, the Gparted was formatting the computer even while being on the same partition that was being formatted. I absolutely freak out and end the process that was in any case crashed. Then, kept on doing my things and reboot. Now, this is what shows:

The filesystem size (according to superblock) is 466882 blocks.
The physical size of the device is 4626712 blocks.
Either the superblock or the partition table is likely to be corrumpt!

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

Ok, I know what that means. And it should be fixed by resizing the partition. But the problem is that as far as I know and have tried, you can't resize a partition that's mounted. And I can't mounted if it's the only one and you're working with it. fsck, after a long time, sends a message that problems isn't fixed. And, as ever before, I can't make a disc to load and try to simply wipe things out and start anew. I have tried with the Intrepid disc and the Jaunty one, with no avail, even if another computer can actually show me it's well burn. 

So, Basically, I'm going mad. I have no idea how to fix this problems and I'm even thinking seriously to either try using a Windows disc to see if I can format and install Windows and then Ubuntu again. Or simply buying a new hardrive, which I really can't.

I would really appreciate any kinda help you could give me. And I would give you any kinda information you would need, as far as I know (or ask) how to get it, lol. By the way, computer is Toshiba Satellite M45 S169. And right now using Ubuntu 9.10, kernel 2.6.31-22-generic-pae (that I was using for the wireless). I also have the 28-19, and 27-7, but logically none of them makes any difference.

What I want is actually not fixing the problem itself. I have my backup and all. What I want is to be able to simply load the installation discs of any other distro to simply install something new and forget about this whole problem...

Anyway that's going to be possible?

Any help would be deeply and afterlife appreciated.

Edit: I was playing with the fdisk -n options, to try and format the whole drives so I would have a brand new computer that would load installation discs, but it was saying that (obviosly) it was busy and couldn't. Well, I keep trying to see if there was anything that I could do. And well, now I reboot and says that:

Operating System not found.

Ok, so as far as I understand, my computer has nothing at all right now. But well, the problem now is that it won't load the installation discs that I have no. Not Jaunty, or Intrepid or Karmic load... So... I think that I'm worst than before... Damn me tinkering with options... Any help would work :D

---

### Post by mörgæs on 2010-08-20
Whoa, that was a long post. 

As for your question of another distro: I would go for Knoppix. Since you have a backup, just wipe the entire drive, partitions and all. 

You are not mentioning Ubuntu 10.04. Have you tried installing this?

---

