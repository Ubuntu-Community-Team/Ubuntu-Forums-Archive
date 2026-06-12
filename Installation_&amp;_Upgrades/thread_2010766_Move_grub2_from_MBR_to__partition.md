---
title: "Move grub2 from MBR to / partition"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2012-06-26
I would like to move grub2 from the MBR to the / partition.

I am running Hackintosh (OSX installed on a PC) as my primary OS. I have a Ubuntu 12.04 install on my 5th HD. 3 OSX, 1 Win7 and the last Ubuntu.

The OSX bootloader Chimera dos not find OSX when grub2 is installed on the MBR on the 5th disc. Therefore I would like to move it to the / partition where it (for some reason) should be recogniced.

Do I just remove Grub2 and then install again to another partition? I have read the info here [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) but I am not sure how to do it.

Can anybody supply a step by step? 

Thank you!

---

### Post by darkod on 2012-06-26
Boot your ubuntu, double check which partition is the root with:
df -h

That will display the mounts and you can see which partition is mounted as /.

Lets say it will be /dev/sde1.

To install grub2 on a partition you have to force it with the -f option.

sudo grub-install -f /dev/sde1

Don't forget, instead of sde1 it should be your correct root partition where you want to install.

After that it's also better to reconfigure the devices connected to grub2 and leave just that partition. You do that with:
sudo dpkg-reconfigure grub-pc

You select/deselect devices with Space. This is done so in the future when there are grub2 updates it knows where to update.

---

### Post by coffeecat on 2012-06-26
> **JohnFante said:**
> I am running Hackintosh (OSX installed on a PC) as my primary OS.

From the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy):

> We do not support circumventing TOS, EULA, etc here. 

Thread closed.

---

