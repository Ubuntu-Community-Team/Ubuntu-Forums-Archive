---
title: "Error on etc/environment"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by marcos.placona on 2007-08-18
Hi Guys, it's been a while since I've last posted here. I was running my Ubuntu fine here, but decided to add some environment variables to it, so they would be loaded when I logged in.

I added them to /etc/environment, doing:

sudo gedit /etc/environment

I added my variables, saved and tried to logoff and login again.

Now, I can't login, 'cause it says my session lasted for less than 10 seconds, and tells me that there's a problema with my /etc/environment file.

My question. Is there any chance for me to recover to the old /etc/environment, or even upate that file to remove the last 4 lines (the lines I added with my variables)?

I tried to do it via terminal, but with no success as when I try to use gedit or edit, it tells me that it can't display it.

Thanks,

Marcos Placona

---

### Post by david_2001 on 2007-08-18
I cannot remember whether it's a default preference or not but gedit may have saved a backup of your /etc/environment file as /etc/environment~.  Otherwise, it sounds like you need to use a console based text editor such as nano.  If you don't have any suitable editor installed then just rename /etc/environment to something like /etc/environment.bak so that it doesn't get loaded when your PC boots.

---

### Post by bapoumba on 2007-08-19
Try CTRL-ALT-F2, this will bring you to one of the text-mode sessions. Login and then you can edit the file with nano (**sudo nano /etc/environment**, CTRL-O to save the file, CTRL-X to exit nano). CTRL-ALT-F7 will get you back to the graphics session.

If you cannot go to the tty that way, boot in recovery mode (careful, you'll be root). After editing the file, enter **reboot**.

---

