---
title: "unity stopped working after upgrade to trusty"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by mariuss on 2014-08-10
I upgraded to trusty from 13.10 and as far as I can tell Unity stopped working. I get the login screen, but after entering username and password I get a screen with only a standard wallpaper. There is a mouse cursor, but it does not do anything, right clicking does not pop up a menu.

I can login using one of the Ctrl-Alt-Fx terminals, run updates and all.

Any suggestions?

There is no /etc/X11/xorg.conf file. The video card is ATI and I think fglrx is supposed to be the driver. Tried to start in safe mode and that does not work, it hangs on a screen that says something about fsck, I let it there a long time, it is not fsck hanging.

Thanks

---

### Post by mariuss on 2014-08-10
Just looked at /var/log/lightdm/x-0.log and noticed some errors there:

modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='fglrx_updates'
modprobe: ERROR: could not insert 'fglrx_updates': Function not implemented

The fglrx-updates and fglrx-amdcccle-updates packages are installed, and these seem to be the only fglrx* packages. I can try installing fglrx, just don't understand why would it be missing, and trying not to make things worse.

---

### Post by mariuss on 2014-08-10
Installed fglrx, fglrx-updates was uninstalled, and still getting the same error:
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='fglrx'
modprobe: ERROR: could not insert 'fglrx': Function not implemented

Is this a LightDM bug?

---

### Post by grahammechanical on 2014-08-10
It most likely is a video driver conflict. As you are getting to a desktop but with only the wallpaper, you can try this: Right click the desktop wallpaper and select Change Desktop Background. That will load System Settings and from there you can open Software and Updates>Additional Drivers tab. You need to be connected to the internet and to allow the utility time to search for drivers. Then experiment.

Regards.

---

### Post by mariuss on 2014-08-10
Thanks, but as I mentioned right clicking does not bring up any menus.

I purged the fglrx driver, supposedly that switched me to radeon, and finally I can login. But now there is no HDMI sound, and apparently that should be on by default in trusty. I followed these instructions:
[https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver](https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver)

Tried to re-install fglrx, run into the exact same problem as before. This is rather strange because I have another computer, exactly same video card, and it is running fglrx happily, with trusty as well.

---

### Post by kansasnoob on 2014-08-10
I encountered a bug while performing Saucy -> Trusty upgrades:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721)

Just for fun (won't blow anything up) run:

```
sudo update-grub
```

Then:

```
sudo apt-get -f install
```

Then do whatever that recommends - if anything. Then reboot and try going through the whole graphics driver thing again.

---

### Post by mariuss on 2014-08-10
Mystery solved. For whatever reason I had an old kernel, 3.8.0-26. The linux-generic and linux-image-generic packages were not installed, not clue how that happened, and basically the kernel would never update. linux-headers-generic was installed, so I was getting the latest headers (and old binaries). After installing linux-generic and linux-image-generic everything stated to work. Both radeon and gflrx, and HDMI audio.

Thanks for the pointers.

---

### Post by kansasnoob on 2014-08-11
> **mariuss said:**
> Mystery solved. For whatever reason I had an old kernel, 3.8.0-26. The linux-generic and linux-image-generic packages were not installed, not clue how that happened, and basically the kernel would never update. linux-headers-generic was installed, so I was getting the latest headers (and old binaries). After installing linux-generic and linux-image-generic everything stated to work. Both radeon and gflrx, and HDMI audio.

Thanks for the pointers.

That's basically what happened to me, only mine was the 3.11 kernel:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721/comments/4](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721/comments/4)

I still found more slightly borked packages that failed to upgrade though :(

It did finally resolve after several go-arounds with apt-get -f install and apt-get install ubuntu-desktop (but maybe you're not using ubuntu-desktop) so your mileage may vary.

---

### Post by mariuss on 2014-08-11
Good point, there could be other packages that have been dropped. I checked and ubuntu-desktop is installed.

How does "apt-get -f install" help? Isn't it forcing an install?

---

### Post by kansasnoob on 2014-08-11
> **mariuss said:**
> Good point, there could be other packages that have been dropped. I checked and ubuntu-desktop is installed.

How does "apt-get -f install" help? Isn't it forcing an install?

It just looks for issues to resolve, like unmet dependencies, partially installed packages, packages that may not have upgraded, or packages to autoremove. It's mostly informative.

---

### Post by mariuss on 2014-08-11
I see, thanks. "apt-get -f install" did not find anything either.

---

