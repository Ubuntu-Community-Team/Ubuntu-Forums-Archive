---
title: "Changing Kernel and it's impact on NDISWRAPPER"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by caiphn on 2005-02-22
I tried to change to the K7 Kernel as it is specifically for AMD/Athlon chips from what I read. However, after doing so I see that a bunch of errors occur (much to fast during startup for me to make note of them) so I had to boot back into the previous Kernel in order to access the Internet. Under the K7 Kernel I checked to see if the Kernel Headers for K7 were installed, they were not so I marked them in Synaptic, however it wasn't able to download them.

1. In order to get NDISWrapper to work with the K7 Kernel  is it necessary to install the Kernel Headers and Restricted Modules, then re # make install ndiswrapper?

2. It won't let me install the Kernel Headers for K7, is that because I don't have a connection to the Internet?

3. Now I have three different Kernel login options, yet I only did the instructions for the K7. Why is that? (I have a -3 AND a -5 now)

 Sorry if this is a dumb question, I try to figure things out on my own.

---

### Post by caiphn on 2005-02-23
Well, as no one has responded to this, I guess I just won't worry about it. However, is there a way in Grub so it doesn't show the two newer Kernels, just the old Kernel? It looked cleaner when I could just choose between Ubuntu and Windows.

Man.. linux is a bit of a learning curve for someone who has been using Windows for the last 10-12 years or so :p

Again sorry, I'm doing all the reading I can, trying to figure out bash right now/figure out how to install programs, not having much luck with that, but one thing at a time right.

Thanks in advance

---

### Post by jsgotangco on 2005-02-23
well just remove the kernels you don't use via synaptic or apt and grub will clean itself

---

### Post by caiphn on 2005-02-23
Ok, I'll just figure out what directory they're in and remove them then? Is there a GUI equivalent file management program in Ubuntu?
-edit-

Ok, I got it working with a newer version, but then I had to 'make install' again in the ndiswrapper directory. Everytime you go to a new kernel, do you have to reinstall everything for it to work?

-edit-

Anyone?

---

### Post by CamB on 2005-08-10
Dragging this thread up out of the past...

I have the same problem - I have upgraded the kernel to K7 and now ndiswrapper has stopped working with a USB wireless adaptor using a driver PRISMA02.sys.

It still works if I boot into the 386 kernel. 

When I make install as the guy above suggests, it reinstalls ndiswrapper fine, however it suggests I should reinstall the windows drivers as they have changed from version something to version something else (sorry for vagueness - its from memory).

I have removed the ndiswrapper drivers and reinstalled them. When I modprobe ndiswrapper, it returns an error message in the log:

"windows driver couldn't initialize the device"

ndiswrapper -l still indicates the driver and hardware are there and ok.

---

### Post by CamB on 2005-08-15
I needed to set the kernel to boot with mem=900mb - ndiswrapper does not currently support highmem (I have 1gb) and USB devices.

---

