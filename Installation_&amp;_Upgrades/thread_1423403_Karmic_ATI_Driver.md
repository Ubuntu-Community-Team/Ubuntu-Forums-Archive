---
title: "Karmic ATI Driver"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Penguin Guy on 2010-03-06
Just upgraded to Karmic, after the upgrade has finished it tells me that the driver doesn't work. It won't let me run Compiz or anything graphics-intensive like that.

Two questions:
[LIST=1]
[*]How do I fix it?
[*]Why did it break in the first place?
[/LIST]

Really ****** off with these Linux graphics issues every time I upgrade.
Thanks for the help.

EDIT: Looks like I was running the old kernel.

---

### Post by lidex on 2010-03-06
Not a whole lot to go on there. How about the output of this command:
```
lspci -nn | grep VGA
```

Did you try jockey (hardware drivers) and or try to install proprietary one? What version?

---

### Post by Mark Phelps on 2010-03-06
> **Penguin Guy said:**
> Just upgraded to Karmic, after the upgrade has finished it tells me that the driver doesn't work. It won't let me run Compiz or anything graphics-intensive like that.

Two questions:
[LIST=1]
[*]How do I fix it?
[*]Why did it break in the first place?
[/LIST]

Really ****** off with these Linux graphics issues every time I upgrade.
Thanks for the help.

Every major version upgrade installs a new kernel version, and the restricted drivers are kernel version specific.  So, if you're running the restricted drivers, you will have to upgrade them every time you upgrade Ubuntu versions.

---

### Post by markbuntu on 2010-03-06
Umm.. actually your safest bet would be to uninstall any proprietary driver before upgrading.

That said, you need to uninstall the old driver


If you are using a driver that you downloaded from the ati site and installed it using the installer there is a removal script that you can use:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh

```


If you installed the driver using  Jockey (hardware manager) then that means the driver is from the Ubuntu repository and has been packaged a little differently so you will need to remove it as follows (you may also need to use this method if you used dpkg to build and install the driver):
```

sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev

```
The driver also may replace the following files with proprietary versions so you may need to restore them to their generic state:
```

sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core

```

If you use Envy to install the driver, use Envy and chose remove completely.

Reboot into recovery kernel and use the fix-x option or "repair broken packages" to get to the generic VESA driver working.  You can verify that the VESA driver is in use by checking in /var/log/Xorg.0.log. 

Then you can use hardware driver to install the driver or get the latest one from ati and install that instead.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Penguin Guy on 2010-03-07
Sorry, looks like I was running the old kernel. Now I've updated grub to run the new one everything seems to be working fine.

Thanks.

---

