---
title: "Dual boot Windows 8 and Ubuntu on Different Drives"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by holiday_hawk on 2014-07-28
[COLOR=#333333][FONT=Verdana][FONT=Lucida Grande]Hi, my laptop contains two hard drives, both just under 1000 gigs. I'd like to dual boot both Windows 8 (what I'm currently running) and Ubuntu, but instead of partitioning one of the drives I'd like to dedicate one hard drive to each OS. I've seen tutorials for how to dual boot, but most of them explain how to do so on one hard drive. The few I've seen for how to do it using a secondary hard drive aren't very straight forward, and left me slightly confused. Can someone explain how to do this to me in a simple, straight forward? way Also, will I be able to choose which OS to boot at startup, if not how would I select which OS to boot? Would there be an easier way to run both OSes on my computer, than dedicating a drive to each one? Thanks in advance![/FONT]
[/FONT][/COLOR]

---

### Post by oldfred on 2014-07-28
Is system new UEFI or configured for older BIOS.

If Windows 8 was preinstalled then it is new UEFI and you have to have gpt partitioning on both drives.
You also want Ubuntu in UEFI mode for easier dual booting.

Some suggest disconnecting Windows drive so Ubuntu only installs to second drive. But you can do it if you include efi partition on the second probably sdb drive and install grub2's boot loader to the sdb drive. You only get the option on where to install grub2 boot loader with the Something Else install option.

Still always a good idea to fully backup efi partition and all of Windows. And make a Windows repair flash drive. Details in link in my signature if not sure how.

How you boot installer, UEFI or BIOS is how it installs, so you must boot in UEFI mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    UEFI install,windows 8 with Something Else screen shots, with second drive you just choose that instead.
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Other Something Else. Main difference with UEFI vs BIOS is with UEFI you have gpt partitioning and the efi partition for efi boot files (it is not the /boot partition). And you generally do not want a separate /boot partition although some examples show that.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

   Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

Attached screen shots are my BIOS, but I have an efi partition for future use and use gpt partitioning in third screen shot for install to my SSD. I am reusing an older / partition that was 12.10 and installing 14.04.

---

### Post by holiday_hawk on 2014-07-28
Thanks for your help, I've got it all set up!

---

