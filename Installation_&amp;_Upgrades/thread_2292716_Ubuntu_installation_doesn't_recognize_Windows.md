---
title: "Ubuntu installation doesn't recognize Windows"
date: 2015-08-30
forum: Installation &amp; Upgrades
---

### Post by matan5 on 2015-08-30
Hi, 

I have Windows OS on my computer, and I want to install Ubuntu alongside Windows. I use bootable USB and the installation of Ubuntu is running. Still, when I have to choose the installation mode, it doesn't recognize that I have windows and my only option is to erase the whole disk. Do you know what can be the problem ?

---

### Post by yancek on 2015-08-30
If you only have the option to "erase disk" I would say it is time to stop.  You might have a bad download of the Ubuntu iso or the creation of the bootable iso didn't work.  I believe you should always have the "Something Else" option which is the manual install.  If you were to select the "Erase Disk" option it's going to overwrite anything currently on the computer.

Other possibilities, since you neglected to mention which version of windows you are using, two many partitions already on the hard drive and therefore unable to create another resulting in the erase disk option.  Boot the Ubuntu install flash drive and open a terminal, then run this command and post the output here:  sudo parted -l(Lower Case L in the command).

---

### Post by dangerjunkie2002 on 2015-08-31
Hi Matan,

Does your machine have Intel Rapid Storage Technology (RST)? I just bought my first machine that does and I had what sounds like the same problem. The installer said I had no OS installed and, if I went to manual partitioning, the partitioner displayed more drives than the machine physically has (multiple copies of the same drives with different names). How many physical discs and SSDs does you machine have and, if it has RST, are you actually using it or is it just switched on by default?

I understand the reason the installer can't make proper sense of the drive is that the standard Ubuntu disc doesn't yet come with Intel RST support pre-installed but that this may be possible. I didn't look into whether any of the discs had this though I suspect the server disc may be better. You could possibly install Ubuntu server then add the ubuntu-desktop package to turn it from command-line into a graphical environment. I used a work-around and got over this the lazier way, My machine did use Intel RST (it had two 128GB SSDs rather than the advertised single 256GB one and used the Intel RST to make them appear as one drive with RAID 0). I sorted this by buying a larger SSD, replacing the factory ones with it then changing the disc mode from RAID to AHCI in the BIOS which took the Intel RST out of play. The install disc then recognised all the drives normally.

Unfortunately, Windows installs its disc drivers at first boot and doesn't scan for the storage hardware every time the machine comes up. This results in Windows blue-screening if you change the hard drive mode as above. I solved this problem by making a Windows USB recovery stick using the manufacturer-supplied utility (It was a new machine and there wasn't anything on it so I didn't mind flattening Windows and reinstalling.) The process I used as as follows: WARNING - This process will result in the loss of all your documents and files in Windows - Make sure you back up anything you want to keep.

    * Do the Windows first-run and get it going.
    * Make a USB Windows recovery stick using the supplied Windows utility (You can skip this if your machine came with physical Windows recovery media)
    * Remove the old drives and replace them with the larger one(s) (Not necessary if you only have one drive and wish to continue using it)
    * Enter BIOS setup and change the hard drive mode from RAID to AHCI.
    * Boot the machine from the Windows recovery media.
    * Perform a Windows recovery onto the desired drive (In my case one of the new SSDs)
    * Boot Windows and go through the first run and setup. This installs it in AHCI mode and it will then work.
    * Perform the Windows 10 upgrade if necessary/required/eligible.
    * Make sure you've done at least one boot of Windows and shut it down properly.
    * Boot from your Ubuntu install media.
    * Proceed with your Ubuntu installation as normal.

All the best,
Paul.

---

### Post by Bucky Ball on 2015-08-31
Welcome. Windows is probably installed in EFI mode. You will need to install Ubuntu in EFI also and use 'Something Else' when you get to the partitioning section. First ...

Boot into Windows> Switch off hibernation and faststart> restart to the BIOS and switch of secureboot. Reboot to the USB. Can you get further now? Is the Win partition visible?

If Windows in hibernation Ubuntu will not be able to see or access the partition. If this is the case, go no further until it can. Good luck.

---

