---
title: "Ubuntu 10.10 Dual boot Windows 7"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by ammw999 on 2012-09-02
Ok so heres what i want to do i have a amd laptop with two hard drives 1 is 500gb the other is 250gb, I want to install ubuntu on the 250gb drive currently the drive is empty the 500gb drive is my windows 7 main i dont want it touched in the installation now ive read other threads about dual booting 2 drives but they dont give clear answers for me to take the risk. I had another laptop that i did install ubuntu with windows on same hard drive i and it worked but when i deleated ubuntu my boot mgr was missing and now the comp is garbage i want to avoid that with this laptop so my boot mgr i need untouched. If possible it would be nice if i can get step by step instructions during the installationg so i dont muess up.

---

### Post by oldfred on 2012-09-02
Welcome to the forums.

You do know that 10.10 is not supported any more?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Many suggest physically disconnecting the Windows drive. Then you are absolutely sure.

But if you use manual install, you can choose all the partitions and particularly the combo box which lists the drives and then you choose to install the grub2 boot loader to the MBR of the Ubuntu drive and then set BIOS to boot the Ubuntu drive.

Herman has lots of detail but has changed to the Alternative or text based installer. Actual procedure of installing is very similar, just screens are not as 'pretty' or gui-fied. See last link which highligts combo box on where to install the grub2 boot loader.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. 
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

