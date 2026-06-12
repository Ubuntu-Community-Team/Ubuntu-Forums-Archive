---
title: "error: no such partition. grub rescue. error need help"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by GameDog(A) on 2013-01-02
I went to reinstall Ubuntu 12.1 so I erased the very small partitioned portion of my hdd that was allocated to my Ubuntu OS. When I restarted my computer I got the dreaded error: no such partition. grub rescue>. I have no access to my bootloader or my USB driver where I have Ubuntu. I  don't have access to a Win7 disc. Any help would be appreciated

---

### Post by darkod on 2013-01-02
If you did reinstall 12.10 it should have installed the grub2 bootloader too. Do you have more than one disk? Maybe you are booting from the wrong one, where the old grub2 is.

You can try booting from the rescue prompt, but you need to know which one is your root partition. In a single disk dual boot, it would usually be /dev/sda5 unless you manually installed on another partition. But in that case you would know which one.

Under the above assumption, you can try booting from the rescue prompt with:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos5)
linux /vmlinuz root=/dev/sda5
initrd /initrd.img
boot
```

See if that helped. If you do manage to boot, you can reinstall grub2 to the MBR with:
```
sudo grub-install /dev/sda
```

---

### Post by ajgreeny on 2013-01-02
> **GameDog(A) said:**
> I went to reinstall Ubuntu 12.1 so I erased the very small partitioned portion of my hdd that was allocated to my Ubuntu OS. When I restarted my computer I got the dreaded error: no such partition. grub rescue>. [COLOR=Red]I have no access to my bootloader or my USB driver where I have Ubuntu.[/COLOR] I  don't have access to a Win7 disc. Any help would be appreciated
It sounds as if you have grub on the wrong disk, or perhaps on a partition instead of the MBR of the disk.

Is Ubuntu on a USB disk, which is how I read your situation?  Try setting the USB drive as first boot device to see if you can now see the grub menu, and if not showing still after that try [boot-repair]("https://help.ubuntu.com/community/Boot-Repair")

---

