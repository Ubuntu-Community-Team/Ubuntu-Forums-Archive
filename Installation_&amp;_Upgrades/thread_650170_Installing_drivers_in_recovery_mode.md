---
title: "Installing drivers in recovery mode"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by grrbrr on 2007-12-26
So I am getting the blank screen errors and have searched up the problem for awhile now and still can't get it to work. 

Firstly I got the blank screen when I tried installing, so I got the alternate download and installed in text mode. Now I get the blank screen when I try to load the OS. I have tried changing resolutions and such but I am now thinking its a 8800 GTS problem.

nVidia released a driver update for my card:
[http://www.nvidia.com/object/linux_display_amd64_169.07.html]("http://www.nvidia.com/object/linux_display_amd64_169.07.html")

How do I install this in recovery mode? put the file into a usb stick or a cd? and what will the command be to run?

Thanks.

---

### Post by dreadlord_chris on 2007-12-26
you just need the file to be somewhere accessible - I just leave mine in my Home folder
start you computer booting normally (don't worry about Recovery Mode - shouldn't be necessary, and it would actually be a little more complicated)
When the screen goes blank - hit Alt-F1 - this will bring you to a text-mode console so you can log in...
log in - you should now be in your Home folder
in case it's running - it's a good idea to stop the X server:
```

sudo /etc/init.d/gdm stop

```
if you are using KDE replace gdm with kdm
it'll ask for you password - and then there's a good chance that your screen will go blank again - just hit Alt-F1 again
Now to install the driver: (assuming you downloaded to your home folder)
```

sudo sh ./NVIDIA<TAB>

```
<TAB> means the Tab key - this will complete the name of the install file for you
hit <Enter>, follow the on screen instructions, say yes to let the NVIDIA installer modify your xorg.conf
if everything completes fine there you should be able to restart your X server:
```

sudo /etc/init.d/gdm start

```

---

