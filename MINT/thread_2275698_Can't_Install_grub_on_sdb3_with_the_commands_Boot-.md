---
title: "Can't Install grub on sdb3 with the commands Boot-Repair gave me"
date: 2015-04-27
forum: MINT
---

### Post by Lucas_Germano on 2015-04-27
This is the link that boot-repair gave me:

[http://paste.ubuntu.com/10918763/](http://paste.ubuntu.com/10918763/)

When i run when the boot-repair program asks me to
```

sudo chroot "/mnt/boot-sav/sdb3" apt-get install -fy
```

```
i get 0 upgraded, 0 newly installed, 0 to remove and 422 not upgraded.
```


and when i run 

```
sudo chroot "/mnt/boot-sav/sdb3" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

```
i get 
The following packages have unmet dependencies:

```
 linux-signed-generic : Depends: linux-headers-generic (= 3.13.0.49.56) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

don't know what to do, tried to find and install this package manually but it still gives me this error,

Would appreciate some help.

Thanks

---

### Post by oldfred on 2015-04-27
Moved since Mint.

Not sure of versions of Mint.

But you have mixed UEFI & BIOS boot. Windows boots in UEFI mode from sda, but you installed Mint in BIOS boot mode in sdb, but attempted to put grub in the partition boot sector of sdb5. In BIOS mode system must boot from MBR of a drive or sdb not sdb5 a partition.

But with mixed boot modes, you have to go into UEFI and turn on UEFI to boot Windows and turn off UEFI or turn on CSM/BIOS/Legacy to boot Ubuntu. Not the easiest way to boot. Better to install Linux in UEFI boot mode. How it installs is how you boot installer.

Boot-Repair seemed to be booted in UEFI mode, and can convert a BIOS install to UEFI boot mode. It will install a new folder in the ESP/efi partition on sda.

Better to have secure boot off, then you do not need signed versions.

And if an Acer you have to specifically authorize another system booting. You have to create an UEFI password (never ever lose that) to enable that.

Please review several of the first links in my signature.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by Lucas_Germano on 2015-04-28
Thanks, i reinstalled following the guide and it worked perfectly. Now i need to figure out how to make my touchpad work. It didn't work in boot-repair bootable ubunt netiher is working with mint. Any ideias?


```

germano@germano-Aspire-VN7-591G ~ $ xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SteelSeries Sensei Raw Gaming Mouse         id=11    [slave  pointer  (2)]
&#9116;   &#8627; SteelSeries Sensei Raw Gaming Mouse         id=13    [slave  pointer  (2)]
&#9116;   &#8627;                                             id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; SteelSeries Sensei Raw Gaming Mouse         id=12    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=16    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=17    [slave  keyboard (3)]


```

---

### Post by oldfred on 2015-04-28
If not of the other links posted above then mention also mention touchpad issue, best to start a new thread with both model & touchpad in title,

---

