---
title: "Three problems after upgrade"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by outlikeashoe on 2008-11-03
Firt of all, I had problems with this upgrade since wednesday.
#1 - When I click on the main menu "places" -> "home" or the other places in the first group, it open up amarok instead nautilus.
#2 - The wlan0 interface doesn't work, it's a Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61). It worked well with Hardy, now it won't work.
#3 - The alsamixer command now has only the Master configuration, before the update there was at least the the front, the microphone, the line in and the surround channels.

Thanks in advance to everyone who will reply.

---

### Post by tuxxy on 2008-11-03
> **outlikeashoe said:**
> Firt of all, I had problems with this upgrade since wednesday.
#1 - When I click on the main menu "places" -> "home" or the other places in the first group, it open up amarok instead nautilus.


This is a well documented bug in Ibex, see the report

[https://bugs.launchpad.net/ubuntu/intrepid/+source/gnome-panel/+bug/260492](https://bugs.launchpad.net/ubuntu/intrepid/+source/gnome-panel/+bug/260492)

To make life easy for you simply you need to edit and remove a line from your .local/share/applications/mimeapps.list

```
sudo gedit .local/share/applications/mimeapps.list
```

The line amy look similar to  

```
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
```

If you are unsure post the output here and Ill see if I can see it :

---

### Post by outlikeashoe on 2008-11-03
Thanks, that line was:
inode/directory=kde-amarok.desktop;nautilus-folder-handler.desktop;kde4-kdesvn.desktop;phatch.desktop;nautilus.desktop;userapp-nautilus-04AJJU.desktop;
I've modified placing nautilus as first instead amarok.

Now the problems are only two..

---

### Post by florus on 2008-11-03
The Intel 4965 bug is causing a lot of problems and the fix is covered in the 8.10 release notes - Known Issues on the Ubuntu website.

---

### Post by outlikeashoe on 2008-11-03
I googled for the release notes, I've seen that:
> Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug.
I'll try installing that package with Synaptic and let you know.

---

### Post by outlikeashoe on 2008-11-03
Done.. it works.. Now the minor problems:
- alsa channels
- multimedia keys (acer aspire 5920g) I had fixed them for gutsy and hardy, but now they doesn't work again..

---

