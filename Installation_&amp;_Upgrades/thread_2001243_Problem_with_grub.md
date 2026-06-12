---
title: "Problem with grub"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by mcdlima on 2012-06-10
Hi,

I had a notebook with windows seven and ubuntu 12.04 recently installed. Then I tried to install lubuntu 12.04 over the ubuntu already installed (as the installer suggested).. the installation was ok but when I rebooted the system, the grub list was the same, with ubuntu and seven only. 

I tried Boot-Repair but it didnt solve my problem.
log generated:

[http://paste.ubuntu.com/1033071/](http://paste.ubuntu.com/1033071/)

Thanks,

---

### Post by drs305 on 2012-06-10
Is it booting correctly to Lubuntu?  My VM of Lubuntu is broken at the moment and I don't recall if Lubuntu is identified as "Ubuntu" in the Grub menu or not. Many of the Ubuntu family of releases are simply identified as "Ubuntu" by Grub.

If in fact you did install Lubuntu and it's just the name that is bugging you, an app called Grub Customizer will let you name the menuentries anything you wish.

See the link in my signature line for Grub Customizer.

---

### Post by Enigmapond on 2012-06-10
You need to just update grub. Log on and in the terminal run:
```
update-grub
```

---

### Post by mcdlima on 2012-06-10
No, I tried the ubuntu option in the grub list but it gives me an error like "no such file"... 

Windows still working fine.

---

### Post by drs305 on 2012-06-10
> **mcdlima said:**
> No, I tried the ubuntu option in the grub list but it gives me an error like "no such file"... 

Windows still working fine.

Ok. If you have no working Ubuntu/Lubuntu, boot a LiveCD, install Boot Repair, and let it attempt to fix things. 

Edit: Looking at the file.

Was your original Ubuntu installation on the same partition, and in the same part of your drive? Your Ubuntu partition is deep into the hard drive. It's possible the BIOS and Grub can't see that deep into the drive but if the new installation is in the same place as the old one this normally isn't an issue. However, where the files ended up within the partition can make a difference in some cases.

Try these commands to learn if Grub can see your boot files:

At the Grub prompt (if you see the Grub menu, press c ):
```

ls  # You should see (hd0), (hd0,1), (hd0,2), (hd0,5), (hd0,6)
ls (hd0,6)/ # You should see *vmlinuz* and *initrd.img*
ls (hd0,6)/boot # You should see *vmlinuz-3.2.0-23-generic* and *initrd.img-3.2.0-23-generic*
ls (hd0,6)/boot/grub  # You should see a bunch of *.mod files

```

If Grub sees all those things, try running these commands to boot. If the boot fails, tell us what happens.
```

set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro
initrd /initrd.img
boot
```

If Grub can't see these files, it probably means that your BIOS can't see past 137GB. You will need to either enable large drives or the LBA option in BIOS, update the BIOS, or create a /boot partition within the first 135GB or so of the drive.

---

### Post by YannBuntu on 2012-06-11
Hello

> **mcdlima said:**
> log generated:

[http://paste.ubuntu.com/1033071/](http://paste.ubuntu.com/1033071/)

Thanks,

- Boot-Repair could not pre-download the packages, so it canceled the purge (that's a security for not purging without being able to reinstall). Do you use Wifi?
- your Ubuntu partition is very far (489GB) from the start of the disk, so as suggested by Oldfred above, you may [need to create a separate /boot close from the start of your disk]("http://ubuntuforums.org/showthread.php?t=1998257"). This is coherent with the grubenv error we see in the log.

---

