---
title: "Installing Ubuntu on Lenove machine without removing Windows installer"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by alex275 on 2014-10-10
I bought a new Lenove Laptop and I want to run Ubuntu as main OS. So that means I'd like to remove the existing Windows installation but not the installer itself. Lenovo Laptops come with a kind of installation partition I think. I guess I just should not remove this partition and I'll be fine, right? I want to double check becausse I did this already once and anyhow it didn't work out. The installer was gone what really pressed the reselling price down a bit.

---

### Post by sudodus on 2014-10-10
Welcome to the Ubuntu Forums :-)

In order to be 100 % sure that you can restore Windows, you should

1. Get a second HDD with at least the same size.

2. Create media for restoration
a. Clone the drive with the current (original) Windows to the second HDD
b. Create rescue disk(s) of Windows
c. Rely on the installation partition that comes with Lenovo laptops.

3. Remove the current drive and replace it with the second HDD.

4. Test
a. Check that the cloned copy works
b. Restore Windows from the rescue disk(s)
c. Restore Windows from the installation partition that comes with Lenovo laptops.

Without a tested method, you don't *know* if you can get Windows back. Only *you* can decide if it is worth the effort.

---

### Post by yancek on 2014-10-10
I don't use a Lenovo but those are usually Recovery partitions and when you initially boot the computer you are prompted to create a Recovery CD.  You can create it later if you haven't already and when used will set it back to factory defaults and overwrite any data you have on it so you need a backup in any case.  The partition should be labelled in some fashion if it is not called Recovery partition so you know which one it is.  Having a backup as suggested above is probably a better option.

---

### Post by oldfred on 2014-10-10
One user posted he never boots the Windows hard drive. He does replace hard drive with new SSD with just Ubuntu. Then when he later sells laptop, he restores Windows drive which has none of his data and is like 'new'.

But do make backups and images of Windows recovery partition. There is a bug in the Ubuntu installer that if it does not show Windows, then it erases entire drive including Windows & recovery. Only safe way to install is to use Something Else.

       Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

