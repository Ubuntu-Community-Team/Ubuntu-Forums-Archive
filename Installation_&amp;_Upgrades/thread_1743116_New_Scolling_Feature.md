---
title: "New Scolling Feature"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by oceanfirehawk on 2011-04-29
Hi everyone,

I hate the new scrolling feature in 11.04 where the scroll bar is hidden until you roll the mouse over it. How do I revert this to the regular scroll bar?

---

### Post by loolooyyyy on 2011-07-22
this is the way:

> sudo su
echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars

and then restart,
remember "sudo echo ....." wont works, use "sudo su" and then the "echo" command

if it didnt work, remove this packages:
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0

source: [www.webupd8.org]("www.webupd8.org")

---

### Post by sikander3786 on 2011-07-22
Here is a better method in which the user doesn't need to login as super user that is by running the 'su' command. Running the 'su' commands doesn't return you to the normal user unless you type 'exit' or close the Terminal. And not to mention that when you are in the 'su' mode, you can probably do anything silly, accidentally ;)

[http://ubuntu4beginners.blogspot.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html)

---

### Post by Luke M on 2011-07-22
Wonderful! Thank you.

---

