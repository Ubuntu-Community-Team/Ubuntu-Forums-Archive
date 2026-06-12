---
title: "Windows on vm inside Ubuntu?"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by jeliocranch on 2011-04-10
Hi y'all.
I've been dual booting win 7 and Ubuntu since Jaunty, but growing tired of restarting everytime I need to do something in Windows.  I think the best solution would be to run Windows on a vm, making Ubuntu the primary OS.  There doesn't seem to be too many people doing that, though: most set up their machines the other way.
Does anyone here have experience running Windows on a vm inside Ubuntu?
Any input would be appreciated...
Thanks in advance.

---

### Post by carl4926 on 2011-04-10
In Virtual Box, it will work just fine. Plenty folks do it

---

### Post by Ray Mac on 2011-04-10
I've run XP for a number of years inside of *nix. The two easiest to use are VirtualBox and any of the VMWare  products. 

  The first thing you need to know is if you have the proper Windows license. Check Microsoft for that info.

  Now you need to decide between VirtualBox and VMWare. VirtualBox has snapshot support built into the free product. Last time I checked VMWare, it was only on the paid version. Snapshots allow you to check out new software without having to reload if it goes bad.

  How important is usb support to you?  VirtualBox has one version that supports usb and one that doesn't. I've had nothing but problems with it. VMWare's usb support is excellent.

  I can live without the usb, so VirtualBox is my choice. It also seems to run faster than VMWare.

---

### Post by Old_Grey_Wolf on 2011-04-10
I run Windows Vista and 7 in Virtualbox on an Ubuntu host.

Download Virtualbox from the Oracle website. Also get the Extension Pack. The Extension Pack adds USB 2.0 device support among other things.

Remember you are running two OSes at the same time; therefore, you need enough RAM for both OSes in order for them to run smoothly.

Edit: You may want to download a pdf of the User Manual from their website.

---

### Post by Old_Grey_Wolf on 2011-04-10
Another thing I would suggest would be to monitor your CPU temperature the first few times you use Virtualization. I use conky for that purpose. The first time I ran Windows Vista as a VM on my laptop, that doesn't have a cooling system designed to handle both cores running at 80% continuously, it got to about 76 degrees Celsius while Vista booted and several minutes afterward. It eventually cooled down to 50 degrees Celsius which is still 10 degrees hotter than normal.

My desktops have faster CPUs, dedicated graphics cards, and better cooling systems. I didn't see very much of a change in the CPU temperature on them. They are capable of being gaming machines.

I don't know what you are using to run the VMs; therefore, just a suggestion.

---

### Post by jeliocranch on 2011-04-10
Thanks guys.  I had been reading a bit on kvm, but finally typed the magic search words into google and found some tutorials on virtual box.  Great info on downloading the extension file for the usb.  Definitely need that.

One reason for me wanting to do things this way (aside from the fact I can do *almost* everything I need to do in Linux, and like it better) is to try a softraid setup.  Unless its fakeraid or hardraid, win7pro doesn't like living that way.  Of course ubuntu is fine and I've heard good things about the software raid built in.  Any experience in this arena?  any forseeable issues with virtual box?

---

