---
title: "Dual booting Windows with two HDDs."
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by Kehlan_Rutan on 2014-12-10
OK, so I have a 1TB hard drive that is currently my C:/ in windows and I have a 500GB as a Secondary.  

I my goal is to have the 1TB for Windows and the 500 for Ubuntu.  When I go to install Ubuntu it looks like it only recognizes the 500 gig (which is good) but it says I have Windows installed on it.  I tried pulling out the Sata of the 1TB and running it again and it still says that Windows is on the 500.  

Does Windows put a packet or something on there and that is what it is recognizing?  Can I just Choose the Duel Boot Option and then Allocate all but like 10 gigs to Ubuntu?  It seems odd to me.

---

### Post by Kehlan_Rutan on 2014-12-10
It should also be noted that my 500 gig HDD is empty.

---

### Post by oldfred on 2014-12-10
Windows does install a Boot partition to which ever drive BIOS reports as the boot drive. If the 500GB drive was the boot drive then even though Windows is on the 1TB drive, its (hidden in Windows) Boot partition may be on the other drive.
Is system newer UEFI or BIOS. And then is Windows installed in UEFI or BIOS boot?

Post this from Ubuntu live installer:
sudo parted -l

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Kehlan_Rutan on 2014-12-11
Awesome thanks.

---

### Post by Mark Phelps on 2014-12-11
IF the windows boot loader is on the 500GB drive, you can copy it to the other drive using EasyBCD from NeoSmart Technologies.

Once installed, start EasyBCD, click the BCD Backup/Repair button, under BCD Management options, choose Change boot drive and click the Perform Action button.

Once that's done, disconnect the 500GB and confirm you can boot from the Windows drive.

You can then install Ubuntu to the 500GB drive.

---

### Post by Kehlan_Rutan on 2014-12-11
Well f.  I got Ubuntu on my computer but lost Windows.  And that is why we back things up people.  
I verified that the boot loader was on the secondary (500 GB).  I used EasyBCD to move it.  Unplugged the 500 and booted right into windows fine.  So, I unplugged the 1TB and plugged back in the 500 and ran Ubuntu.  It still said that there was windows on the 500 gig but I thought I was safe since the boot loader was on the 1 TB.  So, I chose the option to not duel boot only do Ubuntu.  I went through the process and everything seemed fine.  Then, to make sure that Windows was fine I booted from the 1 TB.  But now I get a Grub Recovery error.  

Did I lose everything?

---

### Post by Mark Phelps on 2014-12-11
Doesn't make sense ... 

You were able to boot the 1TB containing Windows by itself, right?  

Then, you installed Ubuntu to the 500GB, with the 1TB disconnected. Right?

Now, when you boot from the 1TB again, it won't boot into Windows? Does it do this when the 500GB is disconnected?

Ubuntu install could not possibly have written to the 1TB Windows drive while that drive was disconnected

---

### Post by oldfred on 2014-12-11
Post link to summary report, do not run auto fix as that install grub everywhere, you want to keep a Windows boot loader on the Windows drive:

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

