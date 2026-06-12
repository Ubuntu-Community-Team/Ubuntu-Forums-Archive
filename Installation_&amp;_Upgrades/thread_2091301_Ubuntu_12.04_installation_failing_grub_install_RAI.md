---
title: "Ubuntu 12.04 installation failing grub install RAID 0"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by adv0cat3 on 2012-12-04
Hey everyone,

I have the same EXACT problem as here:
[http://ubuntuforums.org/showthread.php?t=1972263](http://ubuntuforums.org/showthread.php?t=1972263)

Even a very similar computer. Alienware M14xR2 with 2x 256GB Samsung SSD's in RAID 0.

Regular Ubuntu installer returns Grub / bootloader install error as per the post above so I used the alternate installer as per the posts' recommendation.

After the alternate installer ran and I selected "install to largest freespace available" it deleted the bootloader entirely and neither Ubuntu or Windows ran. The computer just BIOS looped infinitely.

I then found this page:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And ran the automatic boot repair after booting to a normal Ubuntu install disc and selecting 'Try Ubuntu'.

Here's the result of my boot repair:
[http://paste.ubuntu.com/1411314/](http://paste.ubuntu.com/1411314/)


But now I boot directly into windows and there's no Ubuntu / Grub option when booting up.

Any ideas?! I know the boot repair utility is very complex and I was hoping to avoid having to dive deep into it just to repair my installation because I'm still very new to all this stuff.

EDIT1: Looks like the GRUB location tab is greyed out in Boot Repair. This would imply that GRUB is missing which would explain why I boot directly into Windows immediately every time correct?

EDIT2: Trying 'sudo grub-install /dev/hda' and getting -> cannot find device /boot/grub (is /dev mounted?)

EDIT3: Tried 'sudo mount /dev/hda' and getting -> can't find /dev/hda in /etc/fstab or /etc/mtab

---

### Post by oldfred on 2012-12-05
Changed your title to include RAID. Hopefully someone that know RAID will pop in with suggestions. I do not know RAID as I mentioned in you linked thread.

Before running Boot-Repair add the RAID drivers. I thought Boot-Repair added them but not sure.

Bootinfoscript is run as part of BootInfo in Boot-Repair.

       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:


   Boot script is able to search LVM partitions if the LVM2 package is install, Fedora needs to be mounted to see it with os-prober
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
# unlzma is equivalent to xz --format=lzma --decompress.


Ubuntu has not used hda for devices for several years, its /dev/sda1. But with RAID you use the long RAID id not device.


Something like this if manually reinstalling grub:


       
 For RAID reinstall from liveCD
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

### Post by darkod on 2012-12-05
The bootinfo doesn't show any linux partitions. If the install finished, even if it failed installing grub, there should be linux partitions on the array.

Also, double check whether uefi boot is enabled in the bios or not (if there is option for uefi). You don't seem to use uefi so it's better to disable it in bios in case it has the option.

Double check that win7 boots fine after that.

I would try installing again with the alternate cd and this time select manual partitioning (not automated), and take a look at which partitions are shown as existing on the array. Whether there are linux partitions too, or onlt the two ntfs partitions.

---

### Post by adv0cat3 on 2012-12-05
You are correct, it appears that Linux never actually got installed. I can give it another whirl with the guided setup? Although I'm not sure I'm good enough to set up the swap partition manually.

Here's a pic:
[http://imgur.com/nrFZP](http://imgur.com/nrFZP)


Also, I have 16GB of RAM so I'm not even sure I need swap space.

---

### Post by darkod on 2012-12-05
If you don't plan to hibernate, just make a 2GB swap. Otherwise you need about 1.5 x RAM size which in your case would be too much GB for swap only.

In that screen, use up/down to select the free space of 281GB and press Enter.
It will ask you whether you want to create primary or logical partition, and also if you want it to be on the beginning or end of the free space.

Make one logical of 279GB for example at the beginning. Then from the remaining 2GB of free space, make another logical partition.

After those two partitions show up in the list, select the big one, in the windows that opens select Use As ext4, mount point /. You don't need anything else. Select Done configuring partition.

When it returns you to the list, select the small one, Use As swap area. There is no mount point for swap.

That´s it.

Towards the end of the install, if it gets confused and says it can't install grub2 and asks where to try, type this as location (exactly as is the name of your array):
/dev/mapper/isw_cidfefffaa_Volume0

That should be it.

---

### Post by adv0cat3 on 2012-12-05
EDIT:

Here's what I have now:
[http://imgur.com/KXUGw](http://imgur.com/KXUGw)

EDIT2: It's telling me there's nothing set up for swap at the moment so I'm trying to figure out how to configure that correctly. I'll do some googling.

EDIT3: Figured it out! Installing now.

---

### Post by darkod on 2012-12-05
It's too late now, but I forgot to mention if you wanted a separate /home partition you could have created three partitions:
/
/home
swap

But lets see how the installation finishes. Later if you want to, you can consider reinstalling to create /home too since you will know how to do it again.

---

### Post by adv0cat3 on 2012-12-05
> **darkod said:**
> It's too late now, but I forgot to mention if you wanted a separate /home partition you could have created three partitions:
/
/home
swap

But lets see how the installation finishes. Later if you want to, you can consider reinstalling to create /home too since you will know how to do it again.

Install finished. Selected to install GRUB to the main disk. It's now BIOS looping again :(

---

### Post by darkod on 2012-12-05
Can you double check BIOS boot options and see if you need to list the array as boot device?

I have no other ideas, it seems like bios issue not accepting the boot device. The installation seems to have finished OK.

---

### Post by adv0cat3 on 2012-12-05
> **darkod said:**
> Can you double check BIOS boot options and see if you need to list the array as boot device?

I have no other ideas, it seems like bios issue not accepting the boot device. The installation seems to have finished OK.

The BIOS has worked previously with a RAID 0 already. Definitely not a BIOS issue. It feels like the bootloader has been completely wiped out again.

Under BIOS -> Advanced Sata Operation -> 'RAID' is selected
Under BIOS -> Boot -> Hard Drive is selected. There is no RAID option.

I hate to say it but I'm close to giving up because I can always VM 10.04 which is actually the version I really need to run =\

---

