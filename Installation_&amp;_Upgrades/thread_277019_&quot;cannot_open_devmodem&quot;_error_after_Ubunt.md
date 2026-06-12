---
title: "&quot;cannot open /dev/modem&quot; error after Ubuntu auto-update - NEED HELP PLEASE"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by tchoklat on 2006-10-13
I have just installed the latest UBUNTU iso file on y dual boot system with XP. All was going great. I and ran the auto-updater last night (dialup 28kbs) and downloaded the 98 megs of updates. All bar a few downloaded and installed automatically. The system then requested a reboot. After I did this I tried to log-on to my ISP through wvdial, as I normally do in a terminal, with 

<$ sudo wvdial> and the response was -

<cannot open /dev/modem>
<no such file or directory>

What have I done?

signed, 

very newbie! (I cannot even work out how to download Automatix!)

---

### Post by helmut_hed on 2006-11-02
tchoklat, you have to go through the modem driver module build process again... each module, once built, is only valid for the kernel version it was built on.  Edgy has a new kernel, so you need to build a new modem driver module...  Follow the directions you used last time, and good luck.

Jeff

---

