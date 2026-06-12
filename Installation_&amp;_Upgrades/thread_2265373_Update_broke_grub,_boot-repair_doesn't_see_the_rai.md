---
title: "Update broke grub, boot-repair doesn't see the raid"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by dvbarragan@gmail.com on 2015-02-14
Greetings!   

Have been running "trusty", packages 3.13.0-36 thru 3.13.0-44 have updated just fine,  today hit update for 45 and system wouldn't boot.  

I pressed "esc" during boot and was able to get to the grub menu and booted to earlier version (i.e., 44) .... came up fine.   I attempted to update again (via apt-get) and this time it looked successful however, reboot now brings me to grub prompt!  (even worse than before... heavy sigh!) 

I've created and booted a usb boot-repair-disk ... info can be found at ([http://paste.ubuntu.com/10225951/](http://paste.ubuntu.com/10225951/) )

I'm using software raid10  
Any help would be 

Here' my system info:
[TABLE="width: 100%"]
[TR]
[TD="colspan: 2, align: center"]INTEL, DH57DD, LGA1156, Intel® H57, DDR3-1333 16GB /4, PCIe x16, SATA 3 Gb/s RAID 5 /5, DVI, HDMI, HDA, GbLAN, FW /2, mATX, Retail
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]INTEL, Core™ i7-870 Quad-Core 2.93GHz, LGA1156, 2.5 GT/s, 8MB L3 Cache, 45nm, 95W, EM64T EIST VT XD, Retail
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]NOCTUA, NH-U12P SE2 CPU Cooling Fan, Socket 1366/1156/775/AM3/AM2, 2x 120mm Fans, Copper/Aluminum, Retail
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]NOCTUA, NT-H1 Thermal Compound, 1.4 g
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]KINGSTON, 16GB (4 x 4GB) ValueRAM PC3-10600 DDR3 1333MHz CL9 (9-9-9) 1.5V SDRAM DIMM, Non-ECC
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]GIGABYTE, GV-N460OC-768I, GeForce® GTX 460 715MHz, 1GB GDDR5 3600MHz, PCIe x16 SLI, 2x DVI+mini HDMI, Retail
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]SEAGATE, 1TB Barracuda® 7200.12, SATA 3 Gb/s, 7200 RPM, 32MB cache
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]SEAGATE, 1TB Barracuda® 7200.12, SATA 3 Gb/s, 7200 RPM, 32MB cache
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]SEAGATE, 1TB Barracuda® 7200.12, SATA 3 Gb/s, 7200 RPM, 32MB cache
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]SEAGATE, 1TB Barracuda® 7200.12, SATA 3 Gb/s, 7200 RPM, 32MB cache
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]RAID, RAID 10 (mirroring and striping), min 4 hard drives required
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]SONY, AD-7261S Black 24x DVD±R/RW Dual-Layer Burner w/ Lightscribe, SATA, OEM
[/TD]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"]ASUS, VE228H Black WideScreen LCD Monitor, 21.5" TFT Full HD LED, 1920x1080, 0.248mm, 250cd/m², 5ms, VGA/DVI/HDMI, VESA, w/ Speakers
[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2015-02-14
I do not know RAID, but I do not think you install grub to MBR with RAID, but to root of RAID.

Boot-Repair suggested you install mdadm as that is not in the standard desktop. So it could not see the RAID.

>  RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y --force-yes mdadm --no-install-recommends)
Warning: no DMRAID nor MD_ARRAY.



---

### Post by dvbarragan@gmail.com on 2015-02-14
I did add the mdadm and proceeded with the boot-repair,   after following all instructions I get (error: invalid arch-independent ELF magic Entering Rescue mode) now I'm at the grub rescue prompt (no longer at the grub prompt ... I'm guessing it has to do with the grub installed by boot-repair-disk???) even if I set root to the (md/1)/boot area where all the images are ... I get a the invalid arch-independent message when attempting to insmod linux

this is the latest boot-repair info:  [http://paste.ubuntu.com/10229247/](http://paste.ubuntu.com/10229247/)

---

### Post by oldfred on 2015-02-14
Are you using the auto-fix?
It looks like Boot-Repair is installing grub to MBR of drive like sda when it should install to md0 or whatever you have named the root of the md not a partition of the md.

Do you have two RAIDs?
Grub menu shows a separate UUID for /boot than UUID for / (root).
But fstab only shows / not a separate /boot? So kernels & grub would not get reinstalled correctly. They would go into / as a /boot folder not into a /boot partition.

And elf error is often a grub version issue.

But I do not know enough about your RAID to know what is correct or not.

---

### Post by dvbarragan@gmail.com on 2015-02-15
Yes I was using auto-fix,

My raid is setup via the ubuntu docs ([https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html) )

I have 4 1Tb disks
1st partition is swap the 2nd partition is  the remainder of the disk and is marked bootable
So I'm not sure if I have two raids? but both swap and normal (bootable) file systems are protected (hence md/0 and md/1)

I'm fearless at this point as I have good backups so most of this is an educational opportunity ;-)  ... trying to understand how/whats going on.
so rebuilding is something I'm considering .. (but would rather understand how it got broke and how to fix).  

If I decide to just give up and have a do over .... I've seen some suggestions about creating a non-raid boot (i.e., 3rd) partition on the first disk (leaving the same space on the other three as "free").   Thus protecting my (raid) if something bad happens on the boot ... (it's just that the boot wouln't be protected...),  any thoughts on this?   As I understand GRUB2 does not require a separate boot partition.  but a seperate boot partition is recommended for RAID

---

### Post by oldfred on 2015-02-15
I do not have RAID. 
In the old days you had to have a separate /boot as the boot loaders did not have RAID drivers. Now with grub2 that is not required, but do not know if still recommended for any reason or not.

You should just be able to reinstall grub to the root of the RAID. If you add the RAID driver to the Desktop & then run Boot-Repair's advanced mode it should offer as one of the install choices the md. You do not want physical drives like sda, nor partitions sda1, nor the RAID partitions like md1. Not sure how RAID is named as there are many versions of RAID and I guess you can label/name your RAID installs. But root of RAID is where grub needs to be installed.

This is a "fake" RAID or BIOS RAID which is totally different than yours, but shows the mount of the RAID partition and then install to the root of the RAID.
 "fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

What does this show? You need the RAID driver installed.

 ls -l /dev/mapper

---

