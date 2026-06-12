---
title: "Help needed for a fresh installation - looking to move on from Ubuntu Studio"
date: 2017-01-29
forum: Installation &amp; Upgrades
---

### Post by william37 on 2017-01-29
Ok, so - I'm currently running Ubuntu Studio on my laptop (Lenovo Z560). It is super buggy, glacially slow, and pops up error messages every time I boot up. I want to start fresh with a new install of plain ol' Ubuntu.

When I look up how to create an Ubuntu installation, it asks you to download the ISO, which I've done, but then asks me to open the 'Startup Disk Creator.' I cannot find this in Ubuntu Studio, and searching for it in the software repository returns zero results.

Can anyone point me to directions for creating a fresh Ubuntu install that doesn't require the Startup Disk Creator?

---

### Post by Bashing-om on 2017-01-29
william37; Hello;

Be aware that the ubuntu .iso file is what is termed as hybrid, as such in linux we can write the image directly with the 'dd' tool;
To a USB device . Ya got a thumb drive handy ?
If you have low spec hardware, you are advised to consider installing (L)ubuntu - as it is optimized for lower end hardware. 

But be very very careful ! Know what the source is and make sure you KNOW the target . 'dd' is well known as (D)isk (D)estroyer.
verify the downloaded .iso file with md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Now identify the devices you are working with:
terminal command:
```

sudo parted -l

```
and write the image to the USB device :
```

sudo dd if=/path/to/iso of=/dev/sdX bs=4M && sync

```
where the X in sdX is from the output of 'parted' , identifying the USB device .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-01-29
Or use UNetbootin or one of  the many other USB creators. Univeral USB installer is another.

You understand that Ubuntu is not exactly slimline and has a different desktop environment (Unity and not xfce4)? What are your machine specs? It might not make a lot of difference if they're low. If you want speedy, try Xubuntu-core. That would look exactly the same as UStudio, but without the million and one AV apps you may never use or want. ;)

---

### Post by william37 on 2017-02-12
Thanks for the reply! I'm running a 2.67 Ghz i5 processor with 4 GB of RAM. Maybe Xubuntu-core or Mint would be preferable?

---

### Post by Bashing-om on 2017-02-12
william37; Hey ...

With that system ya can throw on it what ever your little heart desires.
Should perform admirably .

[INDENT][INDENT]just do it
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2017-02-13
Startup Disk Creator is trivial to install.
Look for the package 'usb-creator-gtk'

---

