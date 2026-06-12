---
title: "Installing onto another hard drive from &quot;inside windows&quot; installation"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by BioElectro on 2011-05-26
First, a little background:

Laptop at issue: Toshiba Qosmio G25-av513
CD/DVD drive: Matshita DVD-RAM uj-845s

I attempted to do a proper install of Ubuntu 11.04 via booting of off CD.  This failed because my CD/DVD drive is quirky and does not like burned CDs, though it likes factory pressed CDs just fine.  I reattempted using a burned DVD, which almost worked, but my quirky drive just couldn't quite handle it.  Replacing this drive is currently not an option, as I have no money for such things at this time.  I updated the CD/DVD drive firmware to 102D (apparently the most recent), but to no avail.  I am comfortable with tearing apart electronics, so if anyone has knowledgeable suggestions about any kind of maintenance I could do to the drive I would be happy to hear it.  Also, a (cheap!) factory pressed Ubuntu CD could work as well.  Are such things available?

I further attempted booting via flash drive, but this failed as well, despite changing BIOS settings.  If anyone has any useful suggestions on this, I would be happy to hear them.

I attempted installation within Windows XP and was successful, though this is not an optimal solution.  I have a second 60GB hard drive in this laptop that I would like to devote to a proper installation of Linux.  It seems like I should be able to do this from within the current Ubuntu installation, but I am unsure of how to proceed.  Can anyone be of assistance?  Thanks.

---

### Post by Hedgehog1 on 2011-05-27
When you created the LiveUSB (I am thinking this is your best option), did you create using **unetbootin** [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") ??

If not, please use that to convert the ISO into a LiveUSB, and then install using that.


***The Hedge***

:KS

---

### Post by BioElectro on 2011-05-27
I've now tried the unetbootin option.  My computer will still not boot from flash drive, though I am thinking that it is old enough (2005) that the FDD option in the BIOS means "Floppy DisK Drive" (even though my computer does not have one), and perhaps will simply not boot from a flash drive at all.
 
Though the flash drive option did not work, I used the "Hard Disk" option in unetbootin and successfully installed on my second drive.  However, I did not get an Ubuntu option on the boot menu.  There was only Windows XP and Unetbootin.  If I uninstalled Unetbootin from within Windows, there was then no boot menu whatsoever.  I've retried and reinstalled using this method several times now, each time with the same result.  Sometimes I would notice an error to the effect of "Unrecognized partition table on drive 81" with a message to rebuild using an fdisk (I think) compatable utility.
 
I've even gone as far as completely reinstalling Windows XP using the Toshiba/Microsoft recovery disks, which supposedly reset everything to factory settings.  Still, I get the same results and the same "Unrecognized partition table" error.
 
So, I am now at a bit of a loss.  Can anyone assist with this issue, or with any of the things that I mentioned previously?

---

### Post by Hedgehog1 on 2011-05-27
I would agree that you system does not appear to boot from USB.

The correct installation would then be from CD; but your CD drive is not operational.

Can you remove the second drive from the laptop and use a different computer to install Ubuntu on the drive? And then return it to you laptop?  This would allow you use the BIOS 'boot selection' to a hard drive to boot from (Windows or Ubuntu).

Without a functional CD drive, this is really rather difficult.


***The Hedge***

:KS

---

### Post by BioElectro on 2011-05-28
No, I don't have another computer I can put this particular hard drive in.

However, (after much angst and googling) I have solved my issue.  I am now running a functioning, proper install of Kubuntu 11.04.  Now that I have this, I should be able to do everything else I need without nearly as much difficulty.  Details of my travails below for posterity's sake in case anyone else should have similar problems:

Using [UNetbootin]("http://unetbootin.sourceforge.net/"), I installed [Parted Magic]("http://partedmagic.com/doku.php?id=start") using "Hard Disk" method.  I resized my Windows XP partition, giving myself about 10GB free space.  Reboot.  I let Windows do its little self diagnostic thing, as it noticed it suddenly had a smaller partition.  Everything checks out, autoreboot.

Boot into Windows, run UNetbootin again, which uninstalls Parted Magic.  Run UNetbootin again and install Kubuntu 11.04 using "Hard Disk" method.  Reboot.

Select UNetbootin at boot screen.  Kubuntu loads as it would from an installation CD.  At the "Prepare Partitions" section, harrowing troubles await.  After setting up your partitions and clicking "Install Now," one receives the following message:

-----------------------------------------------------------
The installer needs to commit changes to partition tables,
but cannot do so because partitions on the following could
not be unmounted.

/cdrom

Would you like the installer to try to unmount these partitions again?

Go back/Continue
-----------------------------------------------------------

No matter what you do here, the installation halts.  To avoid this, BEFORE clicking "Install Now," switch to a terminal screen [CTRL][ALT][F1] and enter the following command:

sudo umount -l -r -f /cdrom

After doing this (return to your GUI screen with [CTRL][ALT][F7]) and clicking "Install Now," you must return to the terminal screen and enter:

sudo mount /dev/sda1 /cdrom

You only have seconds to do this, so have it set up and ready to go.

Note, your device may be different from "sda1."  This is the device that your Windows installation is on.

You must remount this device because the Ubuntu installer is running from here.  If you do not remount, the installer will crash when it tries to copy files from here.

This is a bug that has existed for some time.

From this point everything went fine.  Though when finished, (if you plan on keeping your Windows installation) you can reboot into Windows and run UNetbootin again to get rid of the UNetbootin option from the Windows boot screen.  Personally, I've decided to eradicate Windows entirely and go straight Ubuntu, only running Windows virtualized when I need it using [VirtualBox]("http://www.virtualbox.org/").  Hopefully, getting that working won't be nearly such a pain in the ***.

Incidentally, if you happen to have a similar laptop to mine, you may notice that the screen brightness is blinding and that the normal brightness controls do not work.  If you have installed the non-free NVIDIA driver, this can be adjusted with [FN][F6] and [FN][F7] (my laptop has a GeForce Go 6600).

***EDIT***

I forgot to mention - I resized and installed to the first hard drive rather than the second because Linux (sometimes?) has issues when it has no partition on the first drive.

Happy computing.

---

### Post by Hedgehog1 on 2011-05-28
**Now THAT qualifies as a real adventure!**

Congratulations on getting to where you wanted to be!


***The Hedge***

:KS

---

