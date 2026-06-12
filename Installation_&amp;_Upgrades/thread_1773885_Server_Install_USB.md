---
title: "Server Install USB"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by kwagger on 2011-06-02
Hi there,

My first post, and I hope my problem is not too clueless - I did try search but to no avail.

I have an HP microserver that I would like to install ubuntu server on.

1x250gb + 2x2tb drives installed. Id like the 250gb partitioned and formatted as the os disk.

Ive tried downloading the 11.04 natty build - this gets stuck cant mount onto cd drive.
Next tried the network installer - (both installed onto a 16gig sandisk cruzer blade using YUMI, universal usb loader and unetbootin) and cannot get it to install.

At the moment, its got further - through most of the net install, but stalled at installing the grub boot loader.

seems like the installer is trying to install bootloader to the usbdisk dev/sda and it should be dev/sdb - the 250gigger.
Its sat with a busybox console up - any clues what I need to do to get the thing to install bootloader onto the hdd?

Ive pulled a lot of hair out and not got anywhere. Any help would be gratefully received.

(p.s. Im ok with dos command line, but am a total noob with linux, so clearly and loudly please !!)

Thanks a bunch in advance.

Kwag

---

### Post by gordintoronto on 2011-06-02
"Ive tried downloading the 11.04 natty build - this gets stuck cant mount onto cd drive."

What does that mean? I don't understand "gets stuck," or "can't mount onto CD drive." Do you understand the meaning of "burn the image" as opposed to saving as a data file?

There is a little overhead to using a GUI, but most servers will never notice it. Everything is a lot easier if you use Ubuntu instead of Ubuntu Server, which has no GUI.

What kind of server do you want to run? Web, file, streaming video, etc?

---

### Post by kwagger on 2011-06-03
> **gordintoronto said:**
> "Ive tried downloading the 11.04 natty build - this gets stuck cant mount onto cd drive."
 
What does that mean? I don't understand "gets stuck," or "can't mount onto CD drive." Do you understand the meaning of "burn the image" as opposed to saving as a data file?
 
There is a little overhead to using a GUI, but most servers will never notice it. Everything is a lot easier if you use Ubuntu instead of Ubuntu Server, which has no GUI.
 
What kind of server do you want to run? Web, file, streaming video, etc?
 
Hi there and thanks for the reply. What I meant was that I was attempting to install from a usb stick, but the install process failed pretty early on, and the error generated related to being unable to mount a CD drive. 
 
I could have been far clearer with that though! 
 
I have installed the desktop version of 11.04 now and that all went fine, and as you say i think i'll be more comfortable with the gui.
 
I would like to provide network document storage and sharing, store video content and provide video streaming to the machines in my home network. (windows pc, netbook, popcornhour, ipad). Wish list would be for the machine to handle usenet downloads as well - that would be handy.
 
Can anyone recommend any additional packages that I will need to install over the basic ubuntu desktop to facillitate this?
 
Thanks again for your help. 
 
Kwag

---

### Post by gordintoronto on 2011-06-03
> **kwagger said:**
> I would like to provide network document storage and sharing, store video content and provide video streaming to the machines in my home network. (windows pc, netbook, popcornhour, ipad). Wish list would be for the machine to handle usenet downloads as well - that would be handy.
 
Can anyone recommend any additional packages that I will need to install over the basic ubuntu desktop to facillitate this?
 
Thanks again for your help. 
 
Kwag

If you right-click on a folder and select "sharing options," you might be prompted to install Samba. I find it works very nicely for file sharing. If you simply play a video from a shared folder, that isn't actual "video streaming." If you want to do more than that, I suggest Googling: streaming linux

It has been a long time since I tried to do anything with Usenet, because Usenet servers are rare in North America.

---

