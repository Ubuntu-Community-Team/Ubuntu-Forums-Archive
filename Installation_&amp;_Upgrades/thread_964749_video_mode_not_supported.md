---
title: "video mode not supported"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by 7Sasha on 2008-10-31
Heya. I'm trying to setup ubuntu 8.10 .
When booting from CD and choosing 'Install ubuntu' , I see a screen message  'video mode not supported' . Same as when trying to start ubuntu without installing from CD.

When trying to install and pressing ctrl alt f1
I get a black screen with the message 'loading.. please wait', 
that never changes.

When doing the same with just loading without installing
I get the console version. 

sudo dpkg-reconfigure xserver-xorg
and enabling kernel buffer w.e. didn't help neither after
sudo /etc/init.d/gdm restart   nor after
sudo shutdown -r now


sudo lspci | grep VGA  says 
01:05.0 VGA compatible controller: Ati technologies Inc RC410 [Radeon Xpress 200]

grep -i driver /etc/X11/xorg.conf    no results


so how do I install ubuntu ?
Thanks in advance.

---

### Post by 7Sasha on 2008-10-31
sudo gedit /etc/X11/xorg.conf says
(gedit:7146): Gtk-WARNING **: cannot open display:

---

### Post by 7Sasha on 2008-10-31
Help...

---

### Post by BlackIrish on 2008-10-31
Hey dude, there's not much we can do...

I also have the same problem, and chances are we won't be getting a fix any time soon... :(

---

### Post by reiki on 2008-10-31
Look in /etc/hal and see if there is a file with a refresh rate out of spec for your monitor. You could also look in /etc/dbus , but I have a feeling you'll have better luck in /etc/hal

dpkg-reconfigure xserver-xorg doesn't fix this and neither does booting to a failsafe and trying xfix.

---

### Post by mootpoint on 2008-10-31
This may or may not be helpful. I had used envy to install my NVidia drivers in 8.04. When I rebooted into 8.10, my video driver world was a mess. I was lucky, and Gnome gave me some error messages, and I could get into the GUI in low resolution mode. 

I ended up using envyng -t (terminal mode) to remove all drivers I'd installed via envy, and loaded the driver via system/administration/hardware drivers. I'm still not sure it's quite right, but at least I get Gnome in a usable resolution now.

If you used envy to load video drivers, you may want to try the same technique and see if you get anywhere. If you can get network access and a terminal, you can always put it back the same way you take it out.

m00t

---

### Post by 7Sasha on 2008-11-30
Hope this helps:

restart computer
wait till it loads and you get the video mode not supported screen
Ctrl + Alt + F1 to get into console mode
sudo apt-get install envyng-qt

if it doesn't find it, run sudo apt-get install envy and you will get 
a suggestion of the right name.

after complete installation of envy type
sudo envyng -t
to run envy in console mode.

in the menu choose REMOVE *** DRIVER to remove ati or nvidia driver
Don't install anything. Only remove.
after removal - restart.
Done.

---

### Post by ericlovecn on 2008-11-30
> **7Sasha said:**
> Heya. I'm trying to setup ubuntu 8.10 .
When booting from CD and choosing 'Install ubuntu' , I see a screen message  'video mode not supported' . Same as when trying to start ubuntu without installing from CD.

When trying to install and pressing ctrl alt f1
I get a black screen with the message 'loading.. please wait', 
that never changes.

When doing the same with just loading without installing
I get the console version. 

sudo dpkg-reconfigure xserver-xorg
and enabling kernel buffer w.e. didn't help neither after
sudo /etc/init.d/gdm restart   nor after
sudo shutdown -r now


sudo lspci | grep VGA  says 
01:05.0 VGA compatible controller: Ati technologies Inc RC410 [Radeon Xpress 200]

grep -i driver /etc/X11/xorg.conf    no results


so how do I install ubuntu ?
Thanks in advance.

It seems as if the latest Video Card Driver do not support the 8.10 perfectly, so we r gonna wait some time...

---

### Post by scudscucker on 2009-07-15
> restart computer
wait till it loads and you get the video mode not supported screen
Ctrl + Alt + F1 to get into console mode
sudo apt-get install envyng-qt

if it doesn't find it, run sudo apt-get install envy and you will get 
a suggestion of the right name.

after complete installation of envy type
sudo envyng -t
to run envy in console mode.

in the menu choose REMOVE *** DRIVER to remove ati or nvidia driver
Don't install anything. Only remove.
after removal - restart.


Solution worked for me, thank you very much.

---

