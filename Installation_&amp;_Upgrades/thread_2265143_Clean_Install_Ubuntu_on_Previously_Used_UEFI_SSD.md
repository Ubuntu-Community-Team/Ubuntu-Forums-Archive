---
title: "Clean Install Ubuntu on Previously Used UEFI SSD"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by halw on 2015-02-12
Looking to wipe current OS and install Ubuntu on SSD. Does the installer automatically setup UEFI partition as well as boot? Also, what about GPT? Is disk formatted that way?

Never did linux install on UEFI bios system before.

---

### Post by ubfan1 on 2015-02-13
The SSD is just another hard disk as far as Ubuntu is concerned, so you can use GPT partitioning, and I'd recommend you set up the partitions (EFI, root, swap, ...etc. the way you want under the "something else" installation choice.  The one gotcha with SSDs is that if you have it in an external enclosure (USB for instance), you probably will not have the trim functionality!!!  If that's your case, I'd partition and install the filesystems, then run fstrim while the disk is internally mounted (using live media if necessary).  Ideally, run a trim after the install to cleanup after all the temporary files, then you will start out with a top performing system. Do read up on the UEFI installs, they should work, but many machines have quirks which make workarounds necessary.

---

### Post by halw on 2015-02-13
@ubfan1, thanks for the reply. Essentially wiping desktop system and installing Ubuntu. Trim shouldn't be an issue with Crucial CX100 SSD. I just wan't sure if I should let the Ubuntu installer do all the work or, as you suggested, pre-partition  the drive myself.

---

### Post by oldfred on 2015-02-13
How you boot installer is how it installs, or you want to boot flash drive in UEFI mode. Your UEFI should have two options to boot it. One clearly saying UEFI and the other just the name or label of flash drive which then is a BIOS/CSM boot.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

What brand/model system & what video card?

---

### Post by halw on 2015-02-13
Asus h97-plus mobo, nvidia gt740 gpu. 16 Gb ram, crucial mx100 256 mb ssd.
Will be booting from live dvd.

---

### Post by oldfred on 2015-02-13
Do not know how similar H is to Z97 model. I just installed to a New Asus-z97-ar model. I had a lot of UEFI settings to get it to boot in UEFI mode. It required change to Other from Windows which I think really meant secure boot. Then I could only get flash drive to boot in UEFI mode with UEFI only, not even UEFI & BIOS setting. I also turned UEFI fast boot off, later set it to 3 sec so I could still get into UEFI if needed.

 Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)

---

