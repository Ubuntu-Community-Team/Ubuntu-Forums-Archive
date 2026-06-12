---
title: "picasa"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by shepaug on 2012-09-11
Anybody install Picasa ? I just like it because the image cropper is a good one..unique..


OK. I am brand new to this from Windows. I never knew I did not have to think with Windows.

I am told to install Winetricks ??

ok..all is new here so I am totally DUMB.

Terminal ?

When asking for password it is normal I can not not see if I enter anything ?

Besides that I came to some screen about some Microsoft users agreement that I had to agree to. OK ? No option to say yes or no. Nothing clickable. Nothing by entering ENTER. or...


So that was the end of that try


NEXT   All I get is a bunch of stuff about some directory not usable.
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] [COLOR=#c20cb9]**wine**[/COLOR] winetricks


What am I asking ? Anybody install winetricks and some dumb instructions.

---

### Post by GeForce 9500GT on 2012-09-11
[Google dropped Linux support for Picasa]("http://www.omgubuntu.co.uk/2012/04/google-officially-drop-picasa-for-linux"). So best is to go for another image viewer/management/editor. 
 
But to give you some info, when you install Picasa for Linux, it automatically installs all needed Wine dependencies. The reason for this is that Picasa for Linux is not really a Linux application but a windows application using Wine to run on Linux systems.

---

### Post by shepaug on 2012-09-11
Now all I get is :::::::::::::::::


owner@ubuntu:~$ sudo apt-get install wine winetricks
[sudo] password for owner:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
owner@ubuntu:~$

A Link


 [http://www.ubuntututorials.com/install-picasa-ubuntu-12-04/](http://www.ubuntututorials.com/install-picasa-ubuntu-12-04/)

Picasa ? I searched long for an image cropper that was simple and easy and did the job well. It was with Picasa. I think that software Paint Shop Pro has the only thing I found similiar.


I just drove into this place and I am going nuts. Back to Windows !!  no..I am stubborn.

I have not used a RUN__________ in many years.

All I really want to do is surf the web and I think it is nice to do such minus Windows if possible.

---

### Post by GeForce 9500GT on 2012-09-11
Gimp can do a lot with images. Fine by me, be stubborn and close yourself for new experiences!

---

### Post by frncz on 2012-09-11
I am not going to be very helpful here, but I do use Picasa under ubuntu 12.04. Picasa runs fine, although the uploading to web albums does not work when I try to push from Picasa. I think it needs IE6 installed, which I did not manange to do. I am able to pull images from Google+ into my we albums.

Picasa has great features and is easy to use, and it is free. Gimp is great, but not so good for photo collections. Picasa's people recognition software is amazing, if a bit scarry.

---

### Post by oldfred on 2012-09-12
I download the current Windows version of Picasa and have not had any issues lately.

Often you cannot download from command line, if you also have synaptic or Software Center open at the same time as they have locked files.

&#65279;sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Configure Wine to set up directory,  Applications, Wine, Configure

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
wine picasa39-setup.exe

---

### Post by bvlenci on 2012-10-30
> **frncz said:**
> I am not going to be very helpful here, but I do use Picasa under ubuntu 12.04. Picasa runs fine, although the uploading to web albums does not work when I try to push from Picasa. I think it needs IE6 installed, which I did not manange to do. I am able to pull images from Google+ into my we albums.

Picasa has great features and is easy to use, and it is free. Gimp is great, but not so good for photo collections. Picasa's people recognition software is amazing, if a bit scarry.

I have also managed to install Picasa under Wine, but I have totally failed to install IE6, which apparently is needed to link to my Picasa web albums. It's mainly because of my web albums that I want to use Picasa, not Gimp.However, I did use Gimp for a while about five years ago, and didn't care for it.) 

I have followed the instructions on various site, all of which involve using winetricks and some options and prefixes that are never explained, so I'm just sort of typing commands as if they were some kind of amulet.

My latest effort was from 

[http://www.xjonquilx.net/2012/05/how-to-run-picasa-on-ubuntu-1204.html](http://www.xjonquilx.net/2012/05/how-to-run-picasa-on-ubuntu-1204.html)

$ env WINEARCH=win32 WINEPREFIX=~/.google/picasa/3.0/winetricks ie6
env: ie6: File o directory non esistente

(That means "file or directory doesn't exist".)

I liked this website, because she at least made some effort to explain what she was doing with each command, but the result was the same as the others. 

A previous attempt, found in a tutorial whose URL I've lost, was:

$ WINEARCH=win32 WINEPREFIX=~/ .wine sh winetricks -q ie6

This resulted in "command .wine not found".

I would really appreciate some suggestions, and would be delighted if they had a few footnotes. 

Thank you very much!

---

