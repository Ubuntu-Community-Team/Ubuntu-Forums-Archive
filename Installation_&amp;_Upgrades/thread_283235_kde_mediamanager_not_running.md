---
title: "kde mediamanager not running"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by twidget on 2006-10-23
Hi
i just used automatix to upgrade kde among other things and it works fine except now kubuntu doesnt automaticaly mount flash drives anymore (i havent tried manualy)and when i click on media in conqueror i get a message that the kde media manager isnt running. does anyone know how i can either fix this or safely downgrade to the version of kde that worked? i would just re-install but ive got too much stuff on here already. also does anyone know how to lower the resolution for the kde sign on screen? i have to use a smaller monitor than the one i used when installing and my screen goes out of range just for the user/password screen. this problem is why i tried upgrading to begin with but it didnt fix it.](*,) 
thanks

---

### Post by Phlosten on 2006-10-24
not sure about your media manager problem, however I may have a solution for your x display issue.

you may need to edit your /etc/X11/xorg.conf file and remove the higher resolution settings. Open your /etc/X11/xorg.conf file for editing from a terminal using 'sudo nano /etc/X11/xorg.conf' and find the following section that looks like this:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "PHILIPS 107S"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection
```

Now the section you want to concentrate on is the one that is set as the default depth. For instance my default depth is "24"

```
DefaultDepth    24
```

This means the following section is what will be used to setup my X resolution.
```

        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
```

what you want to do is remove the higher setting. In my case it would be the "1280x1024". Just delete that small section leaving the "1152x864" as the first entry and then save the file (ctrl-n, then ctrl-x for nano).

Hopefully retrying X through a reboot or similar will then allow your monitor to display.

If that does not work you could try removing the next resolution down OR changing the DefaultDepth entry to 15 or 16.

Hope this helps.

---

### Post by twidget on 2006-10-24
thanks for pointing me in the right direction. at the bottom of the comments for xorg.conf i found this
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
i ran this and now almost everything works fine including the flash drive thing. the only problem is that now the monitor only works at 640x480.](*,) it saved a backup of the original file so tomorrow im gonna compare them and see if i can fix it so that i get a higher resolution.anyone out there know the best way to do that?

---

### Post by twidget on 2006-10-24
problem fixed thanks for the help.

---

