---
title: "creative webcam not working in skype on 64bit natty"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by rvchari on 2011-05-10
hi, i am presently trying out natty 64 bit from my live usb stick. i installed skype from software center. my lappy has an integrated cam that needs to be serviced so i plugged in a creative webcam thru the usb port,

lsusb lists the cam and skype also shows the option in the drop down menu list of video devices. when i hit the test button, it displays nothing....

i also tried this command

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

still webcam doesnt work, any clue or any further configuration needed ?

---

### Post by lechien73 on 2011-05-10
To pre-load that library, you need to install the Ubuntu Restricted Extras, so make sure that is available first. You can install it by opening a terminal window and typing:

```
sudo apt-get install ubuntu-restricted-extras
```

Also, if you're using 64-bit Ubuntu, then you need to issue the command:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

The difference between this and your command is that it gets the library from /usr/lib32 instead of /usr/lib.

---

### Post by rvchari on 2011-05-10
thanks buddy... lib32 did the trick...
hats off to our forum members !!!

---

### Post by sasabgd84 on 2011-07-30
I have bad information, I use Natty x64 i tried post abbove, but get me this on terminal:

noname@noname:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3164): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:3164): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3164): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3164): Gtk-WARNING **: Loading IM context type 'ibus' failed
noname@noname:~$

---

### Post by sasabgd84 on 2011-07-31
When Iam in tools-video-test, tested webcam works perfect, but in video call conversation permanent loading, and people can not see me...My upload is 512 kb/sec :-(  Please people help me...

---

