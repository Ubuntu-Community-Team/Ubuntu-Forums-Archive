---
title: "[SOLVED] Installing &amp;quot;standalone&amp;quot; GRUB"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by grazanaut on 2008-08-05
I want to know if it's possible, and if so, how, to install GRUB standalone without installing any flavor of Ubuntu or Linux (for example using grub-install from the LiveCD?).

What I'd like the outcome here to be is:
- grub installed in MBR
- first partition (small "boot" partition) to contain any other files required by grub (such as menu.lst)
- grub having no reliance whatsoever on other partitions/installations existing (obviously aside from an OS needing to be there if I choose to boot it from the menu)

I currently only have a clean WinXP installation, and I'm hoping this would let me add new OSes (by installing OR imaging) to partitions, or remove OSes (by deleting entire partitions), without preventing Grub from booting. If I delete a partition, I'm hoping that the only result is that I'd need to edit the menu.lst file to remove the OS from Grub's menu, likewise if I add an OS. Even better if it were possible to put this on a Fat16 partition so the files could be edited from either a Linux or Windows OS (with a *nix-friendly text editor of course).

Is this doable?

Many thanks....

---

### Post by mattduckman on 2008-08-05
this is interesting, it should be possible, but i'm not really sure.

if you start a ubuntu live cd, and then start up a terminal, there should be a command called grub-install that you can use. read the [man page]("http://linux.die.net/man/8/grub-install") first.

the thing you do need that's not a part of your scenario is a partition to house /boot on it. you need to create it, mount it, and use ```
grub-install --root-directory=*/mount/point install_device*
```

as i said i'm not sure if this is really all you need to do, you should get more information before you attempt it.

---

### Post by dstew on 2008-08-05
You can definitely do this. The easiest way might be to do a regular Ubuntu installation, with a small /boot partition. Usually, the installation puts the operating system kernel files in this partition, as well as the /boot/grub directory with contains grub's stage2 and menu.lst files.

Once you have done this, you can re-install Ubuntu, but ignore the /boot partition (do not delete it, just don't use it for the installation). At the end of the installation, on the Advanced tab, select the option *not* to install grub. Then, edit the menu.lst file in your old /boot partition grub directory to add the new operating system menu item.

There might be a way with Ubuntu installations to use grub-install or update-grub to automatically update the menu.lst file, but I don't know for sure. These commands are run from a linux OS command line. I don't know what effect they might have on your grub boot partition though. I do know that the grub menu.lst file is created to be scanned by update-grub, and re-created to incorporate a new OS, or a new kernel. I am not sure how exactly to run it if grub is in its own partition.

---

### Post by Herman on 2008-08-05
:) GRUB is (or can be) completely 'operating system independant', if you make a separate small partition for GRUB create a /boot directory in it (optional), and copy your /boot/grub directory into that partition.
Then just install GRUB from that partition to MBR.

This link should help,
[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").-  contains only GRUB, no other files  are required.

You don't need the Linux kernel or any other files from your operating system's  /boot directory, just /boot/grub.
This way you're making a 'dedicated GRUB partition'. GRUB is almost a miniature operating system itself, it doesn't need any Linux kernel. You can copy a Linux kernel and initrd.img there too if you want, but those wouldn't normally be needed for a 'Dedicated GRUB partition'
. 
If you're making a 'Separate /boot Partition', then you would want the Linux kernel and other associated files, and would register the partition as /boot in /etc/fstab. Then it becomes part of an operating system though.
I suppose a 'Separate /boot Partition' would effectively become a 'Dedicated GRUB Partition' if the rest of the operating system was deleted.

You can edit the /boot/grub/menu.lst in your 'Dedicated GRUB Partition' in any way you like.
Probably you would delete the /boot/grub/menu.lst operating system entries which boot your operating systems kernel directly, and replace those with stanzas using either the chainloader or configfile commands instead.
Here's a link about that,  [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
The reason for not using the 'kernel' command (direct booting stanzas) anymore is because your 'Dedicated GRUB' is no longer under the control of the operating system's update-grub script, so the menu.lst file won't be updated when you have a new kernel.
However, you still have your original menu.lst in your operating system, so you only need to relay the boot through the 'Dedicated GRUB' to your boot loader in any operating system.

All the previous posters are correct too, but I just wanted to add my opinions to the subject as well.

---

### Post by maybeway36 on 2008-08-05
I like to use GRUB4DOS as a standalone bootloader. You just put grldr in the root directory of the boot partition and run
```
sudo ./bootlace.com /dev/hda (Linux)
bootlace.com 0x80 (DOS)
```

---

### Post by grazanaut on 2008-08-05
OK, so something I'm having a little trouble comprehending is the idea of /boot as it applies to Grub

My understanding is that Grub is like a mini operating system in itself, which is responsible for booting other OSes. So what I'm confused about, is whether the /boot as Grub sees it has to be the same /boot as the OS sees it?

My understanding of what I'm being told here may be incorrect, so please clarify if I'm mistaken, but it seems that if I have a separate partition (/boot) with grub installed, I have two options:
1) also install the kernel for each OS in the same partition, or
2) otherwise grub can only be used to chain other instances of grub (which exist in each *nix OS partition to boot that particular OS)

If this is correct, then would I be correct in thinking that the /boot partition that Grub sees *needs* to be the same as the OS /boot partition unless that OS has its own bootloader?
If this is the case, what exactly in /boot does grub need access to? If it's only /boot/grub, could I mount or create a symlink for the /boot/grub path in all my OSes to this folder in the grub partition, and only have this folder physically existing in Grub, or something similar?

I'm hoping I'd only need one instance of grub installed, to simplify matters & avoid any confusion with config, etc, though if this isn't possible without the kernels for the various distributions being in my boot partition, it seems the most hassle-free, or more to the point most "segregated" method would be (2) as above, a totally separate "multi-boot-configured" grub, chained to multiple instances of "single-boot-grubs" which exist in the partition for that particular OS and boot nothing but the OS on that partition.

As someone who's toyed with Linux distributions for a number of years, I must say, I'm still 100% noob, especially now that I've found a distribution I actually like enough to put a lot of thought into the best way to install it for my own purposes.....

Hopefully what I'm trying to achieve is as clear as it can be now. I must admit that wanting to install it this way is largely influenced by my past experiences with using BootMagic for multiple Windows installs, which installs itself 100% independently of other OSes on a separate partition, which I really liked...(though on reflection I've realised that each OS that BootMagic booted must have had it's own bootloader on the partition it was installed on - however in the case of Windows which was hidden from other Windows installations, the bootloader was mostly transparent or un-noticeable). The two  main things I liked being that 1) if I installed the BootMagic config tool on any given OS, it would always look to (and write to) ithe boot partition for settings, and 2) if I killed an OS/partition, BootMagic wouldn't complain unless I tried to select the now non-existent OS - and this is what I would hope to be able to do with Grub.

---

### Post by grazanaut on 2008-08-05
Re-reading this post, I think I understand a bit better now:

> **Herman said:**
> :) GRUB is (or can be) completely 'operating system independant', if you make a separate small partition for GRUB create a /boot directory in it (optional), and copy your /boot/grub directory into that partition.
Then just install GRUB from that partition to MBR.

I'm guessing that if I wanted to start out with Grub only booting Windows (i.e. not having any Linux distro to begin with) that I could boot using the Ubuntu LiveCD and copy the /boot/grub directory from the OS that the LiveCD loads?

> **Herman said:**
> The reason for not using the 'kernel' command (direct booting stanzas) anymore is because your 'Dedicated GRUB' is no longer under the control of the operating system's update-grub script, so the menu.lst file won't be updated when you have a new kernel.
However, you still have your original menu.lst in your operating system, so you only need to relay the boot through the 'Dedicated GRUB' to your boot loader in any operating system

On re-reading, I think makes more sense to me now, and I'm assuming that this means I would definitely be best to use this "standalone" grub to chainload other grubs, otherwise I'd need to manually re-configure it every time there was a kernal update?

--> A side question here... I'm assuming that the updates that I'm notified of from time to time (much like the Windows updates) do occasionally update the kernel, and thus would automatically reconfigure grub?

---

### Post by Herman on 2008-08-06
> On re-reading, I think makes more sense to me now, and I'm assuming that this means I would definitely be best to use this "standalone" grub to chainload other grubs, otherwise I'd need to manually re-configure it every time there was a kernal update?

--> A side question here... I'm assuming that the updates that I'm notified of from time to time (much like the Windows updates) do occasionally update the kernel, and thus would automatically reconfigure grub?
:) The standard default installation of Ubuntu will give you about the best arrangement and will suit most people and their computers. The default installation is what I use and recommend for most people. Ubuntu is already just about perfect, there's no need to go changing things. (Unless you want to for fun and learning).
Ubuntu is normally (best) installed in one integral root  (/ ) partition, and GRUB lives in a directory called /boot/grub. The Linux kernel and initrd.img files live in /boot.
Ubuntu uses GNU/GRUB version 0.97 (last time I checked it did anyway), and there are scripts which are unique to Debian based Linux distributions for automating the changes that should be made during a kernel update.
It's pretty hard to think of anything better than the standard Ubuntu install that we're already given automatically. Greater minds than mine have put a lot of thought into it and they have certainly done a great job, in my opinion.

:) There is a thing called a 'Seperate /boot Partition', which contains all the files that would normally be found in the /boot directory, except instead of just being a directory, it's a separate partition. The 'Seperate /boot Partition' contains the Linux kernel(s) and initrd.img(s) and is part of the operating system. It is registered in the operating system's /etc/fstab file. It behaves in most respects the same as a /boot directory except it's a partition. Partitions are fixed in size and position on the hard disk.
The most common reason someone might need a 'Separate /boot Partition', is when they have an older computer and they have a hard drive BIOS limit. The 'Separate /boot Partition' forces the Linux kernel to be located in an area of the hard disk which the BIOS can address. If not, they might be lucky and the kernel might just happen to be installed within the BIOS limit, or it might happen to be located outside the limit and they won't be able to boot the operating system, they'll get GRUB Error 18.
Another reason we might need a 'Separate /boot Partition' is when we install Ubuntu in a LUKS Encrypted file system, (the files are all encrypted except for the /boot partition).

:)  A 'Dedicated GRUB Partition' is something extra you can make if you want to. It has nothing much to do with Ubuntu really, and it's something completely separate and independant from any operating system.
A 'Dedicated GRUB Partition' just has GRUB files in it. You can put a kernel and initrd.img file in there and use it to boot an operating system if you want to, but strickly speaking that's necessary.
'Dedicated GRUB Partitions' are useful for GRUB enthusiasts to play with GRUB, and for people who want to multiple boot many Linux installations. If you have a lot of hard disks with a lot of Linux installations, your GRUB menu might get too crowded. You might want to have a 'Dedicated GRUB Partition' with options to go to GRUB in the first hard disk, second hard disk, third hard disk and so on. From the next GRUB menu you might have a selection of OSes on the same hard disk.
It's also easy to delete and re-install operating systems, because when we delete and operating system it might otherwise be the one which contains GRUB, and therefore we'll temporarily lose our ability to boot up the rest of the OSes. With a 'Dedicated GRUB Partition' we can delete any OS and still boot the others.
Windows users who wanted to install more than one Windows were able to use GRUB in a 'Dedicated GRUB Partition' too. GRUB has the ability to 'hide' and 'unhide' primary partitions, so instead of letting Windows set up a 'default Microsoft dual boot', you can install and boot more then one Windows independantly.
If people who are dual booting Windows and Linux have a 'Dedicated GRUB Partition' then they can safely delete Linux and still continue to boot Windows via GRUB.
GRUB enthusiasts who want to play with GRUB and have fun with it might want a 'Dedicated GRUB Partition', for playing with and learning more about what we can do with GRUB.

The main disadvantage of having a 'Dedicated GRUB Partition' is it adds an extra step to booting up. First you get your GRUB menu from your menu.lst in your 'Dedicated GRUB Partition', then you see the bootloader menu in whichever operating system you choose from there. You still need GRUB or LiLo to boot most Linux systems, and Windows alsways needs it's own boot loader, depending on which Windows you have.

I still don't think I've really answered your questions well at all. Maybe the best way to understand is to just go ahead and install and create a 'Dedicated GRUB Partition' too and try it out for yourself.

Regards, Herman :)

---

### Post by grazanaut on 2008-08-07
> **Herman said:**
> :) The standard default installation of Ubuntu will give you about the best arrangement and will suit most people and their computers.
<snip>
:) There is a thing called a 'Seperate /boot Partition', which contains all the files that would normally be found in the /boot directory
<snip>
:)  A 'Dedicated GRUB Partition' is something extra you can make if you want to. It has nothing much to do with Ubuntu really, and it's something completely separate and independant from any operating system.
<snip>
I still don't think I've really answered your questions well at all. Maybe the best way to understand is to just go ahead and install and create a 'Dedicated GRUB Partition' too and try it out for yourself.

Regards, Herman :)

No, you have answered most of my questions (bar one, see the last paragraph in this post). Your last post almost looks like something from a book/manual/userguide :)

As far as the three main points you made, because I intend to have at least 2 installations of Ubuntu as well as 2 of Windows (I like to have a separate Windows install kept nice and clean for music production, and intend to do likewise with Ubuntu, using the Ubuntu Studio distribution), as well as testing out (then most likely wiping) other distributions, I definitely want a Dedicated Grub Partition - one that will let me boot the remaining OSes I have installed, regardless of whether I zap one of them.

I don't see much of an issue having to go through an "additional step" of the second grub menu (the one installed in each separate OS partition) as for the most part I'll only have one option there (as I'll hide OSes from each other), and set it with a 1 second default choice.

So... the question I now have, which is probably a dumb one (but hey, the "Absolute Beginner Talk" is read-only...) is:

I'll need a /boot/grub folder on the dedicated partition, and I'll need to configure Grub's root to this partition. I would assume that the secondary installs of Grub wouldn't "carry" this information through, and that once the first Grub chainloads the second, the second will be able to set the *actual* root for the OS it is booting? (i.e. to the partition containing the OS).

---

### Post by Herman on 2008-08-07
> I'll need a /boot/grub folder on the dedicated partition, and I'll need to configure Grub's root to this partition.:)  Yes, when you install GRUB from that partition to MBR in your first hard disk, there are three classic commands you use to install GRUB with the GRUB shell, 'find', 'root', and 'setup',  [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"). 
You would type the GRUB designation for your dedicated GRUB partition after the 'root' command, if that's what you mean then yes, that's right.
Or use mattduckman's command, that looks to me like it should work okay, and might be the quickest way to do it.
> I would assume that the secondary installs of Grub wouldn't "carry" this information through, and that once the first Grub chainloads the second, the second will be able to set the *actual* root for the OS it is booting? (i.e. to the partition containing the OS).Each installation has it's own /boot/grub/menu.lst file, which is the configuration file for that operating system's own GRUB.

When you 'chainload' another operating system, be it Windows or another Linux OS with GRUB or LiLo, GRUB hands over the control of the boot process the boot loader installed in the boot sector of the given partition. From that point on, the booting is under the control of the other operating system's boot loader.

The other command used for booting a different Linux is the 'configfile' command, but we can only boot another Linux that also uses GRUB as the boot loader in this way. The first GRUB (GRUB in the Dedicated GRUB Partition), will do the actual booting, but it reads the /boot/grub/menu.lst in the operating system to be booted to find out what to do. 

The root file system for the operating system that will be booted will be set in the boot stanza for that operating system in the /boot/grub/menu.lst file.

You can boot any Linux operating system with the direct kernel boot command too if you want, it's just that you would need to keep on manually updating the boot stanza every time there's a kernel update and that would be a pain in the neck. You could boot 'directly' by the symlinks instead though, if you wanted to.

> Your last post almost looks like something from a book/manual/userguide:lolflag: He-he, sorry about that, I was on a time limit.
> I'm guessing that if I wanted to start out with Grub only booting Windows (i.e. not having any Linux distro to begin with) that I could boot using the Ubuntu LiveCD and copy the /boot/grub directory from the OS that the LiveCD loads? Not really because thee LiveCD boots from syslinux, it has a /boot directory but it doesn't have grub in that directory. It does have GRUB as a program though, in /usr/sbin.

Actually, mattduckman's command looks to me like it might be a better way of doing this than what I have originally suggested. I think that might be worth a try.
I might need to update my website. :)

---

### Post by grazanaut on 2008-08-08
Thanks for the help, all.

Using *ideas* from replies to this thread, and *specifics* from the link in Herman's first post ([How to make a dedicated GRUB partition ]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") - by the way, I should have read this more carefully right at the start, very helpful, thanks heaps), and of course the  [Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html"), I've installed grub without Linux, on a hard drive only containing a freshly installed WinXP (with a heap of space from additional partitions).

I had an old Ubuntu installation on an external hard drive (the new drive is in fact replacing the old, now external drive), which I intend to clone to the new drive as one of my OS choices at some point, but at this point was useful to copy the /boot/grub files from. All done using the LiveCD :)

By the way, the Grub partition is a Fat16 one - no problems at all there, and very nice if I need to edit menu.lst from Windows (keeping in mind CRLF/LF differences of course).

Needed to edit boot.ini in Windows as for some reason installing Grub to the MBR & Fat16 partition changed the numbering of partitions as used by Windows bootloader. I have no idea why this happened, as the Fat16 partition was already there, so Windows shouldn't have decided that partitions had different numbers.... but due to this, I also decided to add partitions 1,2,3,4,5 (some of which don't exist yet) to boot.ini so if it happens again, I can try a partition number other than the default, without needing to do any editing (other than changing the default once I discover the new correct partition number).

Have also cloned another Windows XP install (from my old drive) to a new partition (using dd), and added it to menu.lst. I still have a bit of work to do here, as when I choose that partition it simply states "starting up..." and freezes - doesn't look like one of the common errors with boot.ini (hal.dll not found, etc), haven't got to the bottom of it yet, perhaps the cloning didn't properly copy the boot sector, or I need to revisit the partition numbering used by Grub (for some reason LiveCD calls this THIRD primary partition /dev/hda4, but its physically the third partition, so not sure whether it should be (hd0,2) or (hd0,3)......)

Anyone else who's cloned Windows onto a partition from another drive and booted with Grub, feel free to give pointers :)

---

### Post by Herman on 2008-08-08
> Needed to edit boot.ini in Windows as for some reason installing Grub to the MBR & Fat16 partition changed the numbering of partitions as used by Windows bootloader. I have no idea why this happened, as the Fat16 partition was already there, so Windows shouldn't have decided that partitions had different numbers.... but due to this, I also decided to add partitions 1,2,3,4,5 (some of which don't exist yet) to boot.ini so if it happens again, I can try a partition number other than the default, without needing to do any editing (other than changing the default once I discover the new correct partition number).:confused: Installing GRUB to MBR has never ever caused partition numbers to be changed for me in all the time I have been using Linux! Maybe something in Windows did that. It's interesting to me because this type of thing does happen once in a blue moon and it would be nice to know exactly how and why, and if it can be done on purpose. It would be nice to learn how to control partition numbering. If the partition nyumbers can be changed accidentally then surely there should be some way of changing them back again, but I haven't seen any easy way to do that yet. I know a slow way of doing it, but it's so slow it isn't worth it. :)
Anyhow, that's a very good idea of yours to make some extra lines in your .boot.ini file. 

I'm glad you have been successful and are having fun with GRUB. :)

I don't know very much about cloning Windows from other hard drives, I'm not sure if that's an easy thing to do or not. 
What I can tell you is how to convert between partition numbers and GRUB's notation, here's a link to a conversion table, [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").
> for some reason LiveCD calls this THIRD primary partition /dev/hda4, but its physically the third partition, so not sure whether it should be (hd0,2) or (hd0,3)......) Probably it should be hd0,3). I'm not sure why but it must be your fourth primary partition, do you have an extended partition there anywhere? Maybe that would account for the 'missing' partition number?

If you want to boot two Windows in the same hard drive, you will probably need GRUB's 'hide' and 'unhide' commands, if they are both to be in primary partitions. [More than one Windows on the same disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk")
So maybe your will be something like:
```
title     Microsoft Windows 
hide      (hd0,3)
unhide    (hd0,1)
root      (hd0,1)
savedefault
makeactive
chainloader +1

title      Microsoft Windows 
unhide     (hd0,3)
hide       (hd0,1)
root       (hd0,3)
savedefault
makeactive
chainloader +1
```I only guessed your first Windows might be (hd0,1), which would be your second partition, feel free to change that number if I guessed wrong.

Regards, Herman :)

---

### Post by grazanaut on 2008-08-18
Thanks everyone, all sorted now. A few clarifications on what happened with Windows and partition numbers being changed.

The Live CD (eg with fdisk -l) never thought partition numbers had changed after I installed Grub to the MBR, only Windows had. I think it was because I had added the small Fat16 partition to the start of the drive. After doing that with GParted, nothing changed in Windows, I assume because however Windows was booting originally (does it boot from 1st Active or MBR by default?), GParted left untouched (or perhaps modified accordingly to ensure the original partition was still seen as 1).

I guess after installing Grub, the way in which *Windows* numbers its partitions (or perhaps the way it checks the partition "signatures"?) was interrupted and it renumbered them, hence I needed to modify boot.ini.

Turned out to be a similar problem with the cloned XP installation - an adjustment to boot.ini, trial and error to find the right partition number (as *Windows* sees it). Interestingly enough, after getting this working, then cloning Ubuntu onto the next partition, Windows went and renumbered partitions *again*. Aargh. I'm glad I added all those extra lines to boot.ini, something I'll be doing in these multiboot situations from now on.

I've managed to clone an older Ubuntu installation onto another partition and now have it chainloading (after a bit of fun learning about how to do this and editing fstab... that is, after *learning* a lot :) ), so I now have XP(Fresh), XP(Old/Cloned) and Ubuntu(Cloned) successfully installed and booting.

---

### Post by grazanaut on 2008-08-18
> **grazanaut said:**
> I guess after installing Grub, the way in which *Windows* numbers its partitions (or perhaps the way it checks the partition "signatures"?) was interrupted and it renumbered them, hence I needed to modify boot.ini.


Actually, [_THIS_]("http://www.mail-archive.com/bug-grub@gnu.org/msg10666.html") page describes how a change to the MBR Serial Number value will force Windows to re-enumerate the partitions it knows about. Installing Grub to the MBR would have the same effect.

Interestingly, it comes from the other angle, that is, times when you would *want* Windows to re-enumerate partitions, for example if you boot Windows just once with a partition unhidden that you really wanted to be hidden, Windows will remember this partition, even if you later hide it... forcing a re-enumeration (once the partition has been hidden again), is the only way to force Windows to truly "forget" that the partition existed (hence the only way to hide it properly)...

---

### Post by Herman on 2008-08-19
Grub doesn't overwrite the MBR's 'disk signature'.

---

### Post by grazanaut on 2008-08-19
Hmm. Then I really don't know what was happening. Windows must have detected that *something* had changed, and thus re-enumerated partitions. Perhaps part of what Windows uses as a "signature" it stores in the registry includes other information in the MBR, or a copy of the MBR itself...not sure??

No dramas, I guess my point is that *something* that happened when installing Grub to the MBR triggered a re-enumeration of partition numbers within Windows. And as I had added a new partition to the start of the disk, this changed the partition number (from Windows' perspective) that Windows itself was installed on.

Still don't know exactly what caused it, but IMO that's a moot point as we do know what the "symptoms" were, and how to solve it.

---

### Post by Herman on 2008-08-19
> Needed to edit boot.ini in Windows as for some reason installing Grub to the MBR & Fat16 partition changed the numbering of partitions as used by Windows bootloader. I have no idea why this happened, as the Fat16 partition was already there, so Windows shouldn't have decided that partitions had different numbers....:) I am just guessing, but I think it's more likely that you were right the first time, Windows might have detected the partition having a FAT16 file system and that might have triggered something in Windows. I don't know for sure, it might be interesting to experiment with that and confirm whether that would be probable or not. Windows usually assumes the user is an idiot and it thinks it knows better and will run programs automatically without bothering to inform the user. 
It is an interesting subject. :)

---

