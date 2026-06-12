---
title: "Installing Ubuntu on HP Envy-6"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by nlif on 2013-03-09
Hi all,

I would like to install Ubuntu on a brand new HP Envy 6, with pre-installed Windows 8. However, in the certified hardware list, I don't see the Envy 6.

Does this mean it won't work?
Does this mean it might work, but will lots of tweaking and patching?

Also worth noting, I am not an expert on Ubuntu, or Linux in general. So, if this is very complicated, and requires lots of Linux know-how, I might reconsider.

I'd appreciate any advice.

Thanks.

---

### Post by fiodev on 2013-03-09
It should work just fine. Can you boot into the Live CD of Ubuntu and does it work fine? If yes go ahead install and enjoy the freedom of linux.

---

### Post by Mark Phelps on 2013-03-09
Some HP envy PCs come with Hybrid Graphics -- which does not work well at all in Linux -- hence the advice to try it in LiveCD mode first, to ensure that it detects all your hardware and confirm that all your devices work properly.

---

### Post by oldfred on 2013-03-09
If Windows 8 is pre-installed then you also have secure UEFI boot.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by nlif on 2013-03-11
Thanks.

I created a usb using Lili usb-creator, and the ubuntu secure remix 64bit.
I rebooted from USB, chose "try without install", and Ubuntu starts fine.
However I don't see my wireless network.
I was able to connect via my phone, though, for what it's worth.
(Of course, I am able to connect to wireless in Windows, so the hardware itself works).

Any advice?

Thanks

---

### Post by oldfred on 2013-03-11
There are a lot of threads on wireless issues. I have never had any, so I have not followed them. 

Search forum based on you model or start a new thread with wireless & model in the title.

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Now post a reply  and attach (via the paperclip) the abs-network.txt file which will be in your home folder.

---

### Post by nlif on 2013-03-16
Thanks, I have attached the file.
Just to be clear, though, at thsi point, I am booting Ubuntu from a USB, and do not have it installed.
I wanted to try before I install. Then again, I would not expect that to make a difference with regards to the wireless.

---

### Post by oldfred on 2013-03-16
I have seen a lot of threads on this brand but it varies by model.
Since you have not installed, have you looked in System Settings to see if it offers to install a driver?

Atheros Communications Inc. AR9565 Wireless

---

### Post by nlif on 2013-03-23
Ok, putting the wireless issue aside for the moment, I wanted to go ahead and install it.

I boot from the USB, and select "install".
However, the "installation type" dialog I get is different from what is shown in the tutorials. Instead of options: "Install Ubuntu alongside others", "Erase the disk and install Ubuntu" or "Something else", what I get is an empty list of devices (i.e. no devices at all). This doesn't seem right... what is going on? Did I miss a step? Should I have started by booting from Windows and creating a partition?

More generally, I've tried searching the web, but surprisingly, I cannot seem to find an installation tutorial that matches what I see...
Is there an installation guide, for installing Ubuntu 12.10 (64bit) on a machine with Windows 8?

Thanks again.

---

### Post by oldfred on 2013-03-23
Is it also an UltraBook with Intel SRT? That uses RAID which adds another level of complication. 

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Brand of computer is not critical as it is an Intel Standard.
      
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Quotes from several users:
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.


  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

      
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by nlif on 2013-04-01
Solved!

I managed to install Ubuntu 12.10 along with Win8, and also found a solution to the wireless problem.
Based on posts from this forum, here's what I did:

1. I prepared a USB-stick with 64bit Ubuntu 12.10 and Boot-Repair.
2. From Windows, I created a partition, by shrinking the primary windows partition.
3. Booted from USB, and chose - Try Ubuntu.
4. Opened a terminal and disabled the RAID as described above.
5. Started the intstaller, and chose: "something else" as installation type.
6. Created the root and swap partitions, on the empty space created on step #2.

At this point, I had Ubuntu working, but no GRUB. That is - when booting the machine, it would start Windows, unless I hit ESC and chose to boot from Ubuntu.

Fixing this:

1. I started Ubuntu, and ran Boot-Repair, and did a "recommended repair".
2. When I was done, and rebooted, I got the GRUB (I think that's how it's called..) menu, with lots of options. However, none of the Windows options worked.
3. This was fixed by going to the EUFI settings and disabling "secure boot". I am not an expert on this, and I am not sure what the implications are, but it seems to have worked, and now both Ubuntu and Windows work.

Fixing the wireless: (I found this [here]("http://step4wd.com/2012/12/28/fix-atheros-wifi-for-ubuntu-12-10-on-hp-envy-ultrabook/"))

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic


Thanks a lot for all the help!
 This was a bit of a challenge :)

---

### Post by oldfred on 2013-04-01
Glad you resolved it. :)

With the new UEFI and some of the new hardware configurations, it can be a real challenge to install any other system.

---

