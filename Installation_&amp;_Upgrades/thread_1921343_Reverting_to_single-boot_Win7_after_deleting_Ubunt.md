---
title: "Reverting to single-boot Win7 after deleting Ubuntu Partition"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by unckybob on 2012-02-06
I have a ThinkPad Edge E420 which came with Win7 installed. I installed Ubuntu to it as a dual-boot system. It has a Lenovo recovery partition which I didn't do anything to. I don't have any Win7 installation discs.

I wanted to uninstall Ubuntu and just have a Win7 machine again. 

I booted from a live installation flash drive that I created with usb-creator-gtk. Then I deleted the Ubuntu partition and enlarged the Win7 partition using the space created by deleting the Ubuntu partition. 

Now when I start up I get the following message:

error: no such partition
grub rescue>

"grup rescue>" is actually a prompt I get from "grub".

I read here:

[http://forums.lenovo.com/t5/ThinkPad-Edge/Thinkpad-E420-Restore-with-partitions-changed/td-p/604231](http://forums.lenovo.com/t5/ThinkPad-Edge/Thinkpad-E420-Restore-with-partitions-changed/td-p/604231)

that you can't use the Lenovo recovery partition to restore the partition, if you have changed the partition.

Can someone please tell me how to get this machine to be a Win7 machine again?

---

### Post by drs305 on 2012-02-06
If you are booting from an Ubuntu LiveCD, try this to restore the Windows bootloader without having to use a Windows repair CD. The command assumes Windows is on the first drive (sda) and the boot flag is set to the Windows partition. If you don't know, just try it. Don't pay attention to the output saying lilo isn't fully configured.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot and hopefully you will see your Windows bootloader.

---

### Post by darkod on 2012-02-06
As a quick fix, you can install generic mbr with linux tools. But you shouldn't have touched the win7 partition with Gparted. If possible, always resize win7 partition with windows Disk Management.

Anyway, to install generic mbr boot with the ubuntu cd in live mode and execute in terminal:

sudo apt-get install lilo (you need to have internet connected)
sudo lilo -M /dev/sda mbr

There will be a warning about bootloader config files, just continue. It's normal.

That should make win7 boot provided the resize with Gparted didn't mess something up.

---

### Post by unckybob on 2012-02-06
Hurrah!

Thanks, you guys, that took care of it.

---

### Post by drs305 on 2012-02-06
Glad it worked but sorry you are leaving Ubuntu. Perhaps you will try it again in the future.

Marking the thread 'SOLVED' via the Thread Tools link at the top right of the first post might identify this solution to someone else in your situation.

Happy computing.

---

