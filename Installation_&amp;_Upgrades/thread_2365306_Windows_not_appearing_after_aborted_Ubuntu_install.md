---
title: "Windows not appearing after aborted Ubuntu install"
date: 2017-07-05
forum: Installation &amp; Upgrades
---

### Post by raghulrajan on 2017-07-05
Hi to all, I tried to install Ubuntu latest LTS. I aborted after allotting partition (I had some doubts). Then when I restarted only a blank screen with a blinking cursor appears. So can someone help me to find windows 10 again on my Dell PC?  No cd available with me.Thanks. Raghul.

---

### Post by oldfred on 2017-07-05
If making major changes to your system, the first thing you do is a full backup. Which really should be just an update to your normal regular backup.
And then you make a Windows repair/recovery flash drive. This should have been done the first time you booted system or whenever you update to newer version.

Ok, little late to close barn door, as the horse is already out. (old farm saying).

Is system older BIOS, or newer UEFI?
What model Dell?

If you did not complete install, it should not have installed the grub2 boot loader and Windows boot loader should still be there.
Also have you tried f12 as soon as you start system. That should give you UEFI/BIOS boot options and then you can choose Windows.
If you choose Windows and it still does not boot, then you need to repair Windows with your Windows repair flash drive, or see if f8 gets you into Windows repair console as soon as you select Windows to boot from UEFI/BIOS.

Most Windows repairs cannot be done from Linux. And no Linux repairs can be done from Windows.
From Ubuntu live installer booted in Live mode, post this using terminal.
sudo parted -l

---

### Post by raghulrajan on 2017-07-09
The model of the laptop is Inspiron 15 7000 Gaming. It is the latest model. Only F12 & F8 are working. Boot mode set to Legacy. Ubuntu live installer not working. Only a blank screen with a blinking cursor appear. I aborted Ubuntu after making a partition for 500 GB because I was not able to understand the forms. I thought installation would be easy as in 12.04. Thanks for the reply. Raghul

---

### Post by oldfred on 2017-07-10
It looks like that also has a nVidia card which adds some complication. You need nomodeset to install & first boot or until you install nVidia driver. You may need ppa to get newest driver, do not install directly from nVidia.

Does it have RAID or Intel SRT type setting turned on? Most Dells have RAID on even if one drive, but must have it off for Ubuntu Desktop to install correctly. If Gaming system, it may be RAID 0 which is not recommended for any system other than one you do not care about data. That also means half of data is on one drive and half on other drive. You then must have good backups if you turn RAID off.

Is drive newer NVMe drive also? Some have had to update firmware & Dell UEFI.

Since new UEFI system, you may need to install in UEFI mode to get full driver support for all the very new hardware.
See link below in my signature for general UEFI install.

Some similar Dellsystems issues are often command across models of same brand:
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)

       
 Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en) 
           
 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/) 
           
 Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[URL="https://ubuntuforums.org/showthread.php?t=2345444"]https://ubuntuforums.org/showthread.php?t=2345444

[/URL]       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
     Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
    [URL="https://ubuntuforums.org/showthread.php?t=2345444"]
[/URL]

---

### Post by raghulrajan on 2017-07-13
Thank you very much for the elaborate reply. I downloaded windows recovery image from dell site & restored the OS. But there are few issues. Though I formatted TPM(partition module), The 500 GB partition I dedicated to Ubuntu still seem to be dedicated for Ubuntu, because Windows hardware space is still appearing with 500 GB reduced. Every time I boot the OS, I have to press F12 & select UEFI-Windows boot manager, otherwise "Real tek media message" appears & continuously restarts. I want to recover all 1TB space to windows & then reinstall Ubuntu 16.04. Can you provide some suggestions for this purpose? Thank You. Raghul

---

### Post by oldfred on 2017-07-13
You should not need to recovery the Windows space if you are still installing Ubuntu.
Windows will not see nor be able to use Linux partitions, but Linux has a good NTFS driver that will see NTFS partitions if not hibernated nor if fast start up is on.

But use Windows own tools for any resizing of the Windows NTFS partitions. And immediately reboot so it can run chkdsk which is required after any resize.

For general UEFI install instructions see link below in my signature.

---

### Post by raghulrajan on 2017-07-15
> **oldfred said:**
> You should not need to recovery the Windows space if you are still installing Ubuntu.
Windows will not see nor be able to use Linux partitions, but Linux has a good NTFS driver that will see NTFS partitions if not hibernated nor if fast start up is on.

But use Windows own tools for any resizing of the Windows NTFS partitions. And immediately reboot so it can run chkdsk which is required after any resize.

For general UEFI install instructions see link below in my signature.


[ATTACH=CONFIG]276014[/ATTACH]Installation doubts contd.! The picture above shows "free space" 500000 MB. I think it is 500GB. So how much I can allot for for Root,Swap & Home now. There are also other options like var, opt,usr. Why there are no default values? This could be very confusing for new immigrants like me? Please mention values for root etc.  in MBs because I am confused by the zeros. My RAM is 16 GB. Thanks!

---

### Post by vasa1 on 2017-07-15
> **raghulrajan said:**
> Thank you very much for the elaborate reply. I downloaded windows recovery image from dell site & restored the OS. But there are few issues. Though I formatted TPM(partition module), The 500 GB partition I dedicated to Ubuntu still seem to be dedicated for Ubuntu, because Windows hardware space is still appearing with 500 GB reduced. Every time I boot the OS, I have to press F12 & select UEFI-Windows boot manager, otherwise "Real tek media message" appears & continuously restarts. I want to recover all 1TB space to windows & then reinstall Ubuntu 16.04. Can you provide some suggestions for this purpose? Thank You. Raghul

People will be able to help you better if you're clear about what you want to do.

Do you want to have a pure Ubuntu system? Do you want to dual-boot (Win10 & Ubuntu). You may have mentioned these things before but do make things clear again.

From the post of yours which I've quoted, I'm guessing you have an interest in dual-booting.

---

### Post by raghulrajan on 2017-07-15
Sorry for the confusion. I want dual boot! Windows 10 is preinstalled. The Dell inspiron 7567Gaming  is the latest model! (Specs-Intel Core i7-7700HQ, 1x 16 GB DDR4,1 TB HDD + 256 GB SSD,Nvidia GeForce GTX 1050 Ti). Thanks!

---

### Post by oldfred on 2017-07-16
1GB is a 1000MB and 1MB is a 1000KB.
Giga, Mega, Kilo prefixes.
But some use base 10 and some use base 2.
[https://en.wikipedia.org/wiki/Binary_prefix](https://en.wikipedia.org/wiki/Binary_prefix)

Ubuntu's default install is just / (root) & swap. 
My / in my 16.04 install is up to 8GB used in a 25GB partition, but I have all data normally in /home in another data partition that is 116GB, but I have little music and no videos. Or not a lot of large files.
My old original BIOS system had Windows XP on one drive and Ubuntu on another & I created a shared NTFS data partition so I could have some data easily seen in both installs. I now do not have Windows but have several Ubuntu installs so use a larger Linux formatted ext4 partition for my shared data.

I suggest 25 to50GB for / (root) if you create either a separate /home partition and/or separate /mnt/data partition. If a newer user separate /home is a lot easier to set up as you do it during install. If brand new user, you can just use / but then need to make it larger as your Linux data will be in /home inside /.
With 16GB of RAM you may never use swap, but I still suggest some like 2GB. The only reason some may suggest 16GB (or more) or swap would be if you hibernated. But Ubuntu boots fast & hibernation does not always work well, so best not to use hibernation with Ubuntu.

More details of UEFI install instructions in link below in my signature.

---

