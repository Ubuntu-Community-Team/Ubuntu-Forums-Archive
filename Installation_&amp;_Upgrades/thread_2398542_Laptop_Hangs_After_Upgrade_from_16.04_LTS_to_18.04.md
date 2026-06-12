---
title: "Laptop Hangs After Upgrade from 16.04 LTS to 18.04 LTS"
date: 2018-08-13
forum: Installation &amp; Upgrades
---

### Post by geeky-1 on 2018-08-13
I just upgraded an old laptop from 16.04 LTS to 18.04 LTS, but after it rebooted, it hangs on the Ubuntu (.....) screen. The hard drive light stops flashing after a while and it initially got stuck on 2 dots loading Ubuntu. I tried rebooting a few more times, but it always freezes up (the second time on 5 white dots, last time on 4 orange dots and 1 white dot). It's an Acer 5630-6288 (Core 2 Duo 1.66 GHz, upgraded to 4 GB and 300 MB 7200 RPM hard drive).

---

### Post by kansasnoob on 2018-08-13
That may have an nVidia Geforce Go 7300 graphics chip, in which case I'd try starting up with the nomodeset boot parameter set temporarily in grub at boot:

[https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

Once booted you'll likely encounter a gorfy screen resolution but you will hopefully be able to find out what graphics chip that laptop has.

If nvidia as I suspect, I also think that uses the nvidia 304 drivers which will probably require using a ppa:

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=bionic](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=bionic)

---

### Post by Autodave on 2018-08-14
I usually don't upgrade because there are usually too many problems to deal with.  I just back up everything that I need to save to an external source and do a clean install. 

If that machine has the Nvidia card in it, you are probably going to have to use the nouveau driver (which *should *work).

---

### Post by Elpenor on 2018-08-14
I had the same issue with a tower system equipped with an Nvidia card.
I suspected an improper upgrade of the drivers/config so I tried first:
    sudo apt purge nvidia*
    ubuntu-drivers autoinstall
I don't know if it did any good but it didn't solve the issue right away.
What did was switching from lightdm to sddm using:
    dpkg-reconfigure lightdm
I'll admit I was on the verge of a backup and reinstall...  ;)

---

### Post by geeky-1 on 2018-08-15
I can't even get to the setup menu now (seems to ignore F2 and just  proceed - also whips past the GRUB so fast I don't even have a chance to  press anything there either), so I think a clean install is my only  option. There's nothing I need on it as it was mostly a clean install of  16.04 and I was just upgrading before trying to sell it since I finally  bought an i7 laptop to replace it. It has Intel GMA 950 graphics, so  not an nVidia problem...

---

### Post by mörgæs on 2018-08-15
If you are going for a fresh install you could use the opportunity to switch to something lighter than Ubuntu, say Xubuntu.

---

### Post by Impavidus on 2018-08-15
If you want to sell that laptop you should wipe the hard drive anyway. And unless the buyer has some very good reason to trust you, he should wipe it again.

---

### Post by geeky-1 on 2018-08-15
A fresh install of 18.04 failed again. So I went back and did a fresh install of 16.04 and it's working again. Before I doubled the RAM to 4 GB and swapped the 5400 RPM 160 GB hard drive with a 7200 RPM 320 GB hard drive I ran Lubuntu 16.04 on it since an older version of Ubuntu ran really slow. Ubuntu 16.04 seemed to run ok with the hardware upgrades.

---

