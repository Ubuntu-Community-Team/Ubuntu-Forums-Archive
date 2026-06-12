---
title: "Can't get Xubuntu to install with a GUI"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2010-01-17
I'm trying to put Xubuntu 9.10 on an old notebook that I know can run at least XFCE, because I had an older Xubuntu version on it once, with GUI and everything.

No matter what I do, I can't get Xubuntu 9.10 to install so that I have a GUI.  I can't do anything with a command-line-only install, but that's all I get.

I'm installing Xubuntu over my LAN because the notebook's CDROM drive no longer works, and it can't boot from a USB device.  I keep trying to use the regular Xubuntu Desktop CD, but it won't work.  When I use the Alternate Install CD, it works, but I don't get a GUI.

How do I fix this?  

(Downloading everything over the Internet is not an option.  Takes WAY too long.)

---

### Post by mikewhatever on 2010-01-18
Just to clarify, did you install the full desktop or just the cli system? Could it be that you simply needed to login and install the GUI, or is it already installed and simply doesn't load?

---

### Post by snowpine on 2010-01-18
Try this:

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
startx
```

---

### Post by Objekt on 2010-01-18
To clarify, well, I THOUGHT I did a full desktop install.  However, maybe that is where I'm going wrong.

I'll have to skip some intermediate steps here so this post isn't 8 pages long.  Please ask if anything's unclear.  Cutting to the details:

I hosted the Xubuntu 9.10 install CD on my server by mounting the .iso file to /var/www/ubuntu and running Apache.  I booted the client laptop in PXE mode, using a tftp service to feed it the netboot files (obtained from the netboot.tar.gz package for Ubuntu Karmic).

When it came time to designate a mirror for Ubuntu install files, I pointed the installer to the IP address of my server.  

For some reason, the install would not proceed further if I tried to use the Xubuntu Desktop CD image (xubuntu-9.10-desktop-i386.iso).  It would only work if I used the "Alternate" CD image (xubuntu-9.10-alternate-i386.iso).

So, I completed the install using the Xubuntu 9.10 Alternate CD image.

Is that perhaps the reason I get no GUI?

---

### Post by Objekt on 2010-01-18
I finally got a GUI.  It was pretty convoluted, and I'm thinking there has GOT to be an easier way, but it worked.

The first problem was that any time I did an "apt-get" or anything else involving the repositories, it tried to get stuff from the CD image hosted on my local server.  So I had to manually edit /etc/apt/sources.list with nano, replacing each instance of "http://serverIP/ubuntu..." so that it pointed to us.archive.ubuntu.com.

Somehow I managed to do all umpteen replacements without making a typo.

Next, I ran the command
```
sudo apt-get install xubuntu-desktop
```

A whopping 1.4 GB download later, I had all the stuff in place.  Then I did a
```
sudo apt-get update
```

to wrap up any loose ends, entered a "startx" command, and kept my fingers crossed.

Eventually I got the XFCE4 desktop.  For some reason, the NetworkManager applet didn't want to use the NIC.  It said "device not managed."  Which is weird, because I was obviously able to use the network earlier, and I've never had problems with the DHCP on my router before.  

I tried manually setting the NIC's MAC and manually entering an IP address to get network access.  It worked, but the NetworkManager icon on the panel still has the red "disconnected" symbol on it.  I know I'm on the network because I can install apps, browse the Web, etc.  Weird.

---

### Post by mikewhatever on 2010-01-19
> **Objekt said:**
> .........

I tried manually setting the NIC's MAC and manually entering an IP address to get network access.  It worked, but the NetworkManager icon on the panel still has the red "disconnected" symbol on it.  I know I'm on the network because I can install apps, browse the Web, etc.  Weird.

You may need to edit /etc/network/interfaces and comment out or delete all redundant lines but the following:

```
auto lo
iface lo inet loopback
```

The network manager should work after a reboot.
What I don't understand is why couldn't xubuntu-desktop be installed from the image file on the server.

---

### Post by Objekt on 2010-01-19
I don't know that either.  I assumed the Xubuntu desktop would be present on the Alternate CD as well as the Desktop CD.  

I noticed a different problem this morning.  Using either LXDE or the XFCE desktop, sometimes when I wake the machine up from screensaver, the mouse pointer is doubled.  Not only doubled, but it distorts the screen wherever I move it.  Pretty soon, the GUI is nearly unusable because there's so much garbage graphics on the screen.  I have to restart the machine to fix it; merely logging out and back in doesn't work.  I'll try to get a screenshot later.  

The Presario 710 has a very old graphics chipset, an S3 Twister-K.  Much to my surprise, I've found references via Google to a Linux driver for this device.  If Xubuntu hasn't installed it already, I might try using that.

It's possible the graphical oddities noted above are a symptom of failing hardware.

---

