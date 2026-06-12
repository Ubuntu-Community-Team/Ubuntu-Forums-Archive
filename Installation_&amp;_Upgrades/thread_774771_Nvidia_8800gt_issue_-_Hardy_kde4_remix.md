---
title: "Nvidia 8800gt issue - Hardy kde4 remix"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by sixpounder on 2008-04-29
I really hope someone can help me out.
I just installed a new Hardy Heron Kde4 Remix on my desktop. Downloaded 169.12 proprietary drivers from nvidia.com and installed them. I used nvidia-xsettings to reconfigure xorg.conf and it gave me no errors. I start again the kdm-kde4 and everything works fine, including compiz.

BUT: as I restart my pc, everything stop working: X can't start, saying that it's unable to INITIALIZE nvidia kernel module.

What can I do?
Thank you everybody...

EDIT: if I reinstall 169.12 drivers, everything works perfectly... until next reboot :'(

---

### Post by Lord Landis on 2008-04-29
Do you get this issue if you disable Compiz?

Try re-configuring X to use the free nvidia driver, disable Compiz, and then re-install nVidia's driver.  Also, please post the full error message that Xorg gives you when you start, including the error code.

---

### Post by sixpounder on 2008-04-29
Compiz has nothing to do with this... I re-installed kubuntu 3/4 times and always got the same issue.

The error message is simply Failure to initialize NVIDIA kernel module. Above this, it says that kernel module is versione 71.something and driver module is 169.12, and so API mismatch. I can I fix this? ...

---

### Post by skunkTrader on 2008-04-29
As far as I can tell the 169.12 drivers are included with the Hardy distribution.  I don't think you need to download anything from the nvidia web site.

---

### Post by sixpounder on 2008-04-30
Using included drivers (nvidia-glx-new) gives the same effect :confused:

---

### Post by Micool on 2008-05-06
I also have problems with these proprietary drivers on hardy +kde 3.5.9 X starts, but kdm first load is realy slow... I need to restart X and then KDM and KDE run properly with hardware acceleration...

at each boot up, KDM is slow until X is restarted. Default drivers works fine...

Graphic card is a Nvidia 8800 GTX..

Any ideas ? do you have same effects ?

---

### Post by eudemus on 2008-05-08
Disastrous problems on Hardy KDE4 remix.
Tried the 'proprietary drivers' prompt, using drivers from the repositories, EnvyNG, and downloading direct from nvidia. Nothing worked. Dreadful low-res display was the best I could get.

Also, a load of nice functionality in KDE 3.5 had gone (like storage device management tool)

Gave up. Did clean install of Hardy KDE 3.5.9 instead.
Worked like a dream, pretty much, straight from the off.

I believe there are many saying, "steer well clear of KDE4", and that's well borne out by my experience.

I dare say, Micool, that some problems aren't confined to KDE4. All I can say is, just think how much worse they would be if you were trying to run "remix"!!

---

### Post by brendan.lefoll on 2008-05-08
have you considered installing the normal version of ubuntu (8.04 with gnome) and then doing an apt-get update, apt-get upgrade, reboot, install the nvidia drivers from the restricted device manager in gnome, do an apt-get install kde4 and choose kdm, remove gnome with an apt-get remove gnome if you dont want it, and voila it should work.

There probably is a bug with the kde4 remix drivers. I'm using the nvidia-glx-new drivers on my 8600GT 512MB on a ubuntu 8.04LTS install and all is fine, I installed the way I described above, because i've had problems with kubuntu installs before, and well I don't use kde4 i'm still on kde3 with compiz, but kde4 works fine for me and i use kde4-kdm.

---

