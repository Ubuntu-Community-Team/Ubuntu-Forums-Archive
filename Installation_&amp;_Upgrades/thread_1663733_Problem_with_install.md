---
title: "Problem with install"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by michiganman1993 on 2011-01-10
Hi,
When I try to install Ubuntu 10.10, the installation freezes before the actual install begins on the second page with the options to download updates while installing or not. I have tried with multiple CDs and redownloaded the .iso from the website. Any ways to fix this?
Also, I have successfully installed 10.10 two days ago on this computer and the live CD runs fine without installing.

---

### Post by dino99 on 2011-01-10
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by kansasnoob on 2011-01-10
> **michiganman1993 said:**
> Hi,
When I try to install Ubuntu 10.10, the installation freezes before the actual install begins on the second page with the options to download updates while installing or not. I have tried with multiple CDs and redownloaded the .iso from the website. Any ways to fix this?
Also, I have successfully installed 10.10 two days ago on this computer and the live CD runs fine without installing.

Since installation worked 2 days ago but not now I'm curious as to why you need to reinstall? Maybe knowing that will provide a clue.

Since you can run the Live CD please also post the output from terminal of:

```
sudo parted -l
```

BTW that's a lower case L.

---

### Post by michiganman1993 on 2011-01-10
Here's the pastebin from sudo parted -l: [http://paste.ubuntu.com/552605/](http://paste.ubuntu.com/552605/)
I need to reinstall because for some reason no programs would open so I went for a reboot and it wouldn't start, so I went to GParted and tried to mess around with it and may have messed with the boot files and erased them or something so now I can't boot from the hard drive.

---

