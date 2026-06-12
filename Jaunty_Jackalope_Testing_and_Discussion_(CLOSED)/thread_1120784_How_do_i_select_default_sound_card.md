---
title: "How do i select default sound card?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Andreas1 on 2009-04-09
I tried to keep the title as simple as it is: I installed the 9.04 beta on a laptop with an internal (broken) sound card and an external usb sound card. By default i hear nothing.

Now i do know how to get a sound of this box, but i will pretend for a moment that i haven't already figured that out, since it's not obvious. I am considering making a bug report, because the default behavior of the whole sound configuring thing is not very "ubuntu" at the moment if you have more than one sound card.

So here's what i did so far: Install pavucontrol, go to the Output Devices tab and set my USB device as default. the devices in gnome-sound-properties all set to Pulseaudio Sound Server. Is that the way to go?

Because here's what i would do if i didn't already know better: Open gnome-sound-properties, find an abundance of ALSA and OSS devices, be confused. If pulseaudio handles everything, why isn't there a GUI for choosing the default Pulseaudio output?

It seems to me that pavucontrol is the right place to choose my output device, not gnome-sound-properties. but it's not installed by default, thus the gnome-sound-properties are quite confusing.


I would like to hear your thoughts on this, especially if you have several sound cards. Should i make a bug report?

---

### Post by markbuntu on 2009-04-09
This has been going on since hardy and has caused nothing but grief for hundreds of thousands of people. There have been hundreds of bug reports filed and wishlist requests and brainstorm requests but they all seem to fall on deaf ears. It has become a bad joke. 

From what I understand someone at ubuntu does not like pavucontrol gui so they just left it out of the desktop seed and offered no replacement. They should have just left pulseaudio out completely since the way they went about it created nothing but confusion and hard feelings about pulse and continues to do so today.

It took me weeks to get my two sound cards and usb devices working properly on Ubuntu. There were no such problems with Mandriva or Fedora but of course, pavucontrol and other necessary packages came already installed on those distros.

Gnome is working on a new control that is a replacement for pavucontrol but it is still missing a lot of pavucontrol's functionality. Maybe by Koala this will all get straightened out. 

KDE is also adding more functionality to phonon but I am not sure they are looking to replace pavucontrol since pulse is nicely complementary with phonon in KDE4.2 already

But anyway, to answer your question. If you are using pulseaudio then pavucontrol is where you control multiple hardware devices. Alsa cannot do it without hand editing of /etc/modprobe.d/alsa-base to set the order of the hw devices since hw designations can and often do change on every boot due to semi-random pci detection. So, with alsa if you have more than one sound card default hw0 can become hw1 on next reboot and all your sound will be directed to the wrong default. Pulseaudio does not have this problem since hal reports devices by name.

---

### Post by Andreas1 on 2009-04-17
For those interested, this would be the corresponding [bug report]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229137")

---

