---
title: "Select Proper Boot Device"
date: 2016-07-11
forum: Installation &amp; Upgrades
---

### Post by nukenowakowski on 2016-07-11
Given:
 Intel i7 Quad.  AMD 370 Graphics card running on the  proprietary drivers.  Current setup has been running for several  months.  HDD is a 2TB full use Ubuntu 14.04 install. (no partitions  other than required)
Suspected causes: 
Other computer in the  house went through graceful shut-down citing a power supply having bad  input power (too much wattage or too little wattage is not part of the  report)
Symptom 1:
The initial symptom upon reboot straight to the HDD is
```
Reboot and *Select proper Boot device* or Insert *Boot* Media in *selected Boot device* and press a key

```This  being a problem I've seen many times before and have some experience  combating - I moved straight to my bootable (14.04) USB key
Symptom 2:
```
*BGRT*: *invalid status 0* (expected 1)
```
Shows  up.  I know less about this, but I knew I could run a workaround as  BGRT shouldn't be causing a fatal error. (disk check passes)

[LIST]
[*]Boot from USB key, select "e" on the "Try Ubuntu" line and add "nomodeset" at the end of the linux line 
[*]Once Ubuntu live is running add ppa:yannubuntu/boot-repair install and run a GRUB2 repair 
[*]boot-repair  has been a trusty tool in the past - it reported a possible repair, and  I didn't see anything out of the ordinary... View here: 
[/LIST]
[http://paste.ubuntu.com/19008583/](http://paste.ubuntu.com/19008583/)

After repair and reboot, the initial symptom returns.
```
Reboot and *Select proper Boot device* or Insert *Boot* Media in *selected Boot device* and press a key
```
[LIST]
[*]Suspecting  no good options from here, I decide to try a brand new 1 TB HDD, and  run a fresh install.  Again I get the 2nd symptom when installing from  the 14.04 USB. 
[*]Fresh install runs through cleanly and works to perfection. 
[*]Upon reboot... Initial symptom returns (All other bootable media is disconnected...and the now new HDD is selected) 
[/LIST]

Key points:
[LIST=1]
[*]I appear to be able to boot only from the Universal Serial Bus 
[*]I CAN mount and view drives and write to drives successfully - through the SATA controller 
[*]I have done a battery removal/CMOS reset and BIOS defaults also. 
[*] Secure boot is off. AHCI  has been set, and CSM set as well.  I've tried quite a few of the HDD troubleshooting steps as it was an early suspect (I've also thrown in a SSD and ran a clean install to reassure myself - all problems still persist) 
[*]I HAVE read through other threads titled similar to mine to try their workarounds.  No Joy. 
[*]Finally I know I'm new to the forums, but I'm not new to linux or Ubuntu.  I'm pushing 20 years experience on *Nix like machines, I'm no expert, but I can find my way around... 
[/LIST]

What am I missing?

-Glen

---

### Post by oldfred on 2016-07-11
If you had a power failure, you could need fsck. Files systems then get out of sync.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

You have a lot of kernels, it is time to houseclean.

You show Secure Boot on, but have signed kernels, so it should boot ok. But I might try Secure Boot off.
Some UEFI also do not let you boot anything external unless you specifically turn it on in UEFI, especially if UEFI Secure Boot is on. 
You may have a setting allow USB boot. Or enable USB ports or similar. 

      
 #Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove 

 I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by nukenowakowski on 2016-07-12
Thanks for the reply.  We think alike it seems.  :)
fsck throws a ton of errors at me - I'm looking at >4000 bad sectors.  That screams disk problem.  
However It doesn't solve the issue with other disks not working properly (I've now tried 3 different disks... SATA3 SSD, SATA3 HDD, and PCIeSSD..all fail)  
This has me eyeballing the motherboard...I'm not sure how or where the problem could be coming from.  
Something isn't right in its UEFI recognition.  When I run in legacy mode I get some better behaviours from the drives - I've even managed 2 or 3 correct boots...but I can't recreate a working environment more than twice.  Very bad sign.
I've tested the other drives in other machines.  They boot up happy as can be.
I've even gone the route of clean install on outside machines with all hardware set to 0 on these new drives.  All works great, once swapped into this machine...No joy.
Secure Boot was configured as "on" for my GRUB 2.0 boot-repair software repair..not "on" within BIOS config - 
that just gives me flexibility of running it with secure boot on and fast boot on - giving me a quick startup should I ever want it in the future. 
I've dumped that option and ran the repair again in case its a source of error.  No joy.
I dumped all but the 2 newest kernels now, that is solid advice and something I typically follow, although I've been lazy on this machine, and it shows.  
Still no joy, I'll update when I make progress or get a solution.

-Glen

---

### Post by oldfred on 2016-07-12
Either install is CSM or UEFI and you need to be consistent.
The flash drive can be booted in a different mode from default hard drive setting in UEFI.
UEFI offers UEFI:name and name(or CSM) boot options separately, if Secure Boot is off.
If Secure Boot is on, then the only boot option is UEFI with secure boot on, if allowed or settings changed to allow USB boot.

With 16.04, they have updated to only keep 2 kernels by default.

---

### Post by nukenowakowski on 2016-07-14
[SIZE=2][FONT=courier new]I'm sorry Fred, I think perhaps I wasn't clear.  I performed installs on UEFI and installs as CSM in correct environments - changing out drives, and setting the BIOS correctly.  The idea was to find out what was with the original HDD.  I have found the answer.[/FONT]
[FONT=courier new]```
sudo badblocks -v /dev/sda1
``` Turned up some interesting information.  In total 3435 Bad blocks were found.[/FONT]
[FONT=courier new]Where the blocks were on the disk?  I cannot say for sure..but I have a hunch based on what happened next.[/FONT]
[FONT=courier new]I set a file for the blocks with the intent of running a boot-repair to reinstall grub and the MBR on the disk.  [/FONT]
```
[FONT=courier new]sudo mkdir ./unusable && b[/FONT][FONT=&amp]adblocks /dev/sda1 > /home/nowakowski/unusable[/FONT][FONT=&amp]
[/FONT][FONT=courier new]sudo fsck -l unused /dev/sda1[/FONT]
```
[FONT=courier new]The finishing touch was just running the recommended repair in boot-repair and the next thing I know - the disk is good to go.[/FONT]
[FONT=courier new]I plan on cloning the disk using dd and removing the unused file on the new disk.  This should get me back to where I wanted to be as it does appear the old drive is on the way out.  Based on how it all worked out, my hunch is some of the bad blocks were on the MBR. I don't know of a way to confirm this, but it seems probable.  The behaviors the disk displayed lead me to believe that there may also have been blocks that were damaged in the bootloader, but again its hard to really know for sure.[/FONT]

[FONT=courier new]Thanks for your help fred - you got my noggin going and I found it.  After all fsck was pivotal![/FONT]
[/SIZE]

---

