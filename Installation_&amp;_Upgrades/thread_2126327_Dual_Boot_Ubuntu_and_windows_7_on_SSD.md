---
title: "Dual Boot Ubuntu and windows 7 on SSD"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by lithiumKid1976 on 2013-03-16
hi

im getting ready to dual boot my machine (currently running windows 7) with ubuntu.

my HD is a 60GB SSD with 15GB free space.

what is the correct way to install ubuntu on this? is it any diffrent because its a SSD?

ive seen peoples suggestions where it says to shrink the HD space in windows first, then when installing ubuntu, you manually set the HD space to use for swap and the install.

ive also seen suggestions, where you can let the ubuntu install set the HD space and swap to use.

is there a definitive answer out there? thanks :)

---

### Post by oldfred on 2013-03-16
Always shrink Windows with its Disk Management tools. Some have had success using the installer or gparted, but it is always safer to use Windows tools for Windows. 
Windows will have to run chkdsk or make other repairs on its new size. Also do not shrink it too much as Windows needs most of your SSD anyway. And it really runs best with 30% free space in the NTFS partition.

Ubuntu can be installed in 10 to 25GB. Do you also have a rotating hard drive for data or is this your only drive?

       How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There&#8217;s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)
Discussion of swap on SSD - best not to)
[http://ubuntuforums.org/showthread.php?t=1937251](http://ubuntuforums.org/showthread.php?t=1937251)

---

### Post by lithiumKid1976 on 2013-03-17
hi, and thanks for your reply.

i have my data (pics, music, films etc) stored on 2 x 500gb hd which i have mirrored in windows, so that should be ok.

on my ssd, i can give 10gb to Ubuntu, and windows 7 can have the remaing 5GB.

ill try that later and let you know how it goes :)

thanks

---

### Post by lithiumKid1976 on 2013-03-30
im not having much luck with this, ive got 12.04 booting off a usb. i then manually create the partitions (ie / of 10GB and a swap 1.2gb in size)

after chosing the locale, it starts copying files. but mentions something about ssd1 and sda (will get the full error shortly.)

could it be failing, due to a 500GB mirrored hard disk?

---

### Post by darkod on 2013-03-30
If you are using the manual install method, which destination you selected for the bootloader? If the ssd is /dev/sda you should install it on /dev/sda.

If your raid is fakeraid (bios raid), grub2 from the live cd can't install correctly on fakeraid.

Without the exact error, it's not clear if only the grub-install is failing or something else.

In general, it should install fine since you are not installing onto the fakeraid. Do you know if the partition table on the ssd is msdos or gpt?

---

### Post by lithiumKid1976 on 2013-03-30
ok thanks, here goes. heres whats showing under the partitions before i go to install.


/dev/sda1 ntfs 52821mb
/dev/sda2 ext4 9999mb
/dev/sda5 swap 1198mb

other devices listed
/dev/sdc ntfs 500gb
/dev/sdd1 ntfs 500gb

the above are 2 500gb disks, mirrored in windows. (dont think its bios raid..)
not sure about msdos or gpt?

when installing i get the folllowing issues

ubuntu ubiquity: grub-probe: error: cannot find a grub drive for /dev/sdc
ubuntu ubiquity: grub-probe: error: cannot find a grub drive for /dev/sdd1: check your device.map

then it shuts down...

---

### Post by darkod on 2013-03-30
You are aware that ubuntu won't be able to access a raid created in windows, right?

Also, you should be consistent. Why did you made the raid from sdc and sdd1? In one case you used the disk as a device, in the second case you used a partition on the disk. You either use the disk as device, or a partition, not mixed.

Those errors shouldn't matter as long as it installs grub2 to /dev/sda correctly. Have you tried booting from sda and see how it goes? Even if grub2 didn't install correctly to the MBR you can try adding it from live mode with:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should install it onto the MBR of /dev/sda.

---

### Post by dabl on 2013-03-30
You need to verify that your BIOS can see the SSD as a bootable device (i.e. that the SSD shows up on the "boot sequence" list in BIOS).  Possibly you need to set the "boot" flag on the partition where you are installing grub.

---

### Post by lithiumKid1976 on 2013-03-30
hi

regarding the raid not being access by ubuntu, thats fine, as i have the same data on a USB HD, so that should be ok.

for the raid, i let windows handle it, the 500GB had a 100mb system reserved , then the rest of the space is used as NTFS. this might be why the raid is looking a bit funny.

if i shut down the pc, unplug the raid, and boot to ubuntu, do you think it would work then?

thanks for your help so far.

---

### Post by darkod on 2013-03-30
Hold on, your system reserved partition is on one of the raid disks, and outside the raid? That makes no sense at all. That partition holds the win7 boot files, and I expected the files to be on sda1 since that's where win7 is (I assume).

If the raid disk where system reserved is fails, your system will stop booting since it can't boot without it. So, having the raid doesn't mean much since win7 will not be booting, and it's win7 assembling the raid (which according to your words now seems as windows software raid).

Have you thought about that?

---

### Post by lithiumKid1976 on 2013-05-31
Finally got around to fixing this today, as darkod mentioned, for some reason the reserver partion was on the raided hard disk.
i backed up my stuff to a seperate usb HD. disconnected the Raid HDs. and did a repair of window 7, fixing the mbr.
once windows was back running of the SSD, i was able to install ubuntu 13.04
so far so good, boots really quickly on the ssd.... thanks for all your help..

---

