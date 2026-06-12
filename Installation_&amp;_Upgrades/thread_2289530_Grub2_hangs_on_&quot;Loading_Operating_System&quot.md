---
title: "Grub2 hangs on &quot;Loading Operating System&quot; on new install"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by kdx7214 on 2015-08-04
This machine was an existing machine that I upgraded to 15.04 a month or two ago and it had run fine until yesterday.   Had to reboot (building maintenance was going to have the power out) and when I tried to bring it back up it hung with "Loading Operating System".   I posted on AskUbuntu but nothing there helped.   So I decided to go ahead and wipe the whole machine.    Used dd to clear the partition tables of all 3 drives (dd if=/dev/zero of=/dev/sd? bs=512 count=64) and then tried a two partition installation 256gb root and 8gb swap).   On reboot it still refuses to load.   Weird thing is I can boot from CD or from USB and the drive is there and responding just fine.  I tried boot-repair with no change.

Anyone have any ideas?  I'm completely stuck.

---

### Post by yancek on 2015-08-04
Boot repair has an option to Create Bootinfo summary.  Try running that and posting the output here and someone may have a suggestion for you.

---

### Post by kdx7214 on 2015-08-04
Here is the one I did earlier (before I wiped everything):

[http://paste.ubuntu.com/12001379/](http://paste.ubuntu.com/12001379/)

---

### Post by oldfred on 2015-08-05
You did not post that you erased everything & reinstalled & it still does not work.
[http://askubuntu.com/questions/656249/grub-2-giving-loading-operating-system-and-then-hanging](http://askubuntu.com/questions/656249/grub-2-giving-loading-operating-system-and-then-hanging)

What brand/model system or what motherboard & specs?

---

### Post by kdx7214 on 2015-08-05
Hey @Oldfred I just tried the wipe before I posted that.   Checking out the links you provided right now.  The mobo is a Gigabyte GA-A75M-S2V running an AMD A6-3650 with 8GB ram and running non-UEFI mode.  Has 3 HDs that are setup for AHCI operation (not hot swap though).   Previously had them as an LVM hosting MythTV.   (I asked about this system on AskUbuntu and you were the only responder there :) )

@Oldfred also, sorry about double posting - did not know that askubuntu and ubuntuforums were the same site.  Kinda frustrating.  Plus, cannot figure out how to "close" the previous thread.

Okay, read through both links.   This system has never had Windows on it (just linux in various incarnations).   Still using BIOS.   Does have onboard AMD graphics + NVidia video card (need the OpenCL support for video decoding).   The nomodeset would seem to be irrelevant.  If it was just video mode then the system would continue to boot.   I can't ssh into the machine, no network activity, just hung at "Loading Operating System".  I did try the nomodeset as mentioned in the previous thread but it made no difference.  I have also tried disabling AHCI mode for the drives to no avail.   Tried noacpi (or is it noapic, can't recall atm) and same result.   Completely confused at this point - used linux since Slackware 0.21 back in '94 and never seen something like this.

---

### Post by oldfred on 2015-08-05
Ubuntu Forums & askUbuntu are not the same. In fact those of us here are a bit upset with Ubuntu as its installer has been recommending askUbuntu, but Ubuntu actually owns and supports the Forums. AskUbuntu is a totally separate site by StackExchange.  I just happen to post there sometimes.

I do prefer Ubuntu Forums but that may be as that is where I started finding good info and posting.

I do not know mixed AMD & nVidia. Normally we do see Intel & nVidia. 
Can you select which video you use when booting? Or are they totally separate and you just plug into one or the other as separate video ports?

Generally you want AHCI on. The old IDE was only for old drive PATA/IDE drives.

Did you update BIOS? That changes settings back to defaults. I had to take pictures so I could remember all the changes. My new Asus motherboard lets me take screen shots inside the UEFI.

Most with newer Gigabyte have this issue, but more related to USB ports I/O:
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

---

### Post by kdx7214 on 2015-08-05
I'm not sure how this makes any sense, but somehow it is magically working.   Here's what I did:

I tried every possible combination of changing out hardware - finally back to original setup as none of the changes fixed it.   Finally I decided to try UEFI (on the off chance that this worked - it didn't, btw).  During that process I had to use gpt partition tables, so when I switched back to BIOS mode, I used dd to clear out the first 10mb or so of each drive.   First attempt after that worked.   Is it possible that something gets written to the HD during installations that stays around and can confuse things?   I've never seen that before certainly - and had I not tried gpt/uefi would never have found it.

Thanks for clearing up the difference in the forums situation.   My past work experience was on HPUX systems, so linux is something of a toy for me to mess around with at home (and to run mythtv).  The whole stack exchange thing confuses the heck out of me - why can't I close my own problem?   I can't even "report it" as suggested in another post to get it closed.   Oh well.   It's working for now, so I now get to recreate about a years worth of data lol

---

### Post by oldfred on 2015-08-05
I started using gpt with 10.10 as a test.
And since then have partitioned all new drives with gpt.
If booting with BIOS you need the 1 or 2MB unformatted partition with the bios_grub flag.
Or if booting with UEFI you need the ESP - Efi System Partition as FAT32 with boot flag.

I started adding both bios_grub & efi as then my system was only BIOS, but was getting a new UEFI system. I only recently got new UEFI system but am glad I started planning ahead on partitioning.

I assume you know the limits of LVM. Or if any drive fails, all data is lost.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)

MBR(msdos) has the MBR or first sector of drive and now first partition is at sector 2048. But grub stores core.img in the sectors just after the MBR.
With gpt there is a protective MBR or first sector with one gpt partition, so old tools like fdisk do not see blank drive and try to partition it. But gpt has no space after MBR (why grub needs bios_grub) as gpt structure starts right away. 
Maybe change to gpt & back housecleaned something more than dd which would not seem normal.

---

### Post by kdx7214 on 2015-08-05
Okay, drives are wiped once again, reinstalled with gpt and bios-grub partition and things seem to be working again.  Thanks again for all the assistance @oldfred!

---

