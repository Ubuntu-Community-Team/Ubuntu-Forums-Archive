---
title: "Ubuntu wont't boot after installing Windows 10"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by grandpavic on 2015-08-24
I have installed Windows 10 (formerly running dual boot Win 7). Now when I try to boot into ubuntu I get a message saying it can't find the file system. I could provide more detail if required. 

When I last ran Win 7 and ubuntu both booted as they should.

---

### Post by Petro Dawg on 2015-08-24
That is precisely why I didn't upgrade to Win10 from Win7 yet.  I suspect windows installed over something.   My first step in trouble shooting this would be to boot into a live session of Ubuntu (by usb or cd) and use GParted to check and make sure all the partitions are still there.  If they are, then install and run [boot-repair]("http://help.ubuntu.com/community/Boot-Repair") from the live session.  If that doesn't fix it, then we might have to take a closer look.  

You might also check [this]("http://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help") out if the above doesn't work.

---

### Post by yancek on 2015-08-24
Windows will always overwrite boot files and there are a number of posts here at the forums of users who had exactly this situation when installing windows 10 or upgrading to it.  Run the boot repair and Select the option to Create BootInfo Summary rather than trying the repair.   There are a number of members here who have expertise on the problem and should be able to help you.

---

### Post by grandpavic on 2015-08-25
Here is the output from BootInfo Summary:

[http://paste.ubuntu.com/12194293/](http://paste.ubuntu.com/12194293/)

It looks to me who knows nothing that all of the partitions are still in place. So I guess I need help with grub.

---

### Post by bford162 on 2015-08-25
> **grandpavic said:**
> I have installed Windows 10 (formerly running dual boot Win 7). Now when I try to boot into ubuntu I get a message saying it can't find the file system. I could provide more detail if required. 

When I last ran Win 7 and ubuntu both booted as they should.

Before you try anything else, boot into Windows and turn off Fast Start (See: [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html))

Then shut down your computer, turn it back on, and see if you can boot into Ubuntu.  If you can, then problem solved.  If not, you may have to repair GRUB2.  I created a Boot-repair live USB to do this, but there are other methods.  (See: [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System))

Good luck.

---

### Post by yancek on 2015-08-25
I don't see anything obvious.  You have Grub in the MBR pointing to the correct partition, the grub.cfg menu is correct with the correct partition and UUID and you are not using EFI so that can't be it.  Which drive do you have set to first boot priority?  It should be the 320GB drive.  Don't see any other possible problems.

---

### Post by grandpavic on 2015-08-26
> **bford162 said:**
> Before you try anything else, boot into Windows and turn off Fast Start (See: [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html))

Then shut down your computer, turn it back on, and see if you can boot into Ubuntu.  If you can, then problem solved.  I

Good luck.

Thank you. This worked for me.  

I still have some issues with the way grub starts, but at least I can access both operating systems.

---

### Post by bford162 on 2015-08-26
> **grandpavic said:**
> Thank you. This worked for me.  

I still have some issues with the way grub starts, but at least I can access both operating systems.ou 

You may be able to resolve the GRUB issues with boot-repair.  This utility may not be installed; see documentation at the following URL.  (See:[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))

---

