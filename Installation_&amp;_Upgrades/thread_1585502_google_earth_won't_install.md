---
title: "google earth won't install"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by catlover2 on 2010-09-30
hi, i followed these instructions, but i get this error:


 ```
reed@reed-laptop:~$  cd ~/Downloads
reed@reed-laptop:~/Downloads$  chmod +x GoogleEarthLinux.bin
reed@reed-laptop:~/Downloads$  sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
reed@reed-laptop:~/Downloads$ 

```


         Download Google Earth from the [Google Earth website]("http://earth.google.com/"). 

[LIST=1]
[*]  [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/icon-info.png[/IMG] The linux version will be automatically chosen when downloading from Ubuntu. 
[*]Open a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") from **Applications** -> **Accessories** -> **Terminal**. 
[*]**cd** into the directory where you saved Google Earth. For example, if you saved it to the Desktop type: 
 cd ~/Desktop
[*]Make it executable by typing: 
 chmod +x GoogleEarthLinux.bin
[*]Run the installer by typing: 
 sudo ./GoogleEarthLinux.bin
[*]Leave the default options and click **Begin Install**. 

 [IMG]https://help.ubuntu.com/community/GoogleEarth?action=AttachFile&do=get&target=googleearth-setup-1.png[/IMG] 
[*]When installation is complete, press **Quit**. 
 [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/alert.png[/IMG] Do **not** press *Start* as this will run it as root which is never a good idea. 

 [IMG]https://help.ubuntu.com/community/GoogleEarth?action=AttachFile&do=get&target=googleearth-setup-2.png[/IMG] 
 
[/LIST]
[IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/icon-info.png[/IMG] A file named Google-googleearth.desktop will be installed on the Desktop. This file is safe to delete. 
 
[B][SIZE=1]thanks, catlover[/SIZE]
[/B]

---

### Post by davidmohammed on 2010-09-30
I found this on a quick google.  Hope it works for you

```
./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh
```

---

### Post by catlover2 on 2010-09-30
> **davidmohammed said:**
> I found this on a quick google.  Hope it works for you

```
./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh
```


it sort of worked, except there is no earth!!

there were some errors:
```
reed@reed-laptop:~$ cd ~/Downloads
reed@reed-laptop:~/Downloads$ ./GoogleEarthLinux.bin --target /tmp/ge
Creating directory /tmp/ge
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
reed@reed-laptop:~/Downloads$ cd /tmp/ge/setup.data/bin/Linux/x86/
reed@reed-laptop:/tmp/ge/setup.data/bin/Linux/x86$ mv setup.gtk setup.gtk2
reed@reed-laptop:/tmp/ge/setup.data/bin/Linux/x86$ cd /tmp/ge
reed@reed-laptop:/tmp/ge$ ./setup.sh

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
reed@reed-laptop:/tmp/ge$ 

```

and everything in options in grayed out... 

thanks, catlover

---

### Post by catlover2 on 2010-09-30
update:

if i run it in safe graphical mode or OpenGL emulation mode there is an earth,
but it is *very* slow!

---

### Post by davidmohammed on 2010-09-30
... dont know - 

googling "Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so"" has some hits and some suggested fixes.

I've installed googleearth from the medibuntu repository.  Works for me.  See [here]("http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/") for some instructions.

---

### Post by catlover2 on 2010-09-30
ok, it installed a missing package, but it's still slow as heck!

---

### Post by davidmohammed on 2010-09-30
suggest untick some of the graphic intensive options - from the View menu untick all of the atmosphere, water etc effects.


Play with Tools - Options.  Make sure Terrain Quality is fastest and Map Size is smallest.

---

### Post by catlover2 on 2010-09-30
grrrrrrr!

still slow! i did all you mentioned.

---

### Post by davidmohammed on 2010-09-30
is it just google earth specifically slow with graphics - or do you have slow graphics in general e.g. can you play full screen flash videos etc?

Graphics Driver? 
Graphics Card (lspci | grep VGA)

Specification of your PC (Ram, processor)?

---

### Post by catlover2 on 2010-09-30
not sure about the drivers.

```
reed@reed-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
reed@reed-laptop:~$
```
intel celeron 1.40 ghz 512 MB/RAM


no, youtube vids will not fullscreen well at 360p.

---

### Post by davidmohammed on 2010-09-30
I'm also running a 855GM - yes google earth does run a little slow - your processor doesnt help since it is quite slow.

Do you start xbuntu with "xforcevesa" in your grub - or do you run with a customised "/etc/X11/xorg.conf" file?

Did you remember to untick "safe graphics" in google earth?

---

### Post by catlover2 on 2010-09-30
sorry, i run ubuntu not xbuntu, i'll update my specs.

i forgot to uncheck safe graphics, but now, after a restart, google earth won't start at all!!

---

### Post by davidmohammed on 2010-10-01
any errors reported if you run googleearth from a terminal session?

---

### Post by catlover2 on 2010-10-10
here is the output from running it from the terminal:
```
reed@reed-laptop:~$ googleearth
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x83b5bb0)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x83f8320)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x83b5930)" of type `gboolean'
reed@reed-laptop:~$ 

```

catlover

---

