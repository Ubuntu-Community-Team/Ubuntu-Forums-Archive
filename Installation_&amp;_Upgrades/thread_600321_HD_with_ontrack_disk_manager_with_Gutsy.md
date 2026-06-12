---
title: "HD with ontrack disk manager with Gutsy"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by Olaf Scheel on 2007-11-02
Hi,
I have a problem installing Kubuntu 7.10. : My Pc has two HDs for a dual boot with Windows 2000 (hda 80 GB, 10 GB NTFS, 70 GF FAT and hdb 160 GB for Kubuntu)
My old Bios does not support large Hds, so I use Ontrack disk manager (dynamic disc overlay) on hda to avoid the bios limitation.

Up to Kubuntu 7.04, I could acces hda with the boot parameter hda=remap63.

Now I try to install Gutsy from the alternate CD. Hda is shown as free space. Setting up a dual boot with GRUB and accessing the shared FAT partition is not possible.

Is there no support for Ontrack in the new kernel? Is this a Kubuntu-specific problem?

Thanks for your ideas
Olaf

---

### Post by sedbergman on 2007-11-04
Hi Olaf,

Sorry, i haven't got a solution for you but just to let you know i have exactly the same problem  (not a kubuntu specific problem as i'm using Ubuntu). I can't believe they would remove the hda=remap boot option. The only way i can get it to boot is to alter grub to choose the older kernel used by Feisty.Hope you can at least do this.

Thanks,
Sedbergman.

---

### Post by Olaf Scheel on 2007-12-06
No ideas?

---

### Post by SoUS on 2008-04-27
Looks like I'm in the same boat. Trying to recover my Win2000 system after installing 8.40 ubuntu.  Looks like the ubuntu install wiped out the OnTrack DDO and left my 200gb of life up the creek with out a paddle.

Very disappointed,
SoUS

---

