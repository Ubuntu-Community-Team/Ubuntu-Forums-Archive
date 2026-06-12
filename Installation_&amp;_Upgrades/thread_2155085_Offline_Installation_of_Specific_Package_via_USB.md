---
title: "Offline Installation of Specific Package via USB"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by undrline on 2013-06-17
I installed XUbuntu off a bootable usb created via UNetbootin and a pre-downloaded 12.04.2x86 32bit iso.  I have an external wireless card via usb that needs this package in order to work:
[http://packages.ubuntu.com/lucid-updates/firmware-addon-dell](http://packages.ubuntu.com/lucid-updates/firmware-addon-dell)

At first I tried to File>Add via Synaptic [firmware-addon-dell_2.1.0.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/f/firmware-addon-dell/firmware-addon-dell_2.1.0.orig.tar.gz").  Then I tried copying that and the same, decompressed, to /var/apt/cache/ or whatever it is ... I just couldn't get the package to show up in Synaptic.  Yes, I've read the documentation about offline installation, yes, I've looked at AptOnCD.  Keryx seemed like a good option to get these downloaded from an internet-capable windows machine, but it just kept giving me path errors no matter what iteration I put in the preferences.

I just need this package and dependencies to get the external wireless card working, then I can do all the updates I need to.  And, I'm looking for a solution that's faster than just carrying the whole desktop and peripherals over to the router and back again.

---

### Post by steeldriver on 2013-06-17
It looks like you downloaded the source tarball - you won't be able to install that directly, that's for compiling on your local system - try downloading the actual .deb file from one of the mirrors here --> [http://packages.ubuntu.com/precise/all/firmware-addon-dell/download](http://packages.ubuntu.com/precise/all/firmware-addon-dell/download) 

However by the time you've chased down all the dependencies (particularly those for the BIOS tools) I would think it will likely be quicker to find a working wired connection - personally I'd only resort to sneakernetting debs via a USB if I had absolutely NO network connectivity

---

### Post by Cheesemill on 2013-06-17
Are you sure that that is even the correct package?

That download link is for a package meant for 10.04, but you say you are using 12.04.

---

### Post by steeldriver on 2013-06-17
oops yes thanks Cheesemill - edited my link accordingly (note to self: don't post before coffee)

---

### Post by undrline on 2013-06-18
Glad to see it's in the current packages (was worried ... this installation is the result of a failed upgrade from lucid to penguin).  Based on what you're saying, I guess that's only the first level of dependencies, and they would each have their own, etc.  I went ahead and physically moved the machine.  Thanks for the responses.

---

