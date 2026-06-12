---
title: "How to build a bootable USB (7 Gb)"
date: 2019-05-08
forum: Installation &amp; Upgrades
---

### Post by Forecaster on 2019-05-08
Hi all!

We want to install 16.04 (17.10 or 18.04) through USB on internal sda for old laptop. Where to read an instruction how to build a bootable USB for these versions? 

Regards,
Sergey.

---

### Post by Rubi1200 on 2019-05-08
Hi,

Are you currently using Windows as your main operating system?


If yes, go here and download Rufus [https://portableapps.com/apps/utilities/rufus-portable](https://portableapps.com/apps/utilities/rufus-portable)


Double click the file and follow instructions to install.


Once done, open the application and put the USB stick you want to use in the computer (Rufus will detect it automatically).


Then click Select and browse to where you saved the ISO image of 16.04 and add.


Click start.


There might be a warning about syslinux files just click yes and yes to ISO Image (Recommended) and yes to you know it will overwrite any data on the stick.


Then just wait until finished.


Once done you can close Rufus, take out the stick and then you have a bootable Ubuntu to try out.


Depending on whether you have legacy BIOS or UEFI you may need to figure out how to enter and select the option to boot the stick but let's first get you a bootable Ubuntu stick before we take the next steps.

---

### Post by C.S.Cameron on 2019-05-09
Programs for making bootable USB - [https://askubuntu.com/questions/674441/what-is-the-proper-way-of-creating-installation-media-from-ubuntu-iso/1069189#1069189](https://askubuntu.com/questions/674441/what-is-the-proper-way-of-creating-installation-media-from-ubuntu-iso/1069189#1069189)

---

### Post by Impavidus on 2019-05-10
Keep in mind that 17.10 is dead. Don't install it. 16.04 and 18.04 are both OK, but there's rarely a reason to prefer 16.04 over 18.04. If the laptop is too old to run the latest long term support release of Ubuntu smoothly, try a lighter flavour, not an older release.

---

### Post by Forecaster on 2019-05-17
I killed other OS
I made all as it was proposed. But installing of UBUNTU over other OS killed it. I have used 18.04. Is it possible to restore other killed OS?

---

### Post by Impavidus on 2019-05-17
If you install one OS, overwriting another OS, the other OS is gone. You can get it back by reinstalling it. The installer won't mind overwriting your new OS.

---

### Post by Rubi1200 on 2019-05-18
@Forecaster,

Unfortunately, if you choose the option to erase and use the whole disk then anything that was there before will be gone.

If you have a Windows licence and product key you can reinstall Windows then reinstall Ubuntu but you MUST choose the Install Alongside option otherwise you will be back in the same situation.

You say in the first post it is an old laptop; please provide us with the make and model and specifications such as RAM and graphics card.

Also, what version of Windows was on the laptop? I am assuming it was Windows but if it was Mac then please also let us know which version.

Thanks.

---

