---
title: "Installation problem on Compaq Presario R4125US"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by arunabha on 2005-10-29
I tried installing Ubuntu on a compaq presario R4125US laptop which has a ATI radeon 200M grapics card with 128MB ram . the installation goes fine but X does not start up. ATI provides a proprietary driver for linux but i dont know how to install it in Ubuntu . Another thing is i was never asked for a root password . how do i get root access?

---

### Post by jeanfrancoismelancon on 2005-11-14
I have a presario R4000 and X would not start you have to edit xorg.conf file. In Ubuntu there is no root account (or is not accessible) You must use sudo to get root privileges (and when prompt for a password it your username's password created at installation).

sudo nano /etc/X11/xorg.conf

Edit the "Device" and had the following:

Option      "NoAccel" "true"

And then startx!

---

