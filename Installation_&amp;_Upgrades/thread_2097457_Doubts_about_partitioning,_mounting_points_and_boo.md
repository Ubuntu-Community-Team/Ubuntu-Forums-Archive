---
title: "Doubts about partitioning, mounting points and bootloader"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by GuilhermeBrant on 2012-12-23
Hi all,

I have already had too much trouble with bootloader while repartitioning my HD, so I decided to ask here first before messing it up again. Here is how my system partitions look today :

[IMG]http://s14.postimage.org/jpya1xjs1/my_partitions.png[/IMG]
Both the partitions runs Ubuntu.

It used to be one extended partition containing both the Ubuntu partitions and a Swap one. Yesterday, I had to reinstall ubuntu on one of them and I don't know why, it created another primary partition to install it, so now I have two primary partitions instead of an extended one containing both. Also, I lost my swap partition.

Questions :
1) Is there any advantage on changing the system's partitions so that both occupy the same extended partition? (such as sharing the same SWAP partition, or will they share it even at distinct primary partitions?)

2) As long as the partition containing GRUB (which I guess is always the one having the flag 'boot'?) mantain its beggining, can I resize the partitions without messing up with bootloader? For example, in the case of the picture, can I shrink 'sda1' and expand 'sda6' using that space, without messing up anything?

3) If I had the first primary partition containing /boot (that is, selecting /boot as the mount point in GParted for that partition), without installing any O.S on it, and the second primary partition being an extended one containning all my linux logical partitions, would I ever have to care about not messing bootloader again, when resizing/deleting/formatting my linux partitions?

Thanks in advance,

Luiz.

---

### Post by darkod on 2012-12-23
The boot flag is used by windows, linux doesn't use it. But some boards can't boot if there is no boot flag on any of the partitions, so it's good to have it. But it remains unused and it doesn't mean that partition is controlling grub.

Right now grub on the MBR would be from the latest install. If that is sda1, then sda1 is controlling grub2.

As for primary vs logical, linux doesn't care about that too. It works perfectly fine from either.

Yes, both installs can share the swap partition because you have only one booted at the same time anyway. But that red mark next to sda5 looks like there is something wrong with your swap partition.

You might need to delete it, create it again as swap area, and then in /etc/fstab on both installations replace the old UUID string with the new one (creating a new partition assigns new UUID to it).
You can check all partitions UUIDs with:
sudo blkid

As for resizing, it's possible but only if really, really need it. There is always risk involved things to go wrong, so you better have a full backup of your data before you start, and be ready if something goes wrong (like having the ubuntu cd of the same version at hand, get info what to do if the system stops booting, etc).

---

### Post by ajgreeny on 2012-12-23
I am a bit confused as you say you now have two primary partitions, which you don't.

sda1 with the boot flag is a primary partition, everything else is in the extended partition sda2, and I assume that sda6 is your old Ubuntu OS and sda1 is the new one.

The main Ubuntu partition that you have must be mounted at / which is root, not /boot and  I recommend that you forget about using a separate /boot partition and mountpoint as it can complicate matters on a normal desktop machine and is only sometimes needed on a server.

I also agree with darkod that if all is working OK at the moment, leave things as they are, though there is going to be quite a lot of wasted space with the two installs on similar sized partitions.  Is there a particular reason why you need the two separate OSs?

As for swap, format sda5 as linux swap using gparted, then edit /etc/fstab in both OSs to give it the new UUID, which as darkod says you can find with ```
sudo blkid -c /dev/null
```

---

### Post by GuilhermeBrant on 2012-12-23
Hi guys, thank you very much for your support.

Yes, everything was working fine here. But I have messed with bootloader so many times before, changing the partitions, that I wanted to know more about what I was doing. I tried reading some tutorials (one the best were this one : [https://wiki.archlinux.org/index.php/Partitioning](https://wiki.archlinux.org/index.php/Partitioning) ) but I'm still not confident about the right procedures for reducing the risk at partitioning. From what I have been able to understand, as long as I don't move the beggining of the partition hosting GRUB, the chances of messing with it are minimal, right? 

I took the chance and tried to resize the partitions, and gracefully it turned out fine.

Thank you for clarifying about the swap partition too, I formatted it as linuxswap and added its UUID to the O.S's fstab.

If you have any other, more complete, guide about partitioning and booting targeted at linux that you could reference, I would really appreciate it.

Best regards.

---

