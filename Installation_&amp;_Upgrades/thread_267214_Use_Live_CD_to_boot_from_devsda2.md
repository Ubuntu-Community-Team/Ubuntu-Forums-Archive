---
title: "Use Live CD to boot from /dev/sda2"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by elo on 2006-09-28
Hi experts,

I have installed Windows Vista on /dev/sda1 and Ubuntu 6.06 on /dev/sda2. Multiboot with Grub worked fine until I updated Vista to the newest RC and of course it overwrote the MBR. Now Grub is gone.

Now I want to use the Ubuntu CD to make it boot from /dev/sda2 and run grub-install.

How do I do this? The CD's boot menu has an option "Boot from first hard disk" but there is Vista.

Thanks for your help.

---

### Post by pay on 2006-09-28
This might help you to reinstall grub [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Fatjoint on 2006-09-28
> **elo said:**
> Hi experts,

I have installed Windows Vista on /dev/sda1 and Ubuntu 6.06 on /dev/sda2. Multiboot with Grub worked fine until I updated Vista to the newest RC and of course it overwrote the MBR. Now Grub is gone.

Now I want to use the Ubuntu CD to make it boot from /dev/sda2 and run grub-install.

How do I do this? The CD's boot menu has an option "Boot from first hard disk" but there is Vista.

Thanks for your help.

Argh...

In Windows XP (I realize your saying VISTA, but I haven't had my hands on it yet) the c:\boot.ini file is the menu list for windows mbr manager.  This will tell you what partition Windows exists on in case the GRUB installation fails to properly recall it.

After installing GRUB, if you have problems booting windows, you'll want to examine /boot/grub/menu.lst and look to see if the partition information for windows matches the information within your boot.ini.  If it doesn't - correct the partition information within menu.lst to resolve the issue.

---

### Post by elo on 2006-09-28
Thank you both for your suggestions. The Super Grub CD would have helped, but my Windows was not configured to burn ISO images to CD and booting from the Ubuntu Live CD, burning another CD is not so easy unless you have a second drive, right?

So I'm glad I found a quicker solution without having to create a rescue CD. If you speak German, it's here: [URL="http://wiki.ubuntuusers.de/GRUB#head-29d01f188b13a```

```c65d9825f7a0c001c9ebd2befac"]http://wiki.ubuntuusers.de/GRUB#head-29d01f188b13ac65d9825f7a0c001c9ebd2befac[/URL]

Here's a short translation. Use this if your GRUB config was working fine but GRUB was overwritten by another OS (i.e. you have your menu.lst and you just want to reinstall GRUB in the MBR):

1. Boot from some Live CD (can be the Ubuntu CD, Knoppix etc.)
2. Mount your Ubuntu partition (assuming it's on hda2):

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/hda2 /mnt/ubuntu
```

3. Make the /dev tree visible under the mount directory:

```
sudo mount -o bind /dev /mnt/ubuntu/dev
```

4. Create a root shell in the mounted filesystem:

```
sudo chroot /mnt/ubuntu
```

5. Reinstall GRUB in the MBR

```
grub-install /dev/hda
```

6. Exit the chroot-Environment:

```
exit
```

Reboot, and GRUB should be back. Worked like a charm for me.

---

