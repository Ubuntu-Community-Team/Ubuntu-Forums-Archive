---
title: "synaptic repositories from live usb"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by spectralblue on 2010-02-10
So I'm trying to get synaptic to recognize my live usb as a repository, but it doesn't seem to work. Tried apt-cdrom and it just unmounts the device. I know I can do it easily with a live cd, but I'm trying this on a netbook and don't have an ethernet cable available.

Anyone know how I can get synaptic to recognize my usb as a repository? Thanks in advance guys!

I love ubuntu!

EDIT: What i'm trying to do is active the broadcom sta driver, the live cd can do it easily, but once ubuntu is installed, I have to connect to an ethernet cable or a usb wifi to download the bcm resource from synaptic... any way I can do this offline by copying it from the usb or something?


EDIT: Found the solution myself. Just copied the bcmwl-kernel-source file from the Live CD to the apt cache. :D

Wasn't easy looking for the info myself for a noob haha

---

### Post by agentstewie on 2010-07-22
did you do this from the livecd?
btw helpful post.. up to a point haha. it seems like there still isnt a solution for this. it works for me in the liveusb but as soon as i install ubuntu i cant install any driver because i'm missing some package and i dont have any wired ports where i'm staying at

---

### Post by mlacons on 2010-12-17
Bump.

I'm having the same problem. I'm installing 10.10 Netbook from a usb drive (flash drive, thumb drive, usb stick) onto an HP Mini 210. The live desktop works fine but once installed the wireless broadcom sta drivers don't load properly. 

I know the repository is on the usb drive but can't get synaptic to read it. Reload request "please insert the disk labeled: Ubuntu-Netbook 10.10_Maverick Meerkat_-Release i386 (20101007) in drive /cdrom/"

I have tried mounting /dev/sdb1 into /cdrom That works fine. It seems synaptic umounts the usb device. I've cded into the /cdrom/pool so it couldn't unmount it but it just waited to time out and asked for the cdrom.

The Mini 210 has no wired network option and I don't own a usb cdrom. I might have to get one but there must be some way to get synaptec to recognize the data on the live usb install.

Thanks

---

### Post by subpar on 2010-12-18
So it's really easy. Took me a little time, but I was able to figure it out.

First thing, open up a terminal.

```
sudo gedit /etc/apt/sources.list
```

At the end of the file add this line:

[CODE]deb file:/media/[YOUR USB FOLDER] maverick main[/DCODE]

If you are not using maverick, replace that with whatever version you are using. After doing this, save the file and close gedit. You should be able to reload the sources in Synaptic or do apt-get update in the terminal and it will work.

---

### Post by mlacons on 2010-12-23
Thanks subpar for pointing me in the right direction.

edits need to be made in:
sudo gedit /etc/apt/sources.list
I needed to comment out the first deb statement. "deb cdrom....."

and insert deb file:/media/[YOUR USB FOLDER] maverick main restricted
it didn't  work without restricted on the end but problem solved.
Thanks!

---

### Post by mlacons on 2010-12-23
Just a note to fellow travelers. 

The above fix works great until you run apt-get upgrade. Something gets loaded and you'll have to remove and activate the additional drivers again. It will show the wireless as working but doesn't get a proper dhcp address from the router. 

I have copied the contents of the usb drive to a folder on root called /orig
sudo mkdir /orig
sudo cp -R /media/PENDRIVE  /orig (replace PENDRIVE with whatever your usb device is called)
sudo nano /etc/apt/sources.lst
add 
deb file:/orig maverick main restricted 
and save the file

Now in synaptic, under repositories, unclick all the options except file:/orig ....
hit the reload button
now active the additional drivers. It will only be able to pull from file:/orig ...
after a reboot, go back into synaptic, repositories and click all the repositories that are appropriate.

---

