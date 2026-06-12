---
title: "ubuntu &amp; kubuntu Problems please help."
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by fulio on 2007-08-06
Hi, im pretty new at this guys, ive downloaded the iso of the website i got ubuntu and kubuntu. and here is my problem.

I'm experiencing a problem when my ubuntu & Kubuntu when system boots up. it will run through the boot sequence fine, and after it finish loading it will go to a black screen and it will stay ther for ever. i would have to force a shutdown. and i "Check cd for defects" and no errors at all. i also tryd runnung in safe mode same thing happens. im running a hp pavilion dv6000 with a Nvidia geforce 6150 w/ 120gig and 100 ram i think i cant remember.

---

### Post by ifeldt on 2007-08-08
I am going to assume that the Live CD works fine and you are talking about an installed version of K/Ubuntu.

If this is the case, when the system displays the black screen, press ctrl-alt-F1 and you should get to a login prompt.

Login with your username and password,

Run this command

```
cat /etc/X11/xorg.conf
```

If there  is some way you can post the contents of that file I think we can help you.

If your internet connection works you can do this

```
sudo apt-get install links2
links2
```

When prompted for a password, put in your normal user one.

This will give you a little command line web browser you can use to post the file to this thread.

Pressing alt-right arrow and alt-left arrow will get you to other terminals.

Good luck.

---

### Post by fulio on 2007-08-09
im not able to get to the login prompt. i tryd everyrthing it just freezes on me..

---

