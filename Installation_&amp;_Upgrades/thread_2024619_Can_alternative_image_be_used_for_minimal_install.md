---
title: "Can alternative image be used for minimal install?"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2012-07-13
Hello,

I need to install a minimal Ubuntu version for a set-top media box.

I downloaded the image for minimal Ubuntu. Although the installation works fine, it tries to download other needed packages on the fly. I need a setup where I could just keep all the packages on the same install CD.

Next I tried installing "server install" image on a clean system. However, the server install seems to run more processes than the minimal install.

The download page indicates an "alternative install" image. Is it the same as minimal install + all packages available on demand? 

Or, is there a better way where I can download all the packages and point minimal install to use these packages?

Thank you in advance for your help.

Regards,
Peter

---

### Post by cortman on 2012-07-13
Not sure I completely understand.
You want a minimal (CLI only) installation, but then want a package repository available on disk to install from as well?
Not sure how that would work. The [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD/") will give you a CLI only installation; but it's easy to set up your networking from there, and use apt-get to download other packages. I use the minimal CD myself for all my Ubuntu installations.

---

### Post by PeterTaps on 2012-07-15
Thank you for your help.

Your minimal install CD worked because you were always connected to the network. Try installing the CD without any network connection.

In my case, we have a very slow network connection. Also, we have keep installing minimal images many number of times in a day. Most of the time during install is being spent waiting for the install process to download required packages.

Hope this is clear.

Regards,
Peter

---

### Post by Cheesemill on 2012-07-15
Yes, you can use the Alternate CD.

When you get to the screen in the attached screenshot just hit F4 and select 'Install a command-line system'.

---

### Post by PeterTaps on 2012-07-16
Appreciate your help.

One clarification needed. Is installing the CLI from the alternate CD almost close to installing a minimal image? I know the CLI installation from the server CD runs more processes than required.

Regards,
Peter

> **Cheesemill said:**
> Yes, you can use the Alternate CD.

When you get to the screen in the attached screenshot just hit F4 and select 'Install a command-line system'.

---

### Post by dino99 on 2012-07-16
the "alternate" iso allows you to make a custom installation; so at each step you can select/deselect what you want/need.

---

### Post by Cheesemill on 2012-07-16
> Is installing the CLI from the alternate CD almost close to installing a minimal image?
Interesting question. I wasn't sure so I've just tried it out.

The alternate installation actually installs less packages than the mini installation (324 vs 371).

Take a look at the attached results of 'dpkg --get-selections' on each system if you're interested.

---

