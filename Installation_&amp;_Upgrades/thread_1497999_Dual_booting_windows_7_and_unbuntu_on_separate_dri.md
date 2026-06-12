---
title: "Dual booting windows 7 and unbuntu on separate drives"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by p0is0n on 2010-05-31
Hi all,
I have tried (a few times now lol) to get this setup.
I am using Windows 7 64-bit and Ubuntu 10.4 64-bit.

I have Windows 7 installed on one hdd, another hdd has the System Reserved partition along with a data partition for files, the third hdd is the one where I want to install Ubuntu.

I have found numerous tutorials on installing them both on the same drive, but not on separate ones. The couple I have found haven't really worked.

I think that Ubuntu is installed correctly but there is no option to boot into it. Windows 7 just happily loads itself.
I have tried reinstalling and selecting 'sdc1' (the native ubuntu partition) as the location for the bootloader to be installed and then used Easy BCD to add that location to the windows bootloader which gives the option to load Ubuntu but when selected dies complaining that there is a missing file (I think it just can't find the Ubuntu bootloader).

As an aside when I get to the installation screen the Ubuntu installer keeps on telling me that there are no operating systems detected on the machine (Even though I'm pretty sure the drive it is talking about 'sda' is where Windows 7 is installed). Not sure if that matters just seemed a little wierd.

Any help on this would be much appreciated as I have been at this for ages now.
Also I am fairly inexperienced with linux so small words and explanations would be helpful lol.
Thanks!

---

### Post by cusinndzl on 2010-05-31
Make sure you have the GRUB boot loader installed and properly configured.

---

### Post by p0is0n on 2010-05-31
> **cusinndzl said:**
> Make sure you have the GRUB boot loader installed and properly configured.

How would I go about doing that?
Thanks!

---

### Post by cusinndzl on 2010-05-31
> **p0is0n said:**
> How would I go about doing that?
Thanks!

Boot Ubuntu from the live CD and when the desktop opens open the terminal. 

Then type in "sudo grub", then "find /boot/grub/stage1".

Then type in "root (hd?,?)", replace the question marks with the hard disk number. 

After that type in "setup (hd0)", then type in quit. 

Source: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by darkod on 2010-05-31
Win7 will keep on happily loading itself because it's designed not to detect linux. I think you got it right the first time but what you should have done is change the boot order of the hdds in BIOS. You are still booting the disk which has the windows bootloader which will load just win7 directly.

With the later attempts, I think you might have messed things up slightly, depending what procedures you tried, but even now I believe just changing the hdd boot order in BIOS should get you to the correct grub2 on the correct disk.

Alternatively, boot the 10.04 cd in live mode, and execute the boot info script which will show all the details so I don't have to speak "blind":
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by darkod on 2010-05-31
> **cusinndzl said:**
> Boot Ubuntu from the live CD and when the desktop opens open the terminal. 

Then type in "sudo grub", then "find /boot/grub/stage1".

Then type in "root (hd?,?)", replace the question marks with the hard disk number. 

After that type in "setup (hd0)", then type in quit. 

Source: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Please pay attention. That's for grub1, and 10.04 uses grub2 now. Those commands are NOT applicable.

Don't try them, or you can mix up grub1 and grub2 files, and then you're in trouble.

---

### Post by cusinndzl on 2010-05-31
> **darkod said:**
> Please pay attention. That's for grub1, and 10.04 uses grub2 now. Those commands are NOT applicable.

Don't try them, or you can mix up grub1 and grub2 files, and then you're in trouble.

Thank you for the correction.

---

### Post by p0is0n on 2010-05-31
> **darkod said:**
> Win7 will keep on happily loading itself because it's designed not to detect linux. I think you got it right the first time but what you should have done is change the boot order of the hdds in BIOS. You are still booting the disk which has the windows bootloader which will load just win7 directly.

With the later attempts, I think you might have messed things up slightly, depending what procedures you tried, but even now I believe just changing the hdd boot order in BIOS should get you to the correct grub2 on the correct disk.

Alternatively, boot the 10.04 cd in live mode, and execute the boot info script which will show all the details so I don't have to speak "blind":
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

:oops:
Sorry, I really should have checked the boot priority, I swear thats the same mistake I made on my last machine when I did this.

Thanks a lot, I have them both booting just fine now.

---

