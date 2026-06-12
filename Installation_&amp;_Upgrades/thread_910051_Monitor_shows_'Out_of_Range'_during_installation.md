---
title: "Monitor shows 'Out of Range' during installation"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by Alex53 on 2008-09-04
I am trying to install Ubuntu 8.04 LTS (Desktop) on an IBM xSeries 335.

During installation the monitor switches off and displays a message 'Out of Range'. I tried using the 'Safe Graphics' option to install but the same problem occurs.

I have searched the forum but the other threads referred to the problem once Ubuntu has been installed, so there are other things the user can do in those cases.

Any help would be welcome!

---

### Post by Partyboi2 on 2008-09-04
Try adding vga=791 as a boot option. At the main menu press F6 and at the end of the line add vga=791
you may need to change 791 to a more suitable one that your monitor can handle.
See [[COLOR=Blue]here[/COLOR]]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers") 
Or
try  installing using the alternate cd which is text base installer
[http://releases.ubuntu.com/8.04.1/](http://releases.ubuntu.com/8.04.1/)

---

### Post by Alex53 on 2008-09-04
Thanks for your prompt reply.

Adding vga=791 did nothing, neither did the number for 640x480, 256 colours, which the monitor can obviously display.

I am downloading the alternate iso now.

---

### Post by Alex53 on 2008-09-05
I installed using the alternate CD, which as you said has a text based installer, so everything went well.

However the problem is still there when trying to boot up after installation. 

What is so unusual about this resolution that its out of range for a monitor that can do anywhere between 640 to 1280 on the long side? 

What can I do to sort it out? Thanks.

---

### Post by Partyboi2 on 2008-09-05
What make and model is your monitor? Do you know what the 'HorizSync' and 'VertRefresh' are for it?

---

### Post by Crafty Kisses on 2008-09-05
Try changing your refresh rate, that sounds like the issue.

---

### Post by Alex53 on 2008-09-05
Thanks for your replies. 

I'll be honest, I downloaded Fedora Core 9 and installed it without problems. Now I am working on sorting a whole set of other problems configuring http/mysql/ftp, etc. :) 

Every time I have needed a Linux server its felt like climbing a mountain to install/configure it, and a breeze to run it. While windows is a breeze to install and configure and like climbing a mountain to run daily.

---

### Post by masam on 2008-09-05
hehe, which begs the question, which would you rather spend more time on...installing and making it rock solid...or working on it and making it a rock slide?!?!...;)

---

### Post by Alex53 on 2008-09-07
Agreed, I prefer Linux servers for obvious reasons, but;

1. Within Linux, my limited experience with Ubuntu tells me I want to stay with Fedora.

2. Sometimes you cant fight your boss and go your own Linux way. Currently Linux has no single client/server that will cover e-mail, contacts, tasks and calendar like Exchange/Outlook does, so that pushes us to Exchange servers, and with them Active Directory and AD integrated DNS servers, and therefore a windows domain environment. So I pretty much lose the battle and end up with just web and ftp servers being my only Linux servers :(

Of course, my fun is I do get to tell my boss that the intranet server has been up without downtime for 480 days, and the windows servers are lucky if they last a couple of weeks :)

---

