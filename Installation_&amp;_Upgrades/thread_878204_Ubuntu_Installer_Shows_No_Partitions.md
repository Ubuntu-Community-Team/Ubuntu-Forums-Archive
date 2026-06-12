---
title: "Ubuntu Installer Shows No Partitions"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by mxcrowe on 2008-08-02
I just tried to install Ubuntu into a new partition on my HD.  I used Vista to create an 80gb partition, which shows up as unallocated space.  When I boot into the Ubuntu installer, it takes me to the place where you should choose how to "Prepare Disk Space", but I never get that menu.  It just shows me no partitions and all buttons are grayed out.  If I try to go forward, it says there is no root.  If I try to go backward, it tried to load the partition manager, but nothing happens.  So I just had to exit the installer and reboot into Vista.  Why doesn't Ubuntu recognize my hard drive/partition/SATA controller?  :confused:

Gigabyte GA-P45-DS3L BIOS F7
E7200 Core2Duo 2.53Ghz 1066Mhz FSB 3MB L2
(OC'd to 400mhz x 8 = 3.2Ghz)
SuperTalent 2x2G DDR2-800 PC6400 CL 5-5-5-15 (T800UX4GC5)
Seagate 500GB SATA2 7200 32mb HD
EVGA 8800GT 512MB Superclocked Edition
Ultra X-connect X2 550-watt PSU

---

### Post by Pumalite on 2008-08-02
You have to format the unallocated space. Ubuntu cannot be installed in unallocated space.

---

### Post by mxcrowe on 2008-08-02
I followed the procedure in this tutorial:  [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

Did they get it wrong?  Do I just format the new partition as NTFS or what?

---

### Post by jualin on 2008-08-02
Also make sure that it's not a problem with the Live CD that you are using, make sure that it doesn't have any defects. In my sig you have another tutorial of how to Dual Boot, maybe that will help you out.

---

### Post by jualin on 2008-08-02
> **mxcrowe said:**
> I followed the procedure in this tutorial:  [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

Did they get it wrong?  Do I just format the new partition as NTFS or what?

You don't have too many options of formating in Vista so I think that NTFS would make the trick. Anyways the Ubuntu installer will format it to EXT3 or some other Linux compatible file system.

---

### Post by mxcrowe on 2008-08-02
jualin,
I like your tutorial better...much more detailed.  I'm going to follow that specifically and also take the time to make sure everything is backed up from my Vista partition before I attempt this exercise again.  I'll also test the CD to make sure there are no errors.
Thanks!

---

### Post by mxcrowe on 2008-08-03
No joy.  I scanned the CD for errors and it comes up fine.  Tried to reinstall again after formatting the new partition as NTFS, and the Ubuntu installer recognzies neither partition.  It just comes up blank.  My hardware is nothing bizarre - hey, Vista installed on it no problem.  But the Ubuntu installer doesn't see the Vista partition or the new blank partition. What's up?

---

### Post by Pumalite on 2008-08-03
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it
See if it recognizes your drives/partitions.
If it does; prepare your partitions ahead of time.
Install, go Manual and use the already prepared partitions.

---

### Post by mxcrowe on 2008-08-03
I'll try it, but it appears the installer just doesn't recognize my HD or SATA controller, so I'm not sure what good it will do to create other partitions using another tool.  Why wouldn't it see the valid partititions that are already there?

---

### Post by mxcrowe on 2008-08-03
Ok, Gparted finds two NTFS partitions.  What do I need to do to the partition I intend to install Ubuntu into in order for the installer to work?
Thanks!

---

### Post by Pumalite on 2008-08-03
XP or Vista?

---

### Post by mxcrowe on 2008-08-04
The machine as spec'd in my first post is loaded with Vista Ultimate SP1 in a single partition.  I used Vista to create a new 80G partition for Ubuntu.  Now, whether that partition is unformatted, formatted NTFS, or formated ext3 (via Gparted), the Ubuntu installer does not see either my original Vista partition or the new partition I have created to install Ubuntu.  As far as I can tell, this installer does not recognize that I have a hard drive.  Gparted sees the partitions right away, and I used it to reformat the new NTFS partition to ext3, but the Ubuntu installer acts the same every time - no partitions seen, no O/S loaded.

---

### Post by Pumalite on 2008-08-04
Time to try some boot parameters. Try first:
all_generic_ide
at the end of your boot line

From another thread:

'I had the same problem installimg from the Live USB stick, I didn't see the hard drives. When you start the LiveCD, in the end, before clicking install, open a terminal.

#sudo passwd (to set the root password)
#sudo -s (to become root permanently)

#modprobe ide-generic

Now, I think you will be able to see the other install drives (at least it worked for me).

Now you can start the install clicking the Install program.'

---

### Post by xjgnsdof on 2008-09-20
I had the same problem, and adding "all_generic_ide" to the end of my boot sequence (after pressing F6) allowed me to install Hardy from the LiveCD.

Can someone explain (to me and to the OP) why Ubuntu would fail to recognize hard drive partitions that were there?

---

### Post by Pumalite on 2008-09-20
You might have a SATA controller configured as IDE

---

### Post by IMSciFi on 2008-10-11
Same issue here, but on a Foxconn P45A-S board (Same chipset), 8.04(.1) does not see the SATA drives at all, but 8.10 Beta does.  I'm at work atm but will attempt the appended install command when I get home and report back.

---

### Post by ph8 on 2008-11-10
To get around this bug in Hardy I had edited a setting in the BIOS which presented my SATA drives as IDE - since this was fixed in Intrepid without (apparently) being backwards compatible - I changed them back to being presented as straight SATA and all was well with the world.

Weird, I know

---

### Post by ubiubi on 2008-11-12
Hi

I have the identical problem as descibed at the top of the thread. But the problem of sata drive recognition continues with PCLINUX and FEDORA. I'm going to try the boot line alterations / verify the sata controler is not set up incorrectly.

Window XP
ABIT P35-E
E4300

do these problems only concern Intel based systems?

Cheers for the advice!

---

### Post by Soturi on 2008-11-12
I also had this issue, booting with all_generic_ide=1 at the live CD prompt fixed it. Interestingly, enabling AHCI mode in the BIOS also allowed the installer to 'see' the hard drive. I believe that this error is the result of the ICH10 chipset present in P45 and P43 series motherboards, possibly in G45 series as well. The chipset seems to present non-AHCI enabled drives as an unknown device to Ubuntu, but the workarounds are easy enough.

---

### Post by mxcrowe on 2009-11-05
Just as a follow up, 9.10 installed on the exact same system configuration, no change to BIOS or mobo, with no problem.  Recognized my hard drive right away.  Set up to partitions for Win7 and Ubuntu 9.10.  Using GRUB2.
-MXC

---

