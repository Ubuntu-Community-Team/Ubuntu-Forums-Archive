---
title: "Grub not installing?"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by DerangedDingo on 2007-04-05
Sorry... maybe this has been answered but I did a quick search and found nothing. I've installed Ubuntu easily before on other computers, but on this particular one, everything goes fine, but then grub isn't there, it just goes straight to windows. The hard drive configuration is two Sata 2 drives set in nVidia STRIPE... so it's two drives working as one.

If I boot from the Live CD, the Ubuntu loading screen is gray and all messed up, and when I open GPartEd it shows that all the necessary partitions are there, with information written to them. 

What's up? I've tried installing before and I had the same problem. The first time I used the x86 version, and now I'm using the AMD64 version (we have a dual core AMD 64 Athlon)

Why won't grub appear to let me load Ubuntu? And what's with the load screen? (it's not my graphics card that's doing that... I think)

---

### Post by Herman on 2007-04-05
Hello DerangedDingo,
See if Grub went to the MBR on the second hard disk instead of the first by trying to get a  list of bootable devices to boot from. You should be able to do that with either your F8 or F12 key when your computer is in the early stages of booting.
Yours will be different most likely, but here's how I do that,   [How I boot from my BIOS with my F12 key (or F8 key in most PCs)]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key")

Regards, Herman :)

---

### Post by DerangedDingo on 2007-04-06
No luck.
Just the same results as there would be if I hadn't have installed ubuntu. And if it was going to appear on the boot menu I would have noticed much earlier and set it to default in the BIOS because I have to enter the boot menu any time I want to boot from the CD. It doesn't recognize that either.

Should I change the drive I'm installing it to? It defaults at hd,0 and I didn't bother changing that  in any of the installations. Or should I just manually install GRUB from the Terminal? Any help would be appreciated, I'd love to see how Beryl and Ubuntu run on this system.

PS: Are there other recommended bootloaders that *might* work?

---

### Post by Herman on 2007-04-06
> Are there other recommended bootloaders that *might* work? Yes, in times of difficulties or just for playing around with bootloaders, the tool of choice is [Super Grub Disk.]("http://supergrub.forjamari.linex.org/") That can do more different jobs for you than anything else, including booting your Ubuntu installation even when there are no grub files in it at all. Use Gnu/Linux --> Boot Linux Directly if Ubuntu is in your first hard disk. If Ubuntu is in your second hard disk you can do much the same thing but go to the advanced menus and do it, that way you'll be given a list of hard disks to choose from.
You can also boot a non-first MBR in 'Boot & Tools'-->'Boot Master Boot Record', in Super Grub Disk.

(hd0) is always the best location to install Grub's IPL to in my opinion, but other hard disk's MBRs can be useful as well. I also like to install bootloaders to the first sectors of their partitions too. Why waste a chance to install a bootloader somewhere? I prefer Lilo in the bootsectors though, just to be different. But that's getting away from the main topic.
Just let Grub go to any MBR it likes, as long as you can boot up somehow. (With Super Grub Disk maybe). Then you can re-install Grub later to another MBR if you want to.

You should check in your CMOS (or BIOS if you prefer to call it that), and make sure there are no 'write protect' features or 'antivirus' for the MBR turned on. Turn those off for a while if any of those are on. Actually I don't think you need them for Linux anyway, I'm not sure.     [Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect")

Regards, Herman :)

---

### Post by zvacet on 2007-04-06
[http://ubuntuforums.org/showthread.php?t=401472]("http://ubuntuforums.org/showthread.php?t=401472")
Instead of hd0 you can place grub on your second HD.

---

### Post by DerangedDingo on 2007-04-06
OK, I'll try Super Grub Disk... and I'm trying to download the floppy version.. but for some reason... I can't!! Am I an idiot? Every time I click on it it opens a blank page but doesn't show the little firefox download window...arggg.
There we go. Tried a different mirror.
Oh sweet irony. The floppy has 1.38 mb of space and the image is 1.4 mb...
Let us try a CDRom.
Ok. Good job Infra Recorder.
Ok, so I booted and it, after navigating through to Boot Grub or whatever it was (it's 3:22 gimme a break) it said error 15 file not found sorry :(
I rebooted and navigated to automatically restore grub, and I had chosen already to my hard disk, and it said the same error 15 message.
I hope this narrows it down.. I'm gonna do a bit of searching.

EDIT: OK. Now this is even worse. When I boot from the LiveCD it isn't even recognizing my drive with all of the partitions on it (GPartEd isn't). I asked on another forum and got a response from a very Ubuntu savvy person. He noted that GRUB may have corrupted my partition table, and that that is the reason that GPartEd ignores the drive totally. He said I could use FDISK to recreate a new partition table and save it, so that GPartEd would recognize the drive again.

I hope this works. I guess this computer is forever destined to an eternity of Windows...

---

### Post by DerangedDingo on 2007-04-06
Sorry for bump but I need some help. Where can I get FDisk for Windows XP? It isn't included standard and the download's I've seen for Super FDisk are only demo downloads and don't let me restore the partition table

---

### Post by Herman on 2007-04-06
Sorry, rethinking....
Quoted from your original post,
> The hard drive configuration is two Sata 2 drives set in nVidia STRIPE... so it's two drives working as one. I think that's where your problems may have started. I need to find out more about nVidia STRIPE before I can help you. That sounds like a type of RAID setup. You need help from someone who knows about that.

Okay, I'm still thinking about this. It would be nice if you had provided the link to that other thread in another forum, where you got that other advice.

I don't know anything about RAID or nvidia STRIP, but Grub doesn't normally corrupt anyone's partition tables, it installs its first stage. also called the 'IPL' for the bootloader in the first 446 bytes of the master boot record. The next 64 bytes of the Master Boot Record are the four 16 byte entries of the partition table. Although grub does move the boot flag, that's about the only thing Grub normally touches in the partition table. You can have Grub 'hide' or 'unhide' a partition, but you need to tell Grub to do so with commands. It doesn't do that by itself.

GParted and most other partitioners are fairly sensitive, and it isn't so uncommon for them to refuse to look at a partition table if there's something on there they don't agree with, or weren't made for. That doesn't always mean your partition table is fatally corrupted. Many times if one partitioner doesn't recognize it, another one will. You could try sudo fdisk -lu from the Ubuntu LiveCD and see what that shows. ```
sudo fdisk -lu
```You can restore the bootloader 'IPL' area of your MBR with a Windows 98 boot floppy, I think that's probably what you really mean, you can do fdisk /mbr from a Windows 98-SE boot floppy.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)
That's for restoring your IPL for the Windows XP bootloader, NTLDR though, not for the partition table.

I would be extremely cautious about touching the partition table at all unless you are really, really sure have to. I don't think that's the part of the MBR you need to work on.

Regards, Herman

---

### Post by Neobuntu on 2007-04-06
Did you add a GRUB splashimage?

If so, make sure the "splashimage=" line in menu.lst is seeing/matching the splash file.

Remove the splash.xpm.gz file from /boot/grub if the splashimage line is commented or missing from menu.lst.

I've notice a blank, blank GRUB otherwise.

If run sudo update-grub, you can see if it "sees" the splash file.

---

### Post by DerangedDingo on 2007-04-07
OK
Here's the full story, and I figured it all out. It was actually very simple.
We had two 3 drives plugged in. Two 160 gigs set to Nvidia Stripe. That totaled at 300 gigs.
And a third drive from an old computer with all of my information/games, etc that my father had popped in and plugged in but never configured or enabled in the BIOS. It was also 300 gigs.

SO....
Every time I tried installing Ubuntu it was only installing it to the third drive.
It wouldn't, and never did, recognize the stripe drive, just the individual drives. And since the third one was also 300 gigs it was hard to tell.
Because it was never enabled in the BIOS, of course it wouldn't boot GRUB, grub was installed on a drive that wasn't being used.

SOO... When I was fiddling with our floppy drive, it wouldn't lock, popped back, and we had to open the case and try and pop it back into its spot.
During this, my dad decided to unplug the spare drive (it wasn't being used, right?)
Because of this, when I continued my Ubuntu endeavor, the partitioner stopped seeing the drive. (Because it was unplugged)

So, we just enabled it and formatted it.. and installed the driver and stuff.
Phew. Imagine what woulda happened if I had decided to mess with the Stripe drive... when no problem was there.
Thanks anyway guys.
This forum is very active... responsive.
I gotta get some sleep.

---

