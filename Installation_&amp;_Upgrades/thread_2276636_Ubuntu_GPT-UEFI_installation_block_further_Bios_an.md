---
title: "Ubuntu GPT-UEFI installation block further Bios and Boot Menu access"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by aimausy on 2015-05-04
I have Lifebook LH532 and for almost 2 years,
Ubuntu installaitions are not a problems with the fact that my notebook is UEFI enable.

In the past I just use MBR-MsDos partition, since I knew it works,
and I do not know anything about GPT-UEFI, except it is new better ways with great complications.
(I installed ubuntu(&derivertives multi boots) more than 20 times)

Until I replaced 750GB (MSDOS) with new empty 1TB
and installed ubuntu 14.04.1 as only OS in 1TB 
"and let ubuntu did that automatically, (1st choice installation)"

it made 1TB as GPT and did UEFI installation, without any warning of possible Bios disaster.

 [B]Ubuntu 14.04.1 (& 14.04.02) hacked and blocked firmware Bios,
no more F2 Bios option and F12 boot menu.[/B]


>>>>>> My Fix and workaround.<<<<<<<<<<< 
From
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082418](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082418)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1273060](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1273060)
[http://www.linlap.com/fujitsu_lifebook_ah532?&#comment_c5adb1445ac430630761be90a7eac560](http://www.linlap.com/fujitsu_lifebook_ah532?&#comment_c5adb1445ac430630761be90a7eac560)


 In short process.

 1. Short circuit CL1 and CL2 for Fujitsu LifeBook LH532 as posts above, to get at least F12 boot menu back.
(other computers may need to remove mainboard batteries? or other methods ?)

2. Boot with live Ubuntu then convert GPT 1TB to MBR 1TB (using gdisk)

3. Install Ubuntu on one of the partition of MBR 1TB, (I made 6 partitions).


 Result = multi boots ubuntu no more Fujitsu LH532's F12 boot menu wrecking.
Now I can install Windows and other Ubuntu derivertives, no issue on usb boot nor DVD boot choices.


Conclusion >>> Don't allow your harddisk to be made to GPT before ubuntu installations.
 if you are not 100% that your BIOS is compatible with Ubuntu GPT-UEFI installation.<<<<,


 By forcing your harddisk to be MBR or MSdos format, before Ubuntu installation.
That prevent UBUNTU to be installed in GPT-UEFI that can wreck your Bios.

 
(And do not allow Ubuntu to install in the first choice, by UBUNTU's ways,
you must select the last option, choose your own ways of installations.  Otherwise Ubuntu could make disastrous GPT-UEFI on your computer.)
---------------->>>> HELP need.<<<<<
But I still face problems, how to flash Bios since the solutions in the  above 2 bugs report in the lunchpad are UK models with different serial  LOTS from my note book.

Since my work around in converting GPT 1TB to MBR 1TB gave me boot menu permanent for the moment.

I rather stay without accessing Bios than risking flash the wrong Bios and cannot use the notebook at all.

1. Has anyone manage to reverse the UBUNTU disastrous GPT-UEFI to get the access of Bios Setup without flashing Bios?
2. Can Bios and Flash Utility for other models of LH532(xxx_, or serial Yxxx) work on LH532 bought in Thailand.
---------------

---------------for newbies to ubuntu 
So It is the GPT of the harddisk that force Ubuntu to install as UEFI mode and wreck Fujitsu Bios and many other computers.
It is the "worst bug" (from user point of view)  I found on Ubuntu in my life.

 Ubuntu GURUs must do somethings.
This give bad names to ubuntu.
 The computer technician quote $100 to fix my Bios.

=============

 My Proposal simple problems reductions or preventive solutions (for under 2TB Disk).

 
1. During Installation, there must be warning message about making harddisk into GPT partition type with
" very prominent LETTERING " that this GPT and UEFI installation could wreck the Bios of your computer.
(Many computer's Bios are not compatible with UBUNTU UEFI installation and result in blocking further use of Bios,
and with samples models Fujitsu and many others.)
"Proceed with your own risk "
or
"Choose to do the MBR and Bios installation option." then safe old days of installations are done.

 
2. The installation process check the troblesome models of computers
and just force Bios-MBR installations for those troblesome machines in the only Bios-MBR lists.
But perhaps it should have the option of EXPERT MODE that can override this forced Bios-MBR installation.

 =========

Propose alternative solution.

 Request to the UBUNTU and Grup Gurus to do the Smart Grup "Auto Boot Menu"
Regardless of UEFI successful installations or not.
Grup will install an auto detect boot media and creat options for user to boot from the menu choices
_**as those provided by the Bios.**_

 So we don't have to fix the bugs immediatly but user can carry on their other installation choices.

 But the Bios will be wrecked still. So the previous proposals should be in placed as well.
=========

 
Thanks every one who try to help our communities.
And I hope the Guru will fix this bug soon.

Please help comments if you have the same problems as I had.

---

### Post by oldfred on 2015-05-04
Some have gotten it to work.

 Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

This entry in grub boot menu should get you into your UEFI. Do you have a fast boot in UEFI on? That can be an issue. But then a full cold boot, remove battery, hold power switch to drain last bits and then reboot and press correct key to get into UEFI/BIOS should work.

You should already have this:
      
 ### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup

 }
### END /etc/grub.d/30_uefi-firmware ###

---

### Post by aimausy on 2015-05-04
> **oldfred said:**
> 
You should already have this:

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

fwsetup

}
### END /etc/grub.d/30_uefi-firmware ###

Where this command or parameter suppose to be, I quess in EFI boot partition, but which file?

My harddisk at the moment has only UBUNTU installed, now under MBA 1TB'

I will try to get the latest update on BIOS and flash it . Then I will install ubuntu under GPT-UEFI and see if it wipe out Bios again or not.
That will take a few more days.

Thanks for the info.

---

### Post by aimausy on 2015-05-04
> **oldfred said:**
> This entry in grub boot menu should get you into your UEFI. Do you have a fast boot in UEFI on? That can be an issue. But then a full cold boot, remove battery, hold power switch to drain last bits and then reboot and press correct key to get into UEFI/BIOS should work.

The Bios is not accessable so I cannot check if fast boot in UEFI is on or not.

But removing battery and power  on to clear all electricity the turn on with F2 to go to Bios is not working.

Thanks

---

### Post by Vladlenin5000 on 2015-05-04
Here we go again: ESC ESC ESC... (I lost track of how many time I've said it. Yes, after you install anything that boots onto a GTP partitioned drive, subsequent access to UEFI is much harder because you have a very short time frame to actually press ESC - not any other key (you're thinking like the old BIOS) - to stop the boot process. But is doable.

---

### Post by aimausy on 2015-05-05
from another lunchpad bugs, I am trying to work on.
Christopher,
I had a long chat with Fujitsu Technician who fix somany LH532 in Thailand, which sold with no OS and Ubuntu destroy Bios.
Unfortunately the Warranty has expired and there for they don't need to support them any longer.
They delete the Bios files for the reason they don't want to have anything to do with that problems any longer.
 And warn that even in Thailand they sold a few models. 
The Bios is for preinstall Widows OS will be different than Bios version with no OS, 
even though they have the "same version no."/

If you have the wrong version burn into the Bios Chip, you will have a dead main board,
and they did have the dead ones before they learn that.

With those problems, Fujitsu decide to remove Bios download from the public websites,
at least for Asia-Pacific region, and I could not find them for the US and Canada also.
And we are left in Cold.

The technician has opinion that it was Ubuntu that Block the use of F2 and F12 functions.
So who ever wrote those parts of the Ubuntu installaion routine, should revise what they have done.
You cannot blame Fujitsu, these robust notebook, did not break and UBUNTU hack into their Bios and stuff it up.

He also warn that Fujitsu will not honour any warranty if it found their Bios is tampered with.
And they stop selling the non OS notebook, only preinstalled window 8 with GPT partitions only.
And If we change that to MBR and installed other OS, Fujitsu Technician said that will also void the warranty.

It means If I bought new Fujitsu ( I am about to do that) we will be risking void the warranty,
and the Fujitsu Technicians confirm, they are not supplied with Bios for new models at all.
(The main factory don't want them to mess up the mainboard again while under Warranty.)
So they could not help us fix the Bios problems any longer.

He also confirmed that by removing CMOS batteries for LH 532 .
It will reset only the date, not the Bios settings.
And only the CL1 AND CL2 short circuit is the only way to get the F12 BACK.

Now I hope those Kernel or grup or iNSTALLATION team GURUs will try to figure out,
"How to unblock" the  work that they hack into Fujitsu Bios or their UEFI manipulation.

=============

I will reformat MBR 1TB and install 15.04 as Christopher instructed.
I will later do GPT 1TB, it may be 2 days now before I could finish all these testiong, since holiday is over in Thailand today.
I will give feed back.

Thanks.

---

### Post by aimausy on 2015-05-05
[**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732")
I have tried more than 10 times, as you said and as I thought of other alternative may works on my machine.
Only F12 is working into Boot Menu.
Esc. F2 and other Fs, 
no no success.

Do you have successful Esc with LH532 earlier or on your other models?

How we can slow down the boot time, is there any command in the grub or UEFI installtion routine?

---

### Post by oldfred on 2015-05-05
With BIOS an operating system writes not info into it.
With new UEFI some data can be updated by an operating system. Windows does do some of that, but again UEFI controls all of that.
With new UEFI often vendors add a fast boot setting in UEFI to meet Windows boot time standard. But then none of the keys to get into UEFI work as you do not have time to press them. You have to turn off fast startup.

Most of what you were told was just tech telling you he did not want to help.

---

### Post by timschumi on 2024-04-19
I've recently looked into fixing this issue, and came up with a consistent way of restoring the laptop to full operation.

The boot menu entries can be partially restored by bridging the "CL1_CL2" test point  that is located under or next to the RAM slots.
It may be required to have the laptop powered (or even powered on) while bridging the contacts for the test points to have any effect.
This brings back the  device-based boot menu entries, but does not yet restore access to the  BIOS Setup menu.
For that, a USB stick with [Fujitsu's BIOS update tool]("https://support.ts.fujitsu.com/")  (search by serial number to make sure you find the correct hardware revision) needs to be prepared, booted from, and run.
This restores most BIOS  settings to their default, including the missing BIOS Setup menu.

Alternatively, if the currently installed Linux system is still  bootable, one can use [this tool]("https://github.com/timschumi/ah532-biostools") to restore all entries  without having to go through a BIOS update and reset.
This works by manually  rewriting all broken EFI variables with their expected content.
Please do make note of the list of supported configurations and of the  disclaimer (and let me know in case the tool does or doesn't work on  some previously untested configuration).
In case you want to know more about this works, there is a [post explaining the underlying details]("https://blog.timschumi.net/2024/01/20/ah532-bios-investigation.html").

Lastly, a [workaround for the issue]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f45812cc23fb74bef62d4eb8a69fe7218f4b9f2a") has been merged into the Linux  kernel, which should keep this from occurring on any new  installations.
This patch already ended up in the current installation  media for the Ubuntu 24.04 beta (which I have confirmed to be not affected), and it will presumably be included in  all installation media going forward.

---

