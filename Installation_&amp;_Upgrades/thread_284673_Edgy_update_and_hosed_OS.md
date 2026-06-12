---
title: "Edgy update and hosed OS"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by faceoftheearth on 2006-10-25
I apologize if this is the wrong forum. I noticed a few other people in this one were mentioning problems regarding an Edgy upgrade screw up. I upgraded and it killed my window manager as well as my ability to connect to the internet. I had to boot back into trusty Windows so I could see what my recourse was. I have cleaned all my important files out using the EXT2 driver for Windows but I'd still prefer not to just format and reinstall. My two major problems are with the window manager not existing and with network manager not working. In Dapper I used nm-applet to manager my wifi and it did a fairly decent job. With Edgy the computer is back to not supporting WPA2 etc.. Can I get nm-applet back? If not, can I get my ipw2915 working with WPA2/WEP? As for the window manager I'd be alright to just set it to whatever the default is, since compiz/xgl doesn't seem to be supported for Edgy. 

Thanks in advance

---

### Post by H.E. Pennypacker on 2006-10-26
You should probably worry about your window manager before getting started on Network Manager.  Let's get started by describing exactly what's going on.

You start up the system, and at what point do you realize that something's wrong?  What exactly do you see?  When logging in, does it show that the window manager is being loaded?

I don't use Edgy, but I am sure the default window manager is Metacity (don't see why it would have been changed).  Start up Metacity through a terminal.  What happens?  Either type in "metacity" at a line or "metacity --replace".  I kept the period out of the quote to not confuse you.

Notice anything at this point?  Any error messages?  Is Metacity installed at all?  If not, install it, but it should be installed already. 

Let's talk specifics when describing anything.  When you're done with the window manager, it's probably worth dealing with network manager, not the other way around.

When upgrading to another version, some programs become incompatible, and this could be true for Network Manager.  If it's not installed, just install it once again.  Start up Synaptic, and download it.  If you don't want to use Synaptic, go to Gnome-files.org (or maybe its gnomefiles.org), and download it from there.

---

### Post by faceoftheearth on 2006-10-26
The problem is noticeable after logging in. Essentially none of the windows have the requisite buttons and title bar. I'm not 100% sure that's the window manager, but I think I recall that being the case from when I installed Compiz. As for network manager it gives a specific error about missing a certain library. I'll try metacity -- replace. I had been trying GDM --replace but since I don't have any internet connection in Linux anymore I was mostly just toying around. 

Thanks

---

