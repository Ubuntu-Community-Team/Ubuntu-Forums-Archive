---
title: "Two NTFS questions"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by groston on 2005-09-14
Q1: I have added the following line to /etc/fstab:
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
This works as expected, however, there is an icon (looks like a HD, has the word windows under it, double clicking opens a file browser) on the desktop. How can I make the icon go away?

Q2: Are there plans for Ubuntu to support ntfs rw?

Thank you

---

### Post by mlomker on 2005-09-14
[QUOTE=groston]
Q2: Are there plans for Ubuntu to support ntfs rw?
[/QUOTE]

Have you tried deleting the icon?  I don't run gnome, but in KDE you can delete the icon.

Probably not because the code is still considered experimental/unstable.  If you know how to compile kernels then you could turn the feature on.

---

### Post by groston on 2005-09-14
mlomker,

Thanks for the speedy reply!
If I select the icon and hit the delete key, I get a warnign message that says: 

You cannot move the volume "windows" to the trash.
If you want to unmount the volume, please use "Unmount Volume" in the popup menu of the volume.

Clearly, this is not the desired goal - I only want to get rid of the silly icon, not dismount the drive.

Sorry to ask a question that verges on religion, but can you point me to some resources that discuss the benefits of KDE vs gnome.

---

### Post by cbudden on 2005-09-15
[QUOTE=groston]mlomker,

Thanks for the speedy reply!
If I select the icon and hit the delete key, I get a warnign message that says: 

You cannot move the volume "windows" to the trash.
If you want to unmount the volume, please use "Unmount Volume" in the popup menu of the volume.

Clearly, this is not the desired goal - I only want to get rid of the silly icon, not dismount the drive.

Sorry to ask a question that verges on religion, but can you point me to some resources that discuss the benefits of KDE vs gnome.[/QUOTE]
 In your fstab file, is the drive listed as /dev/sda1 or dev/sda1 ?

---

### Post by mlomker on 2005-09-15
> Sorry to ask a question that verges on religion, but can you point me to some resources that discuss the benefits of KDE vs gnome.

Most of the 'reviews' that I've seen are more like a Coke vs Pepsi thing.  The most useful thing would probably be to just look at [some screenshots](http://www.kde.org/screenshots/kde340shots.php) and see what you think of the look.

If you have broadband and some disk space then you could just download it.  In GDM or KDM you can select which one you want with each login.  Download **kubuntu-desktop** in Synaptic for everything or **kde-core** for just the desktop (none of the extra applications).

---

### Post by prelude on 2005-09-16
edit: my bad, deleted.

so there are no way of removing the mounted drive icons from the desktop?

as I have five mounted ntfs disks the drive icons clutters up my otherwise nice and clean desktop  :-|

---

### Post by groston on 2005-09-16
[QUOTE=cbudden]In your fstab file, is the drive listed as /dev/sda1 or dev/sda1 ?[/QUOTE]
 Sorry about the delay in replying.
In /etc/fstab, the drive is listed as /dev/sda1

---

### Post by mlomker on 2005-09-17
> 
so there are no way of removing the mounted drive icons from the desktop?


Have you looked through the control panels?  I might have to <cringe> install gnome so that I can answer some of these questions.   :-P 

In KDE it is in the Control Center under Desktop, Behavior, and then Device Icons.

---

### Post by taxus on 2005-09-17
When I first installed and configured Ubuntu, I had no volume icons on my desktop for my 2 FAT32 partitions. But then I booted to Windows XP and NAMED my D and E volumes. On the next Linux boot, volume icons appeared on my desktop with the names I'd given in the "Volume Properties". The only way I could get rid of them was to configure Nautilus not to show *any* volume on the desktop.

It's in the GNOME configuration editor GConf, Applications/System Tools menu. The path to the option is: /app/nautilus/desktop, uncheck "volumes_visible".

Problem is that mounted CDs, DVDs and memory cards don't show on the desktop either when mounted. So I rechecked the option, but then on next Linux boot the FAT32 volumes' icons disappeared. I can't explain it.

But my guess is that if you delete the volume name in Windows (in the volume properties) it's won't show on the desktop. Can't hurt to try.

---

### Post by prelude on 2005-09-17
that did the trick, the drives are gone from my desktop. :)

I dont think removing the names from the drives in windows is going to have any effect with me atleast, as two of my five mounted ntfs drives doesnt have any name in windows at all, yet they showed up on the desktop after I mounted them in fstab,

---

