---
title: "digikam - no icon, no camera detected"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by rabbit73 on 2010-05-29
Recently upgraded to Lucid Lynx and lost digikam in the process. Reinstalled from the software manager, but there is no icon in any of the menus. Also installed Gtkam and it showed up just fine. 

The only way I can start digikam is from terminal. I can't even navigate to a directory with pictures and get it to open by right clicking on a jpeg and selecting "open with."

When I do get it open it finds my old albums, but it won't connect to my camera. It says "failed to connect." I tried unmounting the camera (saw that solve in older posts) but still no luck. Any help would be appreciated. Already uninstalled/reinstalled and tried sudo apt-get install digikam from terminal window with the same result. Thanks.

---

### Post by ajgreeny on 2010-05-29
Try removing all your hidden files and folders in your home that relate to digikam.  I don't use it now I'm on gnome, but I did when I used kde in the past, and I think there are a number of files and folders in ~/.kde, so search them out and either remove, or better rename them, and try digikam again.

---

### Post by WinRiddance on 2010-05-29
Try direct access via Nautilus file manager ... be sure to enable hidden files and folders. You can make that permanent under settings for Nautilus. If your backup pics and things still can't be accessed, try to force permission to those files/folders by using something like this:

```
sudo chown -R yourusername:yourusername /media/foldername
```

I use an external drive and several partitions. On some of my older data which originated on a WinXP machine and also on an Ubuntu machine where special admin privileges had previously not been established I needed to use that command.

---

### Post by rabbit73 on 2010-05-29
It doesn't appear to be a rights issue. I can see the pictures in Nautilus. I can right click and choose any other application to "open with" and it works (Firefox, F Spot, etc). If I double click any pic it opens with Eye of Gnome by default. I just can't get digikam to work! No icon in the menu but I can start it through terminal. When I do I can edit all teh pics from my existing albums, just can't connect to the camera to import. Any other suggestions?

---

