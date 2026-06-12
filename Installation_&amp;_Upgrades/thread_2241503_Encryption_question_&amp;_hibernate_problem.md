---
title: "Encryption question &amp; hibernate problem"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by witchbutter on 2014-08-26
I bought a haswell XPS 13 and I am using UEFI boot with luks from a fresh install using the whole disk for Ubuntu 14.04.  I am having a rather annoying issue with hibernate which seems to hibernate just fine but say 3 in 4 resumes fail with either the touchpad not responding, failure to completely load unity, or unity is just a frozen screen.  Googling this issue leads to several discussions about encrypted swap but I believe when you use the default install that the encryption is on the physical volume and therefore swap is encrypted because it is a logical volume.  Am I reading/understanding this correctly?

```

root@localhost:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root 		  /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=dcffc316-ad5c-4545-a4d5-f2d438605c53 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=9D0B-BE58  			  /boot/efi       vfat    defaults        0       1
/dev/mapper/ubuntu--vg-swap_1 		  none            swap    sw              0       0
root@localhost:~# cat /etc/crypttab
sda3_crypt UUID=46e324cb-16a9-44d1-8410-ca6ef612f40f none luks,discard
root@localhost:~#
```

If encrypted swap is not my issue, how can I resolve hibernate for XPS 13?  Other users of the XPS 13 don't seem to have any issue that requires modifying settings.

---

### Post by witchbutter on 2014-08-28
I was correct that the encryption is at the physical volume level.  
As it turns out the installer made the swap space too small to handle the hibernate.  After I increased it hibernate now works as intended.

---

### Post by paul_roberts3 on 2014-08-30
I have an issue with hibernate as well, sounds similar to your symptoms.

Having only installed 14.04 yesterday, I'm very green. Running on an iMac 10,1, dual-boot.

When waking from hibernation this morning it didn't wake by my bluetooth mouse/keyboard, only the attached wired keyboard (which is horrible and really only until I get full functionality with Ubuntu). Upon waking I got the login screen, the bluetooth keyboard was found fairly quickly but not the mouse. I logged in but it hung, something failed to load. I only had my desktop wallpaper, nothing else onscreen. Sounds like Unity failing, perhaps? The only solution I could tell (with my CLI basic skills and lack of confidence/experience) was to switch off via the power button. On reboot everything was fine but the mouse was not connected. I had to use Launcher to access Bluetooth settings and manually connect it.

I chose to encrypt at installation stage, but only the Admin user, not my regular user.

If adjusting the size of swap might do it, I'm happy to give it a go. How do I go about it?

Thanks

---

