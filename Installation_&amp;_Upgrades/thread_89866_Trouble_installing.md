---
title: "Trouble installing"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by renzuken on 2005-11-13
I'm new to Ubuntu and really want to give it a real try as Windows is not my friend anymore!

Anyway I've been trying to go through the installation but it stops dead at 78% 'creating ext3 file system for / in partition #1 of TDE master (hda)...'

As I have no clue on partitioning, I selected the erase hard disk option and it keeps stopping at that point.

Is there something I should try doing to resolve this?

---

### Post by aysiu on 2005-11-13
Sounds as if you have a bum disk--corrupted during download or corrupted during the burn process.

---

### Post by renzuken on 2005-11-13
I'll try burning the image to a fresh disc and see how it goes.

---

### Post by aysiu on 2005-11-13
Do you know how to do checksums? They can be done in Windows and Linux--they basically check the integrity of the download. Also, if you're burning (and you're sure the ISO image is good), try burning at a slower speed (2x or 4x).

For more info on checksums, see these links:
[In Linux](http://ubuntuguide.org/#checkmd5)
[In Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;841290)

---

### Post by renzuken on 2005-11-13
Well I just did a fresh burn of the same ISO image and it stopped at the exact same point again, I'm not sure of how to use check sums so I may just re-download from a different location.

Also would the type of disc affect this (ie CD-R/ CD-RW etc.).

Edit:
I downloaded a new image, checked it to be fine and burned it.

Same problem, I tried reducing the partition size and it whizzed through to 100% but then the bar dissapeared leaving me with just the blank screen.

Is this just my computer's way of saying no?

---

### Post by renzuken on 2005-11-13
So I've downloaded and burnt 3 new images just to test and I do seem to be getting the same thing. I turn down the partition size and the ex3 file system sets up on the first partition and then the bar dissapears leaving the blue screen and then nothing, just seems to stop.

Has anyone else had this happen?

---

### Post by aysiu on 2005-11-13
How long do you wait on the blue screen before giving up? It's possible the blue screen is perfectly normal.

---

### Post by renzuken on 2005-11-13
I thought it might have been just normal, I gave it about an hour and 30 mins, I came back to it and it was still at the same state with no HD activity or noise from the CD drive.

---

### Post by SickTwist on 2005-11-14
Try typing this and pressing enter on the first screen that you see on the install CD (it has the Ubuntu logo):

linux acpi=off nolapic noapic

EDIT: If that doesn't help, reboot the computer and try typing this instead:

linux failsafe

---

### Post by renzuken on 2005-11-14
This is getting very weird.

Now whenever I try and boot the install disc, the kernel doesn't load.
It keeps coming with the error:

'Kernel panic - not syncing: No init found. Try passing init= option to kernel.'

I've tried putting in that command to the ubuntu screen and still that error pops up.

---

### Post by SickTwist on 2005-11-14
You mentioned that you tried downloading the Ubuntu ISO file several times. Could you verify that you downloaded the correct one for your computer architecture. There are three flavors of Ubuntu: PowerPC (for Apple hardware), AMD64 (64 bit processor), i386 (most common, Intel PI thru PIV, AMD Athlon & Duron, etc.). If you're not sure which one you need, tell us more about your computer (brand, model, processor) and we'll help you figure it out.

Once you are sure you have the correct ISO file, do an md5sum check to verify that it downloaded correctly. This step is important to isolating the problem. There is an md5sum program for Windows available [here]("http://www.etree.org/md5com.html"). Once again, let us know if you need assistance with this. Basically the program will give you a number that should match the number in the md5 file that is in the same area from which you downloaded Ubuntu.

Burn the ISO file on a CD-R. CD-RW media will give problems sometimes. Burn it at a slow rate (but not slower than your drive or media is designed for). Do not run any CPU intensive programs while doing this (MP3 player, virus scanner, etc). If you are using Nero to burn or something similiar, there should be an option to "Burn From Image" or "Burn from ISO". That is what you should be using. Do **not** select "Burn as data CD" or you'll end up with a data CD that only contains the ISO file that you downloaded.

Use the boot parameters that I gave in my earlier post to boot the Ubuntu install CD.

When you get to the partitioning screen in the installer, press the Escape key. You will see a menu that lists the various steps of the installer. Use the arrow keys to move down the list to select "Check the CD-ROM(s) integrity" and press Enter. If this process fails then there is most likely a problem with your optical drive and it might need to be replaced. If it succeeds, the installer will return to the partitioning step.

---

### Post by recce101 on 2005-11-14
You might want to try the previous version, 5.04 (Hoary). I've installed or tried to install many different Linux distributions over the past 3-4 months, and Ubuntu 5.04 is far and away the best I've found. Detects all my hardware on both machines every time, fast installation with no hangups, very stable and predictable. This weekend I installed Hoary on four separate partitions on the same computer to test various configurations. Not a hitch. On the other hand, every attempt to install 5.10 has been a real hassle. I've managed to succeed only twice, but then other issues cropped up and I once again went back to 5.04. Eventually I'll "upgrade" one of the Hoary installations to Breezy via the apt-get routine, but I've got plenty of exploring to do before I feel compelled to do that.

---

### Post by renzuken on 2005-11-14
I checked the cd, made sure the burn was fine ( I let it burn at 2x to make sure) and then left it for 30 mins with no apps running to let the disc write. Popped it into my computer (which is a P3 750mhz so I downloaded the i38 version) and it still gives me the 'kernel panic' error and then freezes. 

I'm wondering if this is now a problem with my HD or it's just a simple CD fault.
I'm also considering trying the previous release to see if it will install through easier and then consider an upgrade after.

Edit:

I tried booting with a kubuntu disc to see if it was just that particular image/disc/setup and I've ended up with the identical error.

The ubuntu screen comes up and once I press enter it fails to load, the last few lines of the error are:

> [4294672.864000] Freeing unused kernel memory: 224k freed
[4294672.864000] EXT2-fs error (device ram0):ext2_check_page: bad entry in directory #415: rec_len is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
[4294672.864000] Warning: unable to open an initial console.
[4294672.864000] EXT2-fs error (device ram0):ext2_check_page: bad entry in directory #373: directory entry across blocks - offset=936, inode=373, rec_len=1012, name_len=2
[4294672.864000] EXT2-fs error (device ram0):ext2_check_page: bad entry in directory #209: rec_len is smaller than minimal - offset=0, inode=786432, rec_len=3, name_len=97
[4294672.864000] Kernel panic - not syncing: No init found. Try passing init= option to kernel.
[4294672.864000]


---

### Post by SickTwist on 2005-11-15
I really don't think that it has anything to do with your hard drive. Those errors are occuring before the hard drive has even been detected. It is possible that the CD-ROM drive is dying, the wrong driver is being loaded for the CD-ROM drive, and/or the drive is not compatible with the way that the Ubuntu CD has been formatted.

If you try booting from any other Linux CD besides Ubuntu and you still get errors then it is most likely the CD-ROM drive.

---

