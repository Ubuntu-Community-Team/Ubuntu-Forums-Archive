---
title: "Trouble on IdeaPad S12"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Ambush Commander on 2009-12-19
I'm having difficulty installing Ubuntu Netbook Remix on my new IdeaPad S12. I get the splash screen which prompts me to try/install, but after selecting that and waiting for the splash to finish, all I get is a blank screen with a blinking cursor.

I went and tried the USB key on another machine, and it worked like a charm.

What could possibly be special about my machine?

---

### Post by rjonnal on 2010-04-07
I have exactly the same problem. I'm going to try to borrow a USB DVD drive and do an optical media install instead.

-Ravi

---

### Post by Ambush Commander on 2010-04-07
For the record, I found a solution and documented it here: [http://www.thinkwiki.org/wiki/IdeaPad_S12](http://www.thinkwiki.org/wiki/IdeaPad_S12)

---

### Post by rjonnal on 2010-04-07
AC,

Thanks for the link. Your documentation is detailed and quite sensible. I'll try it out this evening.

-Ravih

---

### Post by rjonnal on 2010-04-07
AC,

I was able to do a full upgrade as your doc suggests, but then I wasn't quite clear on how to continue installing.

-Ravi

---

### Post by rjonnal on 2010-04-11
Ambush Commander,

I am trying to install Ubuntu Netbook Remix (URN) Karmic Koala (9.10) on a Lenovo Ideapad S12 with a Via Nano processor. I encountered the same problem you described in your initial post. I followed the instructions you posted here: [http://www.thinkwiki.org/wiki/IdeaPad_S12](http://www.thinkwiki.org/wiki/IdeaPad_S12).

First, a couple of comments:

1. The commands you describe must be issued as superuser, i.e. using 'sudo' at the beginning of each line. This is only noteworthy because it's counterintuitive that a superuser account even exists prior to installation. No password is required for 'sudo' commands when running the Live OS off the USB stick.

2. I used usb-creator-gtk to write the ISO image to a USB stick. In order to do the full upgrade you recommend, it is necessary when using usb-creator-gtk to increase the amount of space available to the live OS, from the default of 128 MB to at least 250 MB. I was using a 4GB stick, so I increased it to 1 GB. This may not impact other types of USB installation procedures, such as unetbootin or Windows methods.

3. I needed a wired ethernet connection in order to perform the steps you recommended. The wireless ethernet card did not work.

Now, my question: once the 'aptitude full-upgrade' command is executed, what's the next step? I'm left at the command prompt, and unsure of how to 'resume' the installation. The kernel upgrade effected by the commands you describe doesn't impact the kernel that boots off the USB, so you can't simply restart the machine and the same USB stick to install.

The question is somewhat academic now, as I tried the beta version of Lucid Lynx Netbook Remix (10.04) and it worked flawlessly. Still, I'm curious.

Thank you!

-Ravi

---

### Post by Ambush Commander on 2010-04-11
You should be able to CTRL+ALT+F7 to get back to the desktop.

---

