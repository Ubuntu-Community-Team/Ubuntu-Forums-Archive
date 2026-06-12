---
title: "Steps to Add Dual Boot Windows10 + New Drive to Existing Ubuntu Machine"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by subject117 on 2015-11-18
I have a working Ubuntu 15.04 machine with two hard drives, /dev/sda and /dev/sdb. The boot partition is located in /dev/sda1.

I would like to make the machine dual boot Windows 10. I bought a new SSD for Windows 10 and will install windows on the new drive, /dev/sdc. 

What is the best way to go about what I want to do? Is there anything I need to know about when I install Windows on the new drive?

After I install Windows, I know I need to update grub. Should I install a new bootrecord on /dev/sdc with grub-install, or update/modify the one on /dev/sda? How do I tell grub about the existence of Windows on /dev/sdc? Is it just a matter of running update-grub? That scans all the drives and figures out what is bootable? Will I need to mount /dev/sdc first?

Thank you

---

### Post by Vladlenin5000 on 2015-11-18
I never did it what you're asking but logic tells me the easiest and less prone to issues method is as follows:

1. Disconnect all your current drives;
2. Connect only the new SSD;
3. Prepare a USB flash drive with Windows 10 with the Microsoft's official tool or, even better, with Rufus.
4. Boot from the drive created in #3 and install as usual in the single drive;
5. Reconnect the other drives in the same order as before (the new SSD with Windows should come after the others);
6. Boot to Ubuntu - at this point GRUB is still unaware of the new OS -;
7. Run update-grub and it should find the new OS and add it to the list.

---

### Post by subject117 on 2015-11-18
OK, that's roughly what I was thinking of doing but I assumed there was more to it. I don't know much about grub and I am afraid of messing up my machine.

---

### Post by Vladlenin5000 on 2015-11-18
I don't know much either ;-) but I suppose the worst case scenario is Windows not booting in the dual boot setup.

---

### Post by yancek on 2015-11-18
One possible complicating factor that you did not mention is whether Ubuntu is installed using UEFI or MBR.  Windows needs to be the same method or you will have trouble booting one or the other.  If you are using GPT partitioning, you will need to use UEFI for windows as I understand it. It might make a difference if they are installed on separate drives but I'm not really sure as I don't use UEFI.

---

### Post by subject117 on 2015-11-18
According this:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[INDENT]
Boot mode matching -- If you're dual-booting with another OS, the two OSes' boot modes should match. Most computers that ship with Windows 8 and later use UEFI to boot that OS, so this configuration dictates use of UEFI mode when installing and booting Ubuntu.[/INDENT]

The boot modes must match. Thank you for mentioning this.

I looked in the BIOS of my computer and it has references to UEFI, but when I check for the existence of the /sys/firmware/efi file I find it is not there. Does that mean that I am not using UEFI?

According to this:

[http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

I should pick MBR and not GPT when installing Windows 10.

---

### Post by grahammechanical on 2015-11-18
>  I should pick MBR and not GPT when installing Windows 10.

My motherboard has a BIOS boot system and not UEFI but I can still have GPT as the partition table and not msdos partition table. The disadvantage of an msdos partition table is that there is a 4 primary partition limit. That means that to have more than four partitions we have to use one of the primary partitions as an extended partition and the inside the extended partition create logical partitions.

The 4 primary partition limit does not apply to the GPT partition table. Actually, I have two hard disks - one msdos and one gpt. No problems.

Regards.

---

### Post by subject117 on 2015-11-18
VICTORY

It worked! I now have a dual boot machine. Thank you everyone for your support.

The steps I followed were very similar to what Vladlenin5000 listed:

1. Prepare a USB flash drive with Windows 10 with the Microsoft's official tool or, even better, with Rufus.
2. Disconnect all your current drives;
3. Connect only the new SSD;
4. Boot from the drive created in #3 and install as usual in the single drive;
5. Reconnect the other drives in the same order as before (the new SSD with Windows should come after the others);
6. Check BIOS to make sure the original boot drive is first in the boot order
7. Boot to Ubuntu - at this point GRUB is still unaware of the new OS -;
8. Run update-grub and it should find the new OS and add it to the list.

And it just worked. I was expecting much more frustration.

When I ran update-grub I saw this:

...
Found Windows Recovery Environment (loader) on /dev/sdc1
done

That's the name I see in grub. Is it possible rename that to "Windows 10"?

---

### Post by oldfred on 2015-11-18
Grub2's os-prober has not been updated to find Windows 10. It searches for known names and when not found seems to just call it a recovery enviroment.

You can manually create your own boot stanza in 40_custom with any description your want. Once that works you can turn off os-prober so you do not get the incorrect entry.

       One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.
[http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910](http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910)

   Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Once your manual entries work, turn off os-prober by adding this line  to /etc/default/grub configuration file to get grub from adding entries  automatically. You can turn on with false again if you add another  system and want it to find it.
  gksudo gedit /etc/default/grub

GRUB_DISABLE_OS_PROBER=true

sudo update-grub

---

