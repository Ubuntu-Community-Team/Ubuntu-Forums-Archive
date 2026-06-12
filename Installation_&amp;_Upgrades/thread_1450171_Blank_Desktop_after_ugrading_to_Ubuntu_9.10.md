---
title: "Blank Desktop after ugrading to Ubuntu 9.10"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by doublegazing on 2010-04-08
Blank Desktop after ugrading to Ubuntu 9.10

I'm a bit of a novice and a bit lost after I upgraded to ubuntu 9.10 as my desktop is blank (no background picture and no icons - all I see are the upper and lower taskbars and their icons).

My PC is a Sony VAIO with 2GB RAM and a Radeon 9200 PCI Videocard with a 19" widescreen 1440x900 resolution monitor.

I typed the following into the terminal to get the display details and got the information below.

PLEASE would some kind soul tell me if I need to enter new code into the terminal (and what to enter) or whatever to resolve matters.

Much appreciated.

Into the terminal I typed:
sudo lshw -class display

And got:
description: VGA compatible controller
       product: RV280 [Radeon 9200]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:e0000000-efffffff(prefetchable) ioport:9800(size=256) memory:fe8f0000-fe8fffff memory:fe8c0000-fe8dffff(prefetchable)

---

### Post by emanuel.b on 2010-04-08
Hi!

To tell you the truth, you have me a little confused. Have you tried to right click on the desktop, to create a folder, or change the desktop background?

---

### Post by Greg Xix on 2010-04-08
Go to Start > Accessories > Terminal


At the prompt type: gconf-editor

[I]user@user-desktop:~$ gconf-editor
[/I]
Then expand Apps, expand Nautilus, then open Desktop


In there you should see checkboxes for your traditional icons, like Computer, Home and Trash


The Gconf-Editor is the rough equivalent of Windows Registry. So be careful when using it!!

---

### Post by doublegazing on 2010-04-09
> **emanuel.b said:**
> Hi!

To tell you the truth, you have me a little confused. Have you tried to right click on the desktop, to create a folder, or change the desktop background?
Hi,

It's a bit of a mystery seemingly to do with normal desktop display only...

The folders and icons are there on the desktop alright you just can't see them! If however I open up the desktop as a separate file-browser window via the 'Places' icon on the upper taskbar I can see all the folders/icons that are meant to be showing on the desktop and can access them fine.

I've also tried rightclicking the desktop and changing background pictures. The pictures are changing ok as you see the desktop picture (but not the folders & icons present) in a very brief flash when you shut down. I've tried restarting and that doesn't help.

Here's an even bigger mystery: you can even put the mouse pointer over the blank desktop and click on where you think a folder or icon might be and, if you are lucky with this random shot in the dark, the thing will open! They are there alright you just can't see them on the normal desktop and so have to access them via > Places (menu) > Desktop (Desktop - File Browser).

Like I said, a bit of a mystery - to me at least!

Any clues will be greatly appreciated. Thanks.

---

### Post by bplzip on 2010-04-09
I had the same problem after installing 9.10. Changing the screen resolution to 1024x768 fixed it for me.

---

### Post by doublegazing on 2010-04-09
> **Greg Xix said:**
> Go to Start > Accessories > Terminal


At the prompt type: gconf-editor

[I]user@user-desktop:~$ gconf-editor
[/I]
Then expand Apps, expand Nautilus, then open Desktop


In there you should see checkboxes for your traditional icons, like Computer, Home and Trash


The Gconf-Editor is the rough equivalent of Windows Registry. So be careful when using it!!
Thanks, 

I tried this but it didn't work.

---

### Post by doublegazing on 2010-04-09
> **bplzip said:**
> I had the same problem after installing 9.10. Changing the screen resolution to 1024x768 fixed it for me.
thanks,

this gets the desktop working/visible but it looks horrendous! At least I know know that, for some reason, my system does not want to display 1440x900 resolution. I don't know why - as it is what the label on the front of my monitor says the resolution should be and it works fine if I run XP or the previous version of Ubuntu.  ...so its gotta be a problem with Ubuntu 9.10 itself not being compatible with my monitor or Radion 9200 display card right?

---

### Post by emanuel.b on 2010-04-09
> **doublegazing said:**
> thanks,

this gets the desktop working/visible but it looks horrendous! At least I know know that, for some reason, my system does not want to display 1440x900 resolution. I don't know why - as it is what the label on the front of my monitor says the resolution should be and it works fine if I run XP or the previous version of Ubuntu.  ...so its gotta be a problem with Ubuntu 9.10 itself not being compatible with my monitor or Radion 9200 display card right?
Could be, but I'd wait for Ubuntu 10.04 to make sure that it's just a problem 9.10...

---

### Post by beta.tester on 2010-04-09
> **doublegazing said:**
> thanks,

this gets the desktop working/visible but it looks horrendous! At least I know know that, for some reason, my system does not want to display 1440x900 resolution. I don't know why - as it is what the label on the front of my monitor says the resolution should be and it works fine if I run XP or the previous version of Ubuntu.  ...so its gotta be a problem with Ubuntu 9.10 itself not being compatible with my monitor or Radion 9200 display card right?

Hi

This sounds very similar to what a friend of mine had with his i3 processor laptop.

Justa  thought! Could you not try the **live cd** version of 10.04 beta 2? (It has the kernel and video drivers that allowed him to use his laptop in all its glorious intended display :)

Please let me know how you get on, kind regards    john

---

