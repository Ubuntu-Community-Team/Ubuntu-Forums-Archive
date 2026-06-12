---
title: "Cant see grub menu on bootup"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by subehsharma on 2011-07-24
Hi, i'm new to Linux. I've just installed Ubuntu with windows 7 already installed(Not using wubi) and not when i boot my laptop, I'm not getting any grub screen which asks for selecting the OS to boot. Need some help here!

---

### Post by Quackers on 2011-07-24
In Ubuntu open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run. You should see the Windows Loader appear. If so, reboot and you should get a grub menu to choose what to boot.

---

### Post by subehsharma on 2011-07-24
Its showing some problem:

subehsharm@subsharm:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

Any idea?

---

### Post by Quackers on 2011-07-24
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by subehsharma on 2011-07-24
> **Quackers said:**
> Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


Thanks for the suggestion but i got it resolved from a solution posted on this thread:
[http://ubuntuforums.org/showthread.php?t=1374445](http://ubuntuforums.org/showthread.php?t=1374445)

---

### Post by Quackers on 2011-07-24
So I see :-)
All's well that ends well.

---

