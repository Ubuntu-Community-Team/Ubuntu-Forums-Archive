---
title: "Computer Slowed to a crawl after today's update"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mxboy15u on 2009-10-07
I was enjoying Karmic until these last 2 updates. First suspend disappeared and now my computer is working at about 1/8 the speed. Loading any menu takes forever, as does typing in open office etc. I had more luck with the Alphas than I have with this beta. Any advice or do I just need to wait until I get home to put a fresh image on this machine?

---

### Post by TrueTom on 2009-10-07
Use [FONT="Courier New"]top[/FONT] in a console to see if there is a process that eats all CPU cycles. Gnome-Do is a usual suspect...

---

### Post by dino99 on 2009-10-07
are your .xsession-errors or / and logs helpfull ?

---

### Post by mxboy15u on 2009-10-07
I will look at these after lunch, thanks for the quick advice.

---

### Post by tuahaa on 2009-10-07
Me too, well, sometimes atleast. It sometimes comes up with errors and then continues starting up, and then loads ubuntu 9.10 Beta, which is really slow. Other times, no errors come up and then it works faster than ever. They might have stuffed up the updates...

Meh, I think that's why they call it a beta.

---

### Post by rex4u on 2009-10-07
Same here too...:(

---

### Post by pharnet on 2009-10-07
For me netbook-launcher is using 100% cpu and the only thing odd I notice is this:

Oct  7 14:47:13 he kernel: [    4.977668] [drm:drm_fill_in_dev] *ERROR* Cannot initialize the agpgart module.
Oct  7 14:47:13 he kernel: [    4.977737] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Oct  7 14:47:13 he kernel: [    4.977803] DRM: Fill_in_dev failed.
Oct  7 14:47:13 he kernel: [    4.977859] i915 0000:00:02.0: PCI INT A disabled
Oct  7 14:47:13 he kernel: [    4.977883] i915: probe of 0000:00:02.0 failed with error -22

Wasn't there an Intel xorg update today? My theory is that accelerated or 3d graphics magic may not be working and cpu is picking up the slack?

Just pure speculation.

---

### Post by slakkie on 2009-10-07
I have the same problem. I restored a backup of yesterday, disabled upgrading of all xorg related packages and kernel related packages.

Upgraded xorg packages first: no issue
Upgraded kernel packages: no issue

Although I did notice the problem before the xorg upgrade earlier today.

---

### Post by wilee-nilee on 2009-10-07
This may not fix your problems but try to run,in the terminal.
sudo apt-get autoremove    and sudo apt-get autoclean 
fairly often to clean out the cache and unneeded packages.
look carefully at the autoremove and keep at least two working kernels.

---

### Post by pharnet on 2009-10-07
> **wilee-nilee said:**
> This may not fix your problems but try to run,in the terminal.
sudo apt-get autoremove    and sudo apt-get autoclean 
fairly often to clean out the cache and unneeded packages.
look carefully at the autoremove and keep at least two working kernels.

Tried this and performed another apt-get update and upgrade. Updates with libglb2.0-data_2.22.2-0, libglb2.0-0_2.22.2-0, libgtk2-perl, and libkpathsea4_2007.dfsg.2-7. Restarted. Seems to be ok for me now?

---

### Post by mxboy15u on 2009-10-08
Today's update fixed the problem on both of my test computers. I wonder what fun lies ahead in this "beta"???

---

