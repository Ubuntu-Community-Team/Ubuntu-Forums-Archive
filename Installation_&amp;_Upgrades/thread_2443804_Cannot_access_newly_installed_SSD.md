---
title: "Cannot access newly installed SSD"
date: 2020-05-20
forum: Installation &amp; Upgrades
---

### Post by johnburrell on 2020-05-20
Hi

I've upgraded an internal SSD (nvme) and installed Arch Linux on it on the first three partitions.
I use ubuntu to control access to the OS's on the disks, so after Arch installation I ran update-grub on Ubuntu.

Arch shows up in the OS list at boot time, with the correct location, but when I click Arch it says that the device (UUID number) does not exist.

Windows is also installed on the same disk as Ubuntu and I can access that with no problems.

I can mount the new disk partitions from Ubuntu and the Arch files are present, where they should be.

I don't understand why are can't access them at boot time.

regards

jb.

---

### Post by CelticWarrior on 2020-05-20
Welcome.

It's not unusual to have problems booting Arch or derivatives like Manjaro from Ubuntu's Grub. I really don't know why but I'm sure it has been documented somewhere in Arch's or Manjaro's forums. So, I'm not offering a solution, only a suggestion to investigate it in other online forums.

That said, if you want to boot Arch, knowing that everything was installed in UEFI mode (NVME obliges), you can easily boot it directly from UEFI boot settings and in some computers also from the one-time boot menu. You may use Arch's Grub instead as that one usually boots itself and Ubuntu just fine.

---

