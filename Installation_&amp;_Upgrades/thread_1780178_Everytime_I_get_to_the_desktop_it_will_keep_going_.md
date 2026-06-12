---
title: "Everytime I get to the desktop it will keep going back to login"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Majestic 888 on 2011-06-11
So I'm trying to install Ubuntu 11.04 and I'm selecting the option that says try Ubuntu without installing and I will get to the desktop and after like 5-10 seconds it will go black than go to the log in screen and I use "ubuntu" as the username and no password and log back in and it just repeats itself.

I have tried installing Ubuntu with a Live CD and with the USB and same problem. And when I select install Ubuntu I will just get the "the installer encountered an unrecoverable error" error. I have also tried downloading different minors of the ubuntu .iso and no luck!

I have also reformatted my hard drive to ext3 with gparted live. I just don't know what to do next I have been trying to install Ubuntu all day!:(


PS. Also tried using the Ubuntu Alternate with the USB but I have no idea were to start. I can only access the rescue mode.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Majestic 888 said:**
> So I'm trying to install Ubuntu 11.04 and I'm selecting the option that says try Ubuntu without installing and I will get to the desktop and after like 5-10 seconds it will go black than go to the log in screen and I use "ubuntu" as the username and no password and log back in and it just repeats itself.

I have tried installing Ubuntu with a Live CD and with the USB and same problem. And when I select install Ubuntu I will just get the "the installer encountered an unrecoverable error" error. I have also tried downloading different minors of the ubuntu .iso and no luck!

I have also reformatted my hard drive to ext3 with gparted live. I just don't know what to do next I have been trying to install Ubuntu all day!:(


PS. Also tried using the Ubuntu Alternate with the USB but I have no idea were to start. I can only access the rescue mode.

Does this happen with 10.10?

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Majestic 888 on 2011-06-11
Have not tried it with 10.10, downloading it now.

---

### Post by WallyJ2K on 2011-08-02
Please let us know what happens and if you find a solution. I am having the same thing happen with the 11.04 Live CD, on an old laptop that runs XP just fine.

After receiving the "Installation Failed" message, and clicking OK to start a "Desktop", it slowly runs, goes black, then the colorful background, then a login screen. If I use ubuntu/blank it logs in for a quick second, showing the spinning circle and making the Ubuntu sound, then goes back to the login screen again. This login loop never ends.

I think it has to do with my video driver (HP Pavilion ze4900 with an Intel Xtreme video card). BTW, this has happened with 2 different USB HD's and an iso burned to DVD)

Any help is appreciated.

Thanks,

WallyJ2K

---

### Post by WallyJ2K on 2011-08-03
UPDATE:

Ok... So... in an attempt to continue the remedy of my situation I burned tried the CD again. This time I hit F6 at boot to bring up the menu. I hit F6 again to set the nomodeset and acpi-no(??) options for the "Try Ubuntu" option. I alos removed the quiet splash and manually typed in "nomodeset" at the end of the line.

When I hit Enter, it loaded into a Ubuntu desktop session, with no login screen at all.

However, when I double-clicked the "Install Ubuntu" icon on the desktop it went through restarting the Ubuntu session and sent me back to the login loop.

So I thought I would try the same changes at boot with F6, this time using the "Install Ubuntu" option. That didn't work. It still sent me into the login loop.

Ideas?

Thanks,

Walter

---

