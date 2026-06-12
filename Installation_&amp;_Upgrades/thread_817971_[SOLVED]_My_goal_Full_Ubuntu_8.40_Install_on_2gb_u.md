---
title: "[SOLVED] My goal: Full Ubuntu 8.40 Install on 2gb usb! PLEASE READ"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by swoody on 2008-06-04
Well here's my goal: I want to fully install Ubuntu 8.40 onto a 2gb usb flash drive. Before we start, yes I know there are other distros that are designed to be very minimalistic, and would fit easily onto a 2gb flash, but I've become comfortable with Ubuntu, and personally prefer it's appearance and feel. I know the recommended install disk size is 4gb, but I tried installing it onto my 2gb to see what would happen, and it got to 70% before the installer gave me the message that there was not enough room to continue, so I think this can be very possible if there's any way to remove a lot of the stuff I won't be using before installing. Does anyone know if it is possible to remove clutter before the install and/or how to? 

I am a very basic computer user, and only need a very few programs to get 99% of my work done. Here are the few capabilities I would need to have: 
-web browser
-wireless internet capability (laptop)
-Skype
-a very basic image editing software to crop, resize, and rotate pictures
-very basic media playing capabilities
-and obviously a full install with the ability to upgrade, install/delete programs, and save files to the USB drive

I don't need email programs, address books, word processing, games, or any other programs. Also, I think it would be impressive to have a 2gb install with the compiz fusion style enhancements, but that's the least of my worries unless there's enough room for it to fit.

So here it is, my challenge to all of you: help me figure out a way to make this work. I have the live CD, ISO image, and flash drive, you lend me your help and expertise to create a 2gb Ubuntu. 

Thank you all very much! ANY input will be greatly appreciated. :)

---

### Post by peakshysteria on 2008-06-04
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

2 GB seems somewhat small. But not too small :)

I guess you are looking for:

USB Ubuntu 8.04 Persistent install from Live CD

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by swoody on 2008-06-04
Well, I was checking out that site for more info, and I checked out the instructions there, but the only ones you can do with Hardy Heron for under 4gb is a "live cd" kind of thing, or a persistant install. To do the actual full install with upgrade capability it takes 4gb.

When I tried that Persistent install it didn't work out for me. Step 16 on your second link didn't work when I had tried it earlier, so I had to play around with it a bit to get it to work, but it still gave me an error message that it couldn't copy some of the files.

That's actually where i got the instructions on how to do a full install onto a usb drive, and that's when I had mentioned that the install got to 70% when I tried it out.

---

### Post by peakshysteria on 2008-06-04
Hmm, sorry man. Read trough your post a bit fast. And read the howto a bit fast. [4 GBs]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") it is yes. I'm really looking for the same thing as you. But haven't read to much about it yet. But it should be doable for sure.

The ''go into the BIOS to change boot device''-thing kinda turns me of. Isn't it just enough to boot the machine with the stick and it will automatically recognize it??

For the time being I use open office, VLC, Mplayer, Pidgin, 7zip and Firefox from [http://portableapps.com/](http://portableapps.com/) on my 8 GB USB stick. All working smooth without any issues. But I would really like to have a running Ubuntu instead. It might be right around the corner: [http://portableapps.com/apps/operating_systems](http://portableapps.com/apps/operating_systems)

---

### Post by swoody on 2008-06-04
deleted to clean up topic

---

### Post by peakshysteria on 2008-06-04
> **smwoodruff0908 said:**
> All you do through BIOS is change the order of things your computer looks at to boot from. Your BIOS has a full list of things (HD, USB, CDROM, network adapter, etc.) that it looks at, and the first operating system it comes across it'll start. You're not changing anything else besides what order your computer looks at the different areas. So you need to list the items so your USB is higher than any other OS's you have on your comp. If you don't have your usb plugged into your comp it won't find the operating system there, so it'll just continue down the list (basically just booting like normal). So there's really nothing to be afraid of tweaking or damaging by doing this, and you don't have to worry about slowing down start times either since it looks through these areas very very quickly :)

The point is at work I use different computers with limited access. I can't go into the BIOS because I have no access. Meaning this limits the usability for me. And thats why I at the time use standalone apps from portable apps. It's working surprisingly good actually. Though a working bootable (without going into the computers BIOS) Ubuntu Hardy Heron would be close to cutting edge kick ***....

Have you tried Wubi? [http://wubi-installer.org/](http://wubi-installer.org/) eh....forgott about the size again. Sorry man. But this also seems to be a good alternative if you got room for it :)

---

### Post by swoody on 2008-06-04
> **peakshysteria said:**
> Have you tried Wubi?

Yeah, it came with the 8.40 Ubuntu, and I checked it out a little bit, but I'm not super-worried about being able to load my ubuntu in Windows. Most of the computers I'd be booting up on would allow me to change the BIOS boot order, so I'm not that concerned with it, although if space allows it it would be a nice backup to have for the rare occasion I might have to boot from inside Windows.

---

### Post by peakshysteria on 2008-06-04
> **smwoodruff0908 said:**
>  it would be a nice backup to have for the rare occasion I might have to boot from inside Windows.

Haha...I've just this year wiped out all windows OSs in the house. Our three machines are all running Ubuntu now. But in work environment i guess I wont see a Ubuntu as OS in my time I'm sorry to say. So it would be nice to have a complete Ubuntu install on a stick. Let's hope someone with more first hand experience can tell us :)

---

### Post by unco on 2008-06-04
You might be looking for the 'Ubuntu Customization Kit' which allows you to remaster the LiveCd ... haven't tried it myself just readabout it once.

Check out:
[http://uck.sourceforge.net/]("http://uck.sourceforge.net/")
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")
[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd]("http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd")

---

### Post by swoody on 2008-06-04
Thanks unco! I'm checkin these out, I'll let you know if/how it works! 

In the meantime, if anyone else has any other suggestions, please let me know! Thanks

---

### Post by swoody on 2008-06-05
I'm having a bit of a hard time getting those guides to work, but since I don't have linux installed on my comp, and I'm working off the live cd, I think there might be some troubles with some of those steps. Does anyone know of any way to do that same kind of thing, but from inside Windows? or a   way, or any tips for me to try with the live cd?

---

### Post by swoody on 2008-07-03
Just wound up installing it on my 80gb HD. Plenty of room on there after getting rid of Vista :D

---

