---
title: "USB Boot: Cannot use /dev/sda"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by Darkchef on 2011-09-06
Hello,

I've been trying to install Ubuntu onto my Acer Aspire One netbook using a usb boot. I have tried to use both unetbootin and the universal usb installer with no luck. 

unetbootin just makes the screen hang at the syslinux boot screen.

the universal usb installer gets me to the ubuntu purple loading screen but then gives me the error thay it cannot use '/dev/sda' so I have been unable to install ubuntu on the system. 

I have tried to use gparted live cd to wipe the hard drive clean but i then encounter then same system hanging at the syslinux boot screen.

Are there any other bootloaders that I can try to resolve the issue?

---

### Post by nothingspecial on 2011-09-06
Have you tried unetbootin

I can't get usb-creator-gtk to work at the moment but unetbootin will for me.

---

### Post by Darkchef on 2011-09-06
> **nothingspecial said:**
> Have you tried unetbootin

I can't get usb-creator-gtk to work at the moment but unetbootin will for me.

Yeah i've been trying that with no luck. It just seems to hang at the syslinux screen and it stops reading from the usb.

I guess it could just be my pen drive but im not really sure...

---

### Post by nothingspecial on 2011-09-06
I'd try completely reformatting it and trying again.

---

### Post by Darkchef on 2011-09-06
> **nothingspecial said:**
> I'd try completely reformatting it and trying again.

Well i've reformatted the usb drive a few times and I have no idea how to format the hard drive. There is a broken install of Ubuntu on the hard drive where the boot-arg is broken.

---

### Post by ajgreeny on 2011-09-06
Is the ubuntu .iso file you are using definitely a good one?  It may be that you are trying to use a corrupt .iso install medium, so check the md5sum and if it doesn't match, download again with a torrent client, preferably.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by Darkchef on 2011-09-06
> **ajgreeny said:**
> Is the ubuntu .iso file you are using definitely a good one?  It may be that you are trying to use a corrupt .iso install medium, so check the md5sum and if it doesn't match, download again with a torrent client, preferably.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

Its possible, i did download both the 11.04 and 10.04.3 LTS ISOs and its made little difference.

---

