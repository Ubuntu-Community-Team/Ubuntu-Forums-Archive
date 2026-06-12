---
title: "Upgrading a live LUbuntu USB Drive with persistent storage"
date: 2018-04-14
forum: Installation &amp; Upgrades
---

### Post by bertar on 2018-04-14
I created a live USB stick with persistent storage with [mkusb]("https://help.ubuntu.com/community/mkusb") (Lubuntu 17.10).
Now I would like to install updates for the release.
I read that you first have to 'mark' your current kernel to prevent kernel updates, in order to keep everything working.
Is this sufficient?
```

lubuntu@lubuntu:~$ uname -r
4.13.0-21-generic
lubuntu@lubuntu:~$ sudo apt-mark hold 4.13.0-21-generic
lubuntu@lubuntu:~$ sudo apt-get upgrade && sudo apt-get -y dist-upgrade

```

---

### Post by sudodus on 2018-04-14
I would recommend that you avoid a full update & upgrade in a persistent live drive. It is likely to fail, at least if many program packages are upgraded. This is not only affecting kernel packages, but also other program packages.

Instead you can keep your **/home** directory (backed up in some other drive), and make a fresh installation of a daily iso file of either 16.04 LTS (if you want to play safe, or Bionic (to be released during this month as 18.04 LTS). See this link,

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

Then you can either copy 'your old home' into the new persistent live drive's /home (located at the casper-rw partition's /mount-point/upper/home).

Maybe even better, 'kidnap' the usb-data partition and convert it to an ext4 partition with the label **home-rw** or shrink the casper-rw partition and create space for an ext4 partition with the label **home-rw**. And copy 'your old home' directly into this 'new home'.

The following link might help,

[Similar to this link, but in your case probably all partitions in the same drive](https://askubuntu.com/questions/1024094/lubuntu-live-program-files/1024271#1024271)

If you want a stable system, that is up to date, it is a good idea with an** installed system (in USB)**, as in the following link and links from it,

[Install Xubuntu (or Lubuntu) like into an internal drive, but into a USB drive](https://ubuntuforums.org/showthread.php?t=2388746&p=13754656#post13754656)

---

### Post by C.S.Cameron on 2018-04-15
Sudodus:

I have found that trying to copy home to the casper-rw partition's /mount-point/upper/home always fails for me, often asking for a password when none is available. Please let me know if you have gotten this to work.
The only way I have been able to reuse home from install to install is as a home-rw file or partition.
It is however possible to extract a casper-rw file or partition to produce a home-rw file or partition.
I am still trying to get this to work consistently, Permissions can be a challenge.

Bertar:

If you use mkusb to create your boot disk you can shrink the casper-rw partition or usbdata partition and create an ext4 partition labeled home-rw that will contain all your home stuff, bookmarks, documents etc.

The home-rw partition can be copied and reused from release to release but it helps to have two USB drives.

Programs need to be reinstalled from release to release.

This also works with casper-rw and home-rw files with UNetbootin.

---

### Post by sudodus on 2018-04-15
@C.S.Cameron,

Yes, once I had a problem, that the system asked for a password. If I remember correctly, it worked better when I did the copying without persistence: I selected 'Try Ubuntu' at the grub menu instead of the alternatives with persistence. But I can try again and tell you the result.

@everybody,

Gradually I am getting more 'fond of' installed systems in USB, if you intend to use the system a lot and for a long time. There are some modifications, that you should consider in order to reduce wear, if you use a pendrive. See this link,

[Final system tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

If you can get an installed system in a USB drive portable enough (to work in the computer(s), where you need it), it is more stable, and it can be kept up to date just like any installed system.

---

### Post by sudodus on 2018-04-16
It works for me according to this link: 

[How to keep /home from an old persistent live drive when creating a new one](https://ubuntuforums.org/showthread.php?t=1958073&page=38&p=13757039#post13757039)

---

