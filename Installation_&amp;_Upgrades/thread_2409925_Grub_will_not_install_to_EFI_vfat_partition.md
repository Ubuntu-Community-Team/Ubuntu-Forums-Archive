---
title: "Grub will not install to EFI vfat partition"
date: 2019-01-08
forum: Installation &amp; Upgrades
---

### Post by haljeisen on 2019-01-08
I recently purchased a Dell Inspiron 7386 laptop. I ran my Ubuntu install from a USB thumb drive. I didn't need Windows, so I repartitioned the entire internal SSD to be dedicated to Ubuntu. My partition table has 4 partitions:[INDENT][FONT=courier new]
/dev/nvme0n1p1   VFAT    /boot/efi
/dev/nvme0n1p5   ext4    /boot
/dev/nvme0n1p6   ext4    /root
/dev/nvme0n1p7   ext4    /home
[/FONT][/INDENT]

I know the BIOS is trying to do a UEFI boot (not a legacy boot) because I installed [rEFInd]("http://www.rodsbooks.com/refind/") and I can boot into that directly from the SSD. I have turned off SecureBoot in the BIOS. I have converted the internal SSD to GPT.

I've tried running grub-install a few different ways, using variations of this technique:

[FONT=courier new][COLOR=#000000]sudo mkdir /mnt/{boot,root,home}[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]sudo mount /dev/nvme0n1p5 /mnt/boot[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]sudo mount /dev/nvme0n1p6 /mnt/root/[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]sudo mount /dev/nvme0n1p7 /mnt/home/[/COLOR]
[/FONT]
[FONT=courier new][COLOR=#000000]sudo mount /dev/nvme0n1p1 /mnt/boot/efi[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]for i in /dev /dev/pts /proc /sys /run; do sudo mkdir /mnt$i; sudo mount -B $i /mnt$i; done[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]for i in /bin /usr/bin /lib /usr/lib /sbin /usr/sbin /lib64 /usr/share/grub /usr/share/locale; do sudo mkdir -p /mnt$i; sudo mount -B $i /mnt$i; done[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]sudo chroot /mnt[/COLOR][/FONT]

[FONT=courier new][COLOR=#000000]grub-install /dev/nvme0n1
[/COLOR][/FONT]
[COLOR=#000000][FONT=Arial]
I've also tried running [boot-repair]("https://help.ubuntu.com/community/Boot-Repair").
[/FONT][/COLOR]
Regardless of what I do, I cannot boot Ubuntu from the internal SSD. I'm not sure if I need to force grub-install to use the x86_64-efi target, or if the default i386-pc target is acceptable. The /boot/efi/grub directory is always empty, which seems wrong because /boot/efi/EFI/BOOT/ has the rEFInd files in it. [FONT=courier new]modprobe efivars[/FONT] does not seem to do anything when I've booted from the legacy USB thumb drive.


Any help would be much appreciated.

---

### Post by oldfred on 2019-01-08
Have you updated UEFI from Dell and firmware for SSD?
Most Dell systems need that.

Are you able to boot with rEFInd? I have used it as emergency boot when a grub install went awry.

You typically do not need /boot partition with standard desktops, but that does not make any difference.
Please post link to Summary report from Boot-Repair. But it does not fully report on NVMe drives.

       Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some other threads with Dell 7000 series systems. But many issues with Dell are across many models as same UEFI. Bigger difference if AMD or Intel based system.
       
 DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

Newer Dell support firmware updates from Linux.
       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
            UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by haljeisen on 2019-01-08
I was able to solve my problem.

I needed up unmount all of my internal SSD partitions, and then run the Boot Repair utility. Under that condition, Boot Repait prompted me to copy/paste a series of commands which correctly installed Grub on my EPS. The next time I rebooted, the BIOS correctly found EFI to launch Grub which seamlessly transitioned into the kernel and a fully running Ubuntu system.

---

### Post by yetimon_64 on 2019-01-08
> **haljeisen said:**
> I was able to solve my problem...

Could you also mark the thread as [SOLVED] from the the thread tools drop down menu at the top of this thread please?

Doing so makes it easier for both helpers and other forum users doing searches to know at a glance, in the parent forum, when a thread has been solved.

The middle blue link in my sig line has a guide for how to do so, if needed.

Regards, yeti.

---

### Post by Cavsfan on 2019-01-10
FYI: If you ever need to re-install grub in the future, you just need to type this in terminal:
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu
```

Or even if you can boot into rescue mode or TTY1 or whatever and type that, it will work.

(That is where my ESP is, yours probably is too but, you'll need to check.)

---

