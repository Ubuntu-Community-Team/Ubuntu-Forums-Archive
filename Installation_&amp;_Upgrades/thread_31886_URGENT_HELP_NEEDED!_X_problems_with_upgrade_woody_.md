---
title: "URGENT HELP NEEDED! X problems with upgrade woody To Warty"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by karistouf on 2005-05-05
hi ! i was helped by azz to make installation of ubuntu trhuth an external cd rom on USB port.

I have a laptop IBM thinkpad T21 wich CD was ded and no booting on USB port and no access to internet possible

So I made the installation with Kernel fb2.4 thuth floppies of the base of woody

Then apt-get cdrom
apt-get dist-upgrade

then apt-get install ubuntu-desktop

I have noticed that fonts where phaving troubles during installation

X have set to vesa generic  and I would like to re launch the x config to try drivers for S3 savage IX. How to do it ?

Graphical mode is failing. 

Please HELLLLLLPPPPP!!!!  [-X

---

### Post by nad on 2005-05-05
man savage . man xorg.conf . Edit your xorg.conf file to use the savage driver instead of vesa. Sudo /etc/init.d/gdm restart .

---

### Post by karistouf on 2005-05-05
thanks ! i will  do it and test!

---

### Post by karistouf on 2005-05-05
hi, it is not xorg but xfree86.

udev, input rc and pci hotplug failed at launching also

xfree doesn t start.

I came from woody fb2.4 and upgraded it with warty

any idea to launch again the config tool from ubuntu ( like installation pannel a t beginning ?)

I don t find any tools like xsetup to change driver without having to reinstall with flopies Woody, Then upgrade ubuntu warty THEN install ubuntu-desktop

---

### Post by nad on 2005-05-05
dpkg-reconfigure xserver-xfree86

Be prepared for several issues changing your system to ubuntu (I wouldn't consider this an upgrade) as these two distros are not in sync. Why not just install warty from a floppy boot instead of woody?

---

### Post by karistouf on 2005-05-05
thanks, because I m coming from there:

no USB booting
cdrom on usb port
only floppy
no internet access ( all the times being in move with it and of course around they are windows PC... so it is not quite easy to configure ethernet card and to pass thruth a windows network access the internet...)

I will try it now.... and give you answers back/ \\:D/

---

### Post by karistouf on 2005-05-05
nad... :???:   it didn t work. i m suspecting experimental kernel fb2.4 to be in part responsible of it.
but it is good to know this command, thought there is no effect.

but you just said there was floppies. in the ubuntu wart i have no images permit thruth floppy to boot from usb cdrom.

if there is a link, yes i want !

so that s why i followed to first install woody and its base under fb2.4, and so on...

experienced help will be great.

christoph :roll:

---

