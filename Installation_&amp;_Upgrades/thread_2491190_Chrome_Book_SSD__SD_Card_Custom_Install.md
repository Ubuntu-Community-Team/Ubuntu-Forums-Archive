---
title: "Chrome Book SSD / SD Card Custom Install"
date: 2023-09-28
forum: Installation &amp; Upgrades
---

### Post by el_bizarro on 2023-09-28
Hi..

My Chromebook has a 16gb SSD but it accepted Lubuntu with No Issues but left only a few GB left..

Is there a way I can Migrate some of the System files and Folders over to the SD Card and use just the SDD for the Base System.

Then I can use the SD Card for Downloading any Files or Updates ?..

The SDD obviously Boots much faster than the SD Card

In the Event that it's impracticable or impossible can someone tell me where I can configure the Default Folder for the Downloads and if a possibility exists to use a SD Card for any future installs once the System is Installed.

Im hoping that it's do-able..

Thanks

Rob..

---

### Post by guiverc on 2023-09-28
You didn't provide release details which are, at least to me, a starting point.

Ubuntu systems (*I think of Lubuntu as a Ubuntu system, so your Lubuntu is included here*) allow you to control where directories are stored (*the same drive, different drives, even on network devices*), so you can boot *live* media & make whatever changes you wish, then reflect those changes in the system's file-system table (`/etc/fstab`). 

Where packages install to (*including updates*), is controlled by the type of package (*deb, snap, appimage, flatpak etc*) and packager too; so your real control is via directories covered in the prior paragraph. You need to consider this in deciding how you layout your system, the easiest and default for a `calamares` install (Lubuntu has used the `calamares` installer since Lubuntu 18.10) is putting it on a single partition; ie. all space for `/` with the ESP created only if hardware is detected as needing it (ie. ESP being `/boot/efi` so boot is still on / and only ESP portion is separate).

---

### Post by el_bizarro on 2023-09-28
Sorry It's Lubuntu 22.04

---

