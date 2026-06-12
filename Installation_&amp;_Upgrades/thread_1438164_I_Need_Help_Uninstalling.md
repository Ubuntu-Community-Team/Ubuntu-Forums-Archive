---
title: "I Need Help Uninstalling"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Garetty on 2010-03-24
I am in the process of uninstalling Ubuntu because I've had some problems with it. (Planning on Reinstalling later) I have done the part where I have to boot to Windows XP and do the fixboot and fixmbr stuff. Now I have opened Disk Management. I don't know what to do here... Could someone give me a detailed tutorial on how to do this?

Here is a picture: (That is a Windows 7 theme for Windows XP)

---

### Post by cogier on 2010-03-24
There is a great deal on this subject here [https://lists.ubuntu.com/archives/ubuntu-users/2006-December/102255.html]("https://lists.ubuntu.com/archives/ubuntu-users/2006-December/102255.html")

---

### Post by coffeecat on 2010-03-24
I should imagine you simply need to remove the "unknown" (unknown to Windows, that is) partitions and reuse the space. But why are there four?

Better, though, would be to use Ubuntu one last time for this. Boot up with the live CD and go to System > Administration > Gparted. This will identify the Linux partitions properly and allow you to delete them and create a NTFS partition in their place. Or, once you've removed the Linux partitions, you can use Gparted to enlarge the Windows C:\ partition to use the liberated space.

---

