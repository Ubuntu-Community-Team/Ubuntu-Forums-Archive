---
title: "Are you experiencing these problems?"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cheesypoof on 2009-09-05
When I "sudo nautilus" I receive this message and in addition it does not launch the program.
> Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x00 0x00 0x00 0x00 0x00 0x00 
Segmentation fault


In addition, numerous scripts that have worked in the recent past, month or so ago, now no longer work.

Open Terminal here
> cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal
Search here
> cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-search-tool
Open Nautilus(root) here
> foo=`gksudo -u root -k -m "Enter your password to perform administrative tasks" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI

They all seem to have "$NAUTILUS_SCRIPT_CURRENT_URI" in common...

Lastly, very few of the icons of the "Applications, Places, System" are working. The individual programs however are showing up. I am using custom icons, however this only became a problem recently 1-2 weeks ago. I believe this appeared after a human-icon-theme update.

[[IMG]http://img193.imageshack.us/img193/6961/screenshotnp.jpg[/IMG]](http://img193.imageshack.us/i/screenshotnp.jpg/)

Oh, and one more... Are the icons for the search engines appearing in your top right Firefox drop-down menu? They are not for me...

Please let me know if you are experiencing these problems too, or if you have any suggestions on how I can fix them on my computer.

---

### Post by forumache on 2009-09-05
Icons missing: this is intended (and I don't like it as it looks now, I'll see later if I can adapt).
To turn the icons on/off: System|Preferences|Appearance | Interface | Show icons in the menu
Firefox listens to the same setting.
Need to restart firefox (and logout/in again for the main menu, IIRC)

---

### Post by taavikko on 2009-09-05
nautilus fails to run root: [https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/420841](https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/420841)

---

### Post by exploder on 2009-09-05
Funny, they had this fixed and it appears the problem has returned... You can open Nautilus as root with this command.

```
sudo dbus-launch nautilus
```

---

### Post by X10N on 2009-09-05
Works for me. I get this output;

```
lulicus@X10N-PC:~$ sudo nautilus
[sudo] password for lulicus: 

** (nautilus:32639): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:32639): WARNING **: No marshaller for signature of signal 'DownloadFinished'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

---

### Post by cheesypoof on 2009-09-06
Thank you all for your input and answers to my aforementioned problems. :D

---

