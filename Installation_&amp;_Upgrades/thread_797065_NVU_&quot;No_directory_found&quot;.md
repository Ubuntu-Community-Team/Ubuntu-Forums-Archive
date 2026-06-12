---
title: "NVU &quot;No directory found&quot;"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by IchBeisse on 2008-05-16
I just tried installing NVU onto my Hardy machine, but I get this error when I try to open it:  "Failed to execute child process "nvu" (No such file or directory)"
I followed these instructions:
[I]Prerequisites: add universe and multiverse repositories.

Open a terminal window and type in:
sudo apt-get install nvu
sudo rm -f /usr/share/applications/nvu.desktop
sudo gedit /usr/share/applications/nvu.desktop

Insert the following lines into the new file:

[Desktop Entry]
Name=Nvu
Comment=Web Development Editor
Exec=nvu
Icon=nvu.xpm
Terminal=false
Type=Application
Categories=Application;Network;

Refresh the GNOME panel with the following command:

killall gnome-panel

After that you can find Nvu in the Gnome menu under Applications -> Internet.[/I]

Any ideas about what I did wrong?

---

### Post by EXCiD3 on 2008-05-17
Try this, open termina and run:
```
locate nvu
```

The output should show the directory to the nvu executable. You should replace the line in nvu.desktop entitled "Exec=nvu" with "Exec=<directory to nvu>" found using the locate command. If you need more help just post the output of the "locate nvu" command and i can show you exactly what to do from there.

---

### Post by Herman on 2008-05-18
I used to use NVU but I use KompoZer now instead.

I believe KompoZer is the modern version of NVU.
KompoZer is easily installable in Ubuntu through 'Applications'-->'Add/Remove', if you have the right repositories enabled.

Is there any special reason why you want NVU as opposed to KompoZer? 

Try KompoZer, you might like it, I do! :)

---

### Post by EXCiD3 on 2008-05-18
> **Herman said:**
> I used to use NVU but I use KompoZer now instead.

I believe KompoZer is the modern version of NVU.
KompoZer is easily installable in Ubuntu through 'Applications'-->'Add/Remove', if you have the right repositories enabled.

Is there any special reason why you want NVU as opposed to KompoZer? 

Try KompoZer, you might like it, I do! :)

Ah i thought i was forgetting something, you are correct. NVU is no longer in development and KompoZer is just NVU with CSS integration. You should use that instead.

---

