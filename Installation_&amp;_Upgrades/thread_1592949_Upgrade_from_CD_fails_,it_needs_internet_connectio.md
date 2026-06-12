---
title: "Upgrade from CD fails ,it needs internet connection &amp;  not using packages on cd"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by radiobert on 2010-10-11
This problem looks much like a bug for me...
Stated by the title, I use the CD upgrade method to upgrade my kubuntu 10.04 to 10.10.
Not to mention,the ISO image of the CD is this one :kubuntu-10.10-alternate-i386.iso

 At the first run I choose YES for the prompt asking for internet connection or whatever, but I immediately realise that I have chosen a wrong option, so I exit and restart the upgrade all over again.
On the second run, I choose NO for the prompt , then the installation continues until it reaches the 'fetching files' stage. It pops up and says "The upgrade has aborted. Please check your internet connection or installation media and try again. All files downloaded so far are kept."
```
" p, li { white-space: pre-wrap; } Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev_2.26.0-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.26.0-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/pkg-config_0.25-1_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-dev_1.4.0-0ubuntu1_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/libqt4-webkit_4.7.0-0ubuntu4_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6-dev_2.4.2-2_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libxau/libxau-dev_1.0.6-1_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/x/x11proto-core/x11proto-core-dev_7.0.17-1_all.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libxdmcp/libxdmcp-dev_1.0.3-2_i386.deb Could not resolve 'archive.ubuntu.com'
 Failed to fetch..................
"

```I don't want to reinstall the whole system again because I want my applications;
I don't want to use the updater to upgrade because I have a low internet speed .

What do I need to do ?

---

### Post by mörgæs on 2010-10-11
Why don't you want to have internet access during installation? Downloading and installing bugfixes is an important part of the process.

---

### Post by radiobert on 2010-10-11
Please, as I said... I have slow internet . If I want to update, I can always update later on.  I need help regarding the problem, on how to reset the settings or what.. Thanks for your consideration anyways...

---

### Post by mörgæs on 2010-10-11
Yes, that was exactly what I did not understand. You will need to download a lot of bugfixes anyway in the future, no matter how you install the system, so why not begin right away?

All right, your decision.

---

### Post by radiobert on 2010-10-11
You can try think of 10 computers connected to one internet line...if I use the online method for every computer then it would comsume 10 times the bandwidth of the offline method....


Ok, now I solved the problem....By using the kpackagekit to upgrade, and canceling it when it starts to download, the CD upgrade method can be used again without the problem mentioned above.


Ironically it says "could not calculate upgrade" because the update-manager-kde is marked for removal but is in the removal blacklist. I speculated that there are broken packages, so I resorted to use aptitude to fix it...and  it turns out there are indeed broken packages(dependencies)

---

### Post by radiobert on 2010-10-11
Yes, now the CD upgrade works....:)

---

