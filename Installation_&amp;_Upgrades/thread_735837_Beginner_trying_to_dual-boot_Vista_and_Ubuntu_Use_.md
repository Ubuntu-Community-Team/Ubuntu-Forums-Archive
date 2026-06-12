---
title: "Beginner trying to dual-boot Vista and Ubuntu? Use &quot;Recovery&quot; partition?"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by ubuntogenius on 2008-03-26
I have a PC running Vista with a "Recovery" partition on the drive, approx 6 gigs of space on the partition. I want to install Ubuntu on there. I don't need much space, as it's only for testing purposes.

The recovery is for HP (not sure if that makes a difference), but is it OK for me to format this partition? Could this mess up any other files on the other (main) partition?

Also, when I install Ubuntu, will it install grub as my boot-loader? Is the rest of the setup relatively straightforward? I want Vista to still me the primary OS, but want the option to boot into Ubuntu.

Let me know if more info is needed. Many thanks!

---

### Post by deleyd on 2008-03-26
I would leave the HP recovery partition alone. (I would also make one of those DVD recovery backup discs, which HP has a program somewhere that lets you make ONE recovery DWD (which actually takes 2 DVDs)

I installed Ubuntu on my HP laptop a few months ago. Let's see if I can remember anything useful. There was a post that warned not to install whatever the current version was a few months ago (was it version 7?) on an HP 9000 series or 6000 series computer. So I went and installed the beta of whatever the next version was. Anyway, it was a sticky post for awhile, maybe do a search for it if you're installing on a HP.

Then, I was told to get the free trial download of PerfectDisk ([www.perfectdisk.com](www.perfectdisk.com)) and run that to defragment the hard drive. I recall I selected the setting that consolidates the free space. This was an important step, as this program was able to move things around so the next step would be successful.

Then I could Shrink the Partition. Control panel, Administrative Tools, Computer Management, Disk Management, right-click on drive C:, and select "Shrink Volume". I told it to shrink it by 10GB (which is probably more than I needed.)

Then I was ready to install Ubuntu. Put Ubuntu on a CD and got it going (somehow). I recall there was a step where I had to tell it to "use the largest free space" (something like that) when it asked where should it put Ubuntu. I recall being a bit nervous, as it didn't explicitly show me the 10 GB free space I had created, and I think I chickened out and tried a few other ways, but eventually decided I didn't know enough how to do it manually, so I reran it and selected "use the largest free space" (something like that) and it worked just fine.

Ubuntu installed it's boot loader (is it called Grub?). The default was to boot into Ubuntu unless I explicitly told it to boot into Windows Vista instead at the beginning of the boot process.

I wanted to have the computer on boot default to Windows Vista, and only boot Ubuntu when I explicitly said to at the beginning of the boot sequence.

I recall there was a file somewhere I had to edit, a file related to Grub, and I changed a number from 1 to I think 4. When you first turn on the computer, you get the Ubuntu (or Grub?) menu, listing all the possible choices of boot, and you've got 10 seconds to decide, else it boots into the default. Ubuntu was the top, a few debug versions were below, and Vista was the 4th (I recall wondering if I should count the blank line, and I think it turned out that yes, you do count the blank line, so 4 instead of 1 is the number you want.

Here's a scrap note I found about this:
You can set grub to boot into Vista by default by working out the number of Vista in the boot menu. The first item in the boot list is 0, second is 1, etc etc. The 'Other Operating Systems' line should be included in the count. Then you need to open the boot config file (in Ubuntu):

Code:
gksudo gedit /boot/grub/menu.lst
And changing the 'default' line from zero, to whichever number Vista is. (4)

I recommend you stop here, and don't continue and do what I did, which was to
install EasyBCD.

I read about EasyBCD and how wonderful it was. Not quite sure what it did or
how it worked, but installed it anyway.

   1. Booted into Windows Vista.
   2. Installed EasyBCD
   3. In EasyBCD, went to "Manage Bootloader", and told it to "Reinstall the Vista Bootloader", because I'm an* idiot!*

Vista boots fine, but Linux will no longer boot.

Searched the internet for information on how to reinstall GRUB bootloader, which Ubuntu had installed. Looked complicated. Decided to ask Geoff the expert for some advice. (Also a good excuse to stop working on this for today.)

Geoff said just reinstall Ubuntu all over again, which I did, and that fixed things.

Anyway, final outcome is on booting computer, I get a 10 second count down to select if I want to boot Vista or Ubuntu, and if I do nothing it boots into Vista.

---

