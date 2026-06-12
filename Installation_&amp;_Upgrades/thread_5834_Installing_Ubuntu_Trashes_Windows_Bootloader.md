---
title: "Installing Ubuntu Trashes Windows Bootloader"
date: 2004-11-22
forum: Installation &amp; Upgrades
---

### Post by jdong on 2004-11-22
This is a general problem with Linux 2.6.x

---

### Post by talkingwires on 2004-11-22
Hey -
I've been using Ubuntu for about a month now, and have enjoyed it until two days ago. I was preparing to install Half-life 2 (!!!), so I tried to boot up Windows, only to have Grub echo Window's menu.lst entry and freeze. I hadn't gone into Windows in over a week, but the only thing I'd really done system-wise was the usual "sudo apt-get update && apt-get upgrade" After trying several approaches, I gave up and wiped my Windows partition and started from scratch.

Once everything was up and running, I reinstalled Ununtu. Image my surprise when I had the same problem: Grub spits out "title Windows XP norootverify chainloader +1" or something to that effect and just sits there.

Does anyone have a clue what could be causing this? I'm not reinstalling Ubuntu anymore if it's just going to wipe out Windows again...

---

### Post by jdong on 2004-11-22
Linux 2.6 CHS geometry issues... an **sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda --force** will most likely fix it.

---

### Post by talkingwires on 2004-11-22
Um, is this a problem with a specific kernel / bootloader that I can just avoid? Will running those commands fix it, or can I look foward to experiencing this problem on a regular basis?

---

### Post by dorris on 2004-11-23
also experienced similiar problems, I got fed up with trying a million fixes that didn't work, as said above, Its a drive geometry/clash with bios settings, and the way it reads the drives, grubs setup, does a little trashing to the windows boot sector,
there is a way to recover it available, I can't remember the source, but google : "chainloader XP grub" and you'll find it.

me personally, I wasn't in the mood for fixes, just pulled out the old ghost image, then reloaded ubuntu!
some pointers, try change bios from auto/chs HDD mode to LBA or large.
it works for some users, but not many, if that fails, a sure way is to reinstall windows, followed by ubuntu, just ensure before the format, that your bios is NOT using CHS/Auto!
for the last 2 weeks, its been working great.

---

### Post by plasmo on 2004-11-23
same goes here. normally i would just turn the bios hard drive to LBA and yeah it 
would just work. install windows first then ubuntu. all goes fine

---

### Post by darrell on 2004-11-23
[QUOTE=talkingwires]Um, is this a problem with a specific kernel / bootloader that I can just avoid? Will running those commands fix it, or can I look foward to experiencing this problem on a regular basis?[/QUOTE]

It's not a problem with the bootloader, it's a problem with the partitioning software/kernel interacting differently with the bios's idea of disk geometry.

The bottom line is that once fixed, only repartitioning will (possibly) screw it up. I learnt about all this the hard way, so if anyone wants, I could document in detail what I found out, including ntfs resizing issues.

darrell

---

### Post by talkingwires on 2004-11-26
[QUOTE=darrell]It's not a problem with the bootloader, it's a problem with the partitioning software/kernel interacting differently with the bios's idea of disk geometry.

The bottom line is that once fixed, only repartitioning will (possibly) screw it up. I learnt about all this the hard way, so if anyone wants, I could document in detail what I found out, including ntfs resizing issues.

darrell[/QUOTE]
Okay. One more question: are the commands jdong posted the best way to fix the problem, or would it be switching the BIOS over to using LBA for my harddrive? I ask because installing Ubuntu to run the commands will wipe out Windows again, and the version of Knoppix I have burned has questionable NTFS support.

---

### Post by darrell on 2004-11-27
[QUOTE=talkingwires]Okay. One more question: are the commands jdong posted the best way to fix the problem, or would it be switching the BIOS over to using LBA for my harddrive? I ask because installing Ubuntu to run the commands will wipe out Windows again, and the version of Knoppix I have burned has questionable NTFS support.[/QUOTE]
 I think that setting LBA on in your bios can't harm, and may avoid the problem in the first place, but it seems, is not guaranteed to.

What is your current starting point? Is it a working windows partition which fills the whole disk?

What do you mean by "the version of Knoppix I have burned has questionable NTFS support"?

darrell

---

### Post by talkingwires on 2004-11-28
[QUOTE=darrell]I think that setting LBA on in your bios can't harm, and may avoid the problem in the first place, but it seems, is not guaranteed to.

What is your current starting point? Is it a working windows partition which fills the whole disk?

What do you mean by "the version of Knoppix I have burned has questionable NTFS support"?

darrell[/QUOTE]
Well, I recovered my partitions: I have an NTFS partition, a shared FAT32 partition that takes up most of my disk, and a Linux/swap partition. My partitions are set up the way I want them, and Ubuntu ran fine for over a month before the issue started popping up. A clean install of Ubuntu is still in its respective partition, but since installing Grub wreaks havok on my Windows partition, I can't boot it...

Oh, and the copy of Knoppix I have burned is something like a 3.1 pre-release. It may have NTFS support, but it's such an old version that I doubt it works very well.

---

### Post by HungSquirrel on 2004-11-29
Any particular reason why the initial post of this thread appears below one of the replies to it?   :shock:

---

### Post by darrell on 2004-11-29
When you say "but since installing Grub wreaks havok on my Windows partition, I can't boot it..." does this mean when you try to install grub as part of the ubuntu installation process?

If this is the case. I am thinking it is that the rewriting of the partition table during the ubuntu install process is what is causing the problem, rather than the actual installing of grub. What I suggest you do is:

1. Boot your knoppix cd

2. Make a backup of your existing (windows-generated) Master Boot Record (MBR):
**dd if=/dev/hda of=/choose/some/path/mbr-backup bs=512 count=1**
you might want to do this twice, once putting the backup somewhere on your hard disk, and again putting it on a floppy, just in case.

2. at a command prompt, type grub

3. at the grub prompt, type **find /boot/grub/stage1**
this should find your ubuntu grub config file and report:
(hdx,y) - x is the disk number, starting from 0, y is the partition number, starting from 0

4. still at the grub prompt, type **root (hdx,y)** (using x and y from the output of the find command above)
and then
**setup (hd0)**

5. remove the knoppix cd and reboot. see if both windows and ubuntu works. Repost here if you don't see options for both operating systems on the grub menu.

6. If there are any problems, you can reboot into knoppix, and put things back to how they were by restoring your backup of the MBR:
**dd if=/where/you/put/it/mbr-backup of=/dev/hda bs=512 count=1**
type this very carefully, dd is a very powerful command, and you could trash your disk if you make a mistake in the above command. In particular, make sure the numbers (which mean 1 block of 512 bytes) are correct.

---

### Post by Magneto on 2004-11-29
if the kernel ubuntu ships with and the grub update they put into circulation dont play nice why hasnt the bug been submitted/addressed?
Grub was upgraded for me in hoary the other day but I don't use the horrible debian style kernels and my xp install is fine

Another note for all ubuntu users is- do not apt-get dist-upgrade for updates if you have no problems with your systems and take a look at what's going to be installed and why and whether or not its worth it.
In fact, if you have a stable system only enable security  main in your sources.list

Darren- someone earlier had success with running setup from the grub commandline within ubuntu too - people are over-reacting with all this blowing away of systems/partitions etc 

 
sudo grub

grub>

---

### Post by jdong on 2004-11-29
umm, does this thread look REALLY messed up??

---

### Post by Magneto on 2004-11-29
[QUOTE=jdong]umm, does this thread look REALLY messed up??[/QUOTE]
 only cuz of your super moderator thread stealing post at the top ;)

maybe grub messed up the thread, better rebuild the server 

:)

---

### Post by talkingwires on 2004-12-03
Sorry I haven't replied. I've been away for a while, and never got to try your suggestion, Darrell. Anyway, I followed your instructions, and got it working. Thanks!

---

### Post by jdong on 2004-12-03
[QUOTE=Magneto]only cuz of your super moderator thread stealing post at the top ;)

maybe grub messed up the thread, better rebuild the server 

:)[/QUOTE]
yep... blame everything on me! yay, fun.

---

### Post by Dreamsmith on 2004-12-23
[QUOTE=jdong]Linux 2.6 CHS geometry issues... an **sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda --force** will most likely fix it.[/QUOTE]

Phew!  I just had this problem, and thought I had trashed Windows XP completely, but booting my handy LNX-BBC and issuing the above command fixed it so Windows could boot again.

Shouldn't Ubuntu's installer warn you when your current partition map's geometry is completely different from the geometry it's about to write to the disk?  It doesn't seem like this would be a difficult situation to detect, and it sure would save a lot of heartache (I tried Windows XP's recovery options first, so although I didn't lose anything, I did spend a couple hours essentially reinstalling Windows (which didn't fix anything) before finding the proper fix).  Heck, if it had just showed me a little more detail about the partition map it was about to write I'd have known instantly to abort the whole thing, it was obviously messed up.  (Not saying you should necessarily display that detail, just noting how bloody obvious this problem is -- it shouldn't be that hard for the installer to detect.)

BTW: Now that I've issued that command, and restored the old geometry, will Ubuntu still function alright?

---

