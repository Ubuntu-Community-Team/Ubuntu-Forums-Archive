---
title: "GRUB error 18"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by shak022 on 2007-06-05
I was using my dell laptop as usual, and when I booted today I was stuck with GRUB error 18, right out of the blue. I read up on this and it seems my bios is unable to access a kernel on some part of my hard drive, or my hard drive is too big for my BIOS. I don't understand why this came up all of a sudden though.

I tried using the super grub bootdisk, but that didn't help any. I also read some stuff about setting my BIOS to auto or lba, but my dell bios has neither of those options. It appears the only solution is to create a partition at the begining of my hard drive and setup my boot files there, but I have absolutely no idea on how to do this. Would anyone be kind enough as to walk me through the solution?

---

### Post by Herman on 2007-06-06
Hello shak022, 
Some grub error numbers are always caused by one and only one specific problems and are simple to cure without any more troubleshooting.
Grub error 18 is one of those errors that can seem mysterious and hard to determine.
It seems particularly mystifying that it could occur all of a sudden in any computer during normal use and without any unusual events or operations having preceded it.

If you can show some more information about your computer like the output from 'sudo fdisk -lu' and a copy of the bottom portion of your menu.lst file it might or might not help give someone a clue where to begin to try to help you.
You should be able to get that information by running a Ubuntu Live CD or any Live CD.
I think it's likely that even more testing than that will be needed. What is your BIOS version? [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information").

I'm not sure if creating a separate /boot partition will help in your case, that was for old computers with the 8.0 GB hard drive limit, it helps sometimes, but it isn't a cure-all solution, unfortunately. You can try it if you want. 
I recommend [GParted -- LiveCD]("http://gparted.sourceforge.net/") for all partitioning work. You should download one of those and burn it to disc. You could use that to make a small partition at the start of your hard disk. Then you would copy your /boot directory to that and edit /etc/fstab accordingly.  More likely it will turn out to be some kind of a BIOS problem or even a minor hardware related problem though, I am just guessing.

Regards, Herman

---

### Post by shak022 on 2007-06-07
Thanks for your reply Herman.

It looks the problem is more serious.. I ran GParted but it was unable to detect the hard drive at all. I then ran geometry (hd0) from the grub command line, it printed out the partitions but was unable to to identify the filesystems. Finally, I took out the hard drive and placed it into an enclosure. It powered, but the computer was unable to load the external drive. Occasionally, the hard drive also 'clicks' while in the enclosure.

I'm rather worried now, I think I threw everything at it, including Ultimate Boot CD. Any tips on recovering the data before I have to get it examined by a professional service would be greatly appreciated.

---

### Post by Herman on 2007-06-07
For a home PC user who has data that isn't too valuable, doing it yourself for free is a much more attractive proposition than having to pay someone possibly a lot of money to recover your data.
If you use your computer for business, your data could be a lot more important. It still might be worth trying to recover it yourself. It would save time and a small amount of money, ('small' compared with what your data might be worth, which is something only you can guess).  
Before continuing you should remember that, generally speaking, the less the disc is interfered with now, the more chance your data can be recovered professionally if you decide to go that route. 
That depends on what exactly is wrong with it though. If it's just a simple MBR problem, it can be fixed easily yourself with TestDisk as long as your file system blocks are still okay. 
If it's a physical problem though, like a collapsed bearing, I would worry about any possibility of more physical damage being done to the disk surface.  
Then again, on the other hand it seems to me most likely that whatever damage can be done would already have been done by now anyway. 
I will leave it to you to make those judgements, but I feel it's my duty mention those things just to make sure you are aware, although probably you already know that. 

I have a web page under construction showing one or two examples of what it's like using TestDisk to recover a lost partition. 
You could read about TestDisk at it's  home site first and take a  look at my illustrations if you like.
 
Here's the Link for [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk"), and there is [PhotoRec - CG Security]("http://www.cgsecurity.org/wiki/PhotoRec"),  as well but I haven't tried that one yet myself.

Here's the link for the page I made, [TestDisk Page]("http://users.bigpond.net.au/hermanzone/TestDisk%20How-To.html"), 
*This link will work at the time of this thread being active but actually I only upload this page when it's wanted so if the link doesn't work some day in the future, just PM me and I will fix it.*

I hope something there will help you, good luck,
Regards, Herman

---

### Post by shak022 on 2007-06-09
Thanks for the tips. I really like the page you setup, it details everything step-by-step for a noob like me ;D
So I tried running testdisk off my GParted CD, and TestDisk was unable to see the hard drive at all. It picked up some /dev/hdc (around 50mb) which I'm guessing is the reserved dell partition for diagnostics/recovery. It's kind of strange because the hard drive must be readable, since GRUB attempts to load and spits out the error. Any idea why TestDisk doesn't see it?

Would burning a sole TestDisk bootcd be of any help? (I was wondering how TestDisk would see the drive, when GParted couldn't)

BTW, It might also be worth nothing that the hard drive makes a staticky, pulse-like "ching" noise while in the enclosure every 30 secs or so.

---

### Post by Herman on 2007-06-09
Well what we take for granted every day we use our computers is really quite an achievement in precision engineering and electronics. We keep forgetting that it's a whole series of technological near-miracles that enable us to even perform the most basic tasks with a hard disk, and with other parts of our computers as well. It  only takes one or two tiny problems and the whole series of miracles it takes to do our daily work come crashing down like a house of cards.
[IMG]http://users.bigpond.net.au/hermanzone/p6/DSCF0473.png[/IMG]


The hard disk spins at 7200rpm or so, and the tiny read/write heads on the ends of the actuator arms need to be able to be positioned accurately over the tracks containing the sectors you want to read by precision electronics. The controller card underneath the hard disk contains the firmware, and is really like a small computer itself, just to control the hard disk and make it be able to talk to the rest of the computer. Scott Mueller's book, [Upgrading    and Repairing PCs]("http://www.quepublishing.com/promotion/1626") has a lot of fascinating information about hard disks, and probably you would find lots of other sources of information as well. Hard disks are really interesting things. 
I had a hard disk failure one time and I suspect a plain old fashioned bearing failure as the cause of the problem because there was an oily stain under the sticker covering the spindle bearing. Almost anything can cause a hard disk to stop functioning normally, it could be a failure of the actuator coil, or something more exotic inside the firmware in the controller card. 
So it's hard to say why you might be able to get Grub, but not the rest of the hard disk. If you can get Grub up, you should be able to still read quite a bit of your hard disk. Grub reads your partition table, which is in the first sector, and the next part of Grub, called stage1_5 lives in the next 15 sectors of the first track of you hard disk. 

According to the [Gnu/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html"), some error messages can come from Grub's stage1 ,in the MBR, [Stage1 errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors"), and some can come from the stage1_5, [Stage1.5 errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors"). 
Stage1_5 errors share the same error numbers and meanings as stage2 errors, so* if you had Grub error 18 without seeing your Grub menu*, it might only mean your first track is readable.  
If you do see your Grub menu first, *and then get Grub error 18*,  that would tend to indicate that possibly at least half of your hard disk is still working pretty well!
Your Grub menu comes from your Grub's main part, stage2, and your /boot/grub/menu.lst file, which lives in the Ubuntu partition somewhere else on your hard disk.  :)
What happens when you press your 'c' key from your Grub menu and try out some of these commands,[                                                                         How to get GRUB's Command Line to investigate a computer]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer"). Maybe you can 'cat' a plain text file or two with Grub.

GParted is probably looking at the partition table and is often pretty finicky about whether it likes what it sees. Sometimes it will refuse to show you anything at all if it detects something it doesn't like. I presume that is to protect you from a possible disaster if it tries to do something with a previously corrupted partition table. The partition table can easily be corrupted by using a different kind of partitioning software on it that isn't 'Parted based.   TestDisk works the other way around, TestDisk looks all over the hard disk for boot sectors and file system superblocks and can write the position or co-ordinates of those those back to the partition table if you tell it to. Burning a special CD with just TestDisk on it wouldn't likely be any help at all though, I wouldn't imagine.
Grub's error 18 is not a very good indicator to rely on, but if TestDisk can't see your start blocks for your partitions either then I don't know what else you can do. Knoppix has 'gpart', which is a bit like TestDisk, you can use that for a second opinion, you can start that by typing 'gpart' in a Knoppix terminal. I don't have much experience with 'gpart'.
Regards, Herman

---

### Post by Herman on 2007-06-09
Something else interesting about whether GParted chooses to show me an graphical representation of my partition table or not has to do with whether the disk is plugged in to my computer or plugged into a USB enclosure.

I can have a hard drive in my laptop which GParted will be quite happy with, and remove the hard drive from my laptop and place it in a USB enclosure, and GParted will refuse to have anything to do with it. 
Fdisk will still see it but it will give me a message something  like 'the last partition finishes past the end of the disk', or something like that. The disk could still be mounted and all the files were still accessible, but GParted completely ignored it.
Then I can put the same hard disk back into my laptop and GParted will be quite happy with it again.

I guess this has to do with whether it is seen as an IDE hard drive or SCSI. When it is plugged into the laptop it's an IDE disk and when it's plugged into the USB firmware it's seen as an SCSI disk, coming up in GParted as 'sda' rather than 'hda'.
I have  one here now out of my laptop with Ubuntu installations in it that was invisible to GParted but now it's okay. I forget how I did that. Maybe I ran experiments on it with TestDisk and that fixed it. Otherwise I would need to set a new disk label in it with GParted to get GParted to 'see' it and and re-format the disk with new file systems.
I just though I should mention that. So it is perfectly normal for your hard disk from your laptop not to show up in GParted while it's in an external USB enclosure.
It isn't normal for it to be making those bad noises though.
Regards, Herman :D

---

