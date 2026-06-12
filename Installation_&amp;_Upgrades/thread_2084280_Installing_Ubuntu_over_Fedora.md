---
title: "Installing Ubuntu over Fedora"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by ojhaarjun on 2012-11-14
Hello all,
I want to install Ubuntu on the same disk on which I have currently installed Fedora 17. I am on dual boot with Windows 7. I want to know that if I write Ubuntu on Fedora then will it crash my GRUB?

Please Help
Thanks in advance.

---

### Post by carl4926 on 2012-11-15
It should be fine
You might want to check the volume labels - because fedora adds one
Use gparted in the live session (before running the installer) to remove it

---

### Post by ojhaarjun on 2012-11-15
Where can I find the volume label?

---

### Post by carl4926 on 2012-11-15
Using gparted
Right click the fedora partition and the context menu should offer a list that includes: label
click it and see

---

### Post by ojhaarjun on 2012-11-15
Okay I am right now install gparted on Fedora after that I'll run the installer.
I have to delete the Fedora partition using gparted in Ubuntu Live Session right?
Thanks

---

### Post by carl4926 on 2012-11-15
> **ojhaarjun said:**
> Okay I am right now install gparted on Fedora after that I'll run the installer.
I have to delete the Fedora partition using gparted in Ubuntu Live Session right?
Thanks
No, you don't necessarily need to delete it

I  was just informing you of fedora's habit of adding a label to the install partition, and how to remove it
Gparted is just a partitioning tool. It's a bit easier than using the advanced tool in the installer.
Once you remove the label. Close Gparted and run the Ubuntu installer and proceed this way:
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)
Then simply point the installer to the partition/s you want to use
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by ojhaarjun on 2012-11-15
See the screen shot. Look there's no label.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227199&stc=1&d=1352958888[/IMG]

---

### Post by carl4926 on 2012-11-15
So win7 is sda2?
What is in sda5? Could we delete it?
Because is's all a right mess

**Do you know if you have UEFI BIOS???**Answer this before doing any more. Fedora manages well with UEFI.

I'd like to see everything deleted back to sda3, so we can re-create everything.
sda3 is extended space, so you basically create logical partitions inside it.

If you need to leave sda5 in place, fine, just delete sda6 and 7

You seem to have little room left in sda2 (win7) and a massive additional NTFS partition.... is this what you want?

---

### Post by ojhaarjun on 2012-11-15
So I just have to delete sda6 and sda7 and the just open installer and install Ubuntu along side to Windows 7?

---

### Post by carl4926 on 2012-11-15
> **ojhaarjun said:**
> So I just have to delete sda6 and sda7 and the just open installer and install Ubuntu along side to Windows 7?

Well, no...
I asked for more information/detail. But you didn't supply it.

To be honest, you are rushing this and I'm not convinced you understand exactly what you are doing. And the potential risks.

But if you are keeping sda5
You could delete sda6 and 7
Then with the unallocated space create a partition 
swap = to 2x your RAM
and all that remains to ext4, which will be set as / in the advanced installer

But you ought to answer my earlier questions first

---

### Post by ojhaarjun on 2012-11-15
Yes, sad2 is Windows 7.
I store my rest of the files in sda5 so we cannot delete it.
I don't know if I have UEFI BIOS or not.

---

### Post by carl4926 on 2012-11-15
> **ojhaarjun said:**
> Yes, sad2 is Windows 7.
I store my rest of the files in sda5 so we cannot delete it.
I don't know if I have UEFI BIOS or not.

Then follow my earlier comment

[I]But if you are keeping sda5
You could delete sda6 and 7
Then with the unallocated space create a partition 
swap = to 2x your RAM
and all that remains to ext4, which will be set as / in the advanced installer[/I]

---

### Post by oldfred on 2012-11-16
You do not have UEFI.

With UEFI you have gpt partitioning and with gpt partitioning you do not have an extended partition. Also with UEFI the first (sometimes 2nd) partition has to be the efi partition and will be shown as that.

Your first partition is the typical 100MB hidden Windows boot/repair partition.

Fedora's default install uses lvm and a separate /boot partition and in Ubuntu's desktop you need to add the lvm2 drivers to see Fedora. If just erasing Fedora you can delete the Fedora boot partition and the lvm partition.

---

