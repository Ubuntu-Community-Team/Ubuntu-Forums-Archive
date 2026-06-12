---
title: "Dell Mini 10 and 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by lisanels47 on 2012-04-26
Great!  My Dell Mini 10 now works with 12.04 LTS.  

Installed using the i386 live image.  After the install, I didn't get the logon screen, but after logging in using CTRL-ALT-F2, I set the root password up, ran updates, and was able to get a logon screen.

I had to choose Ubuntu 2D because my screen was half size horiz.  Now it's working great.

---

### Post by GnuSense on 2012-04-30
What are your boot speeds? My Mini 9 boots to the display manager in about 10 seconds, I understand boot times are quite a bit lower on 12.04.  I'm not planning on upgrading for another year since Lucid is still supported, but it might be nice to have a newer, better wifi driver.

---

### Post by jahst on 2012-09-09
other option worked for me so posting here for future reference

[http://askubuntu.com/questions/140371/ubuntu-12-04-logon-issues-on-dell-mini-10-gma-500/185824#185824](http://askubuntu.com/questions/140371/ubuntu-12-04-logon-issues-on-dell-mini-10-gma-500/185824#185824)


------------------------------------------


Finally fixed this over the summer.
Here's what I had to do.

Edit /etc/default/grub file

Make the GRUB_CMDLINE_LINUX_DEFAULT line looks like this

GRUB_CMDLINE_LINUX_DEFAULT="console=tty1 mem=896mb"

install desktop-base 

sudo apt-get install desktop-base

desktop-base does something to fix it.. no idea what.. but 

GRUB_CMDLINE_LINUX_DEFAULT="console=tty1 mem=896mb" alone still has the split screen problem.



** NOTE - installing desktop-base adds the debian space background to grub boot menu. 
I believe you can remove this by deleting or editing /usr/share/images/desktop-base/desktop-grub.png

or just leave it and enjoy the fact you can finally login without that annoying split screen.

Also, installing lubuntu-desktop helps a lot on the mini10.. actually quite usable. 

If you get a strange blank section between wireless icon and power icon.. right click on the panel, add-remove panel items. Remove the "system-tray" and add "indicator-applets"

If you want a unity look/feel... right click the panel and customize the settings. Move it to the left, change the width to 35 or 40 pixels.... and change color to solid opacity with transparency.. or anything other than the default image. This setup closely resembles the unity look/feel. 



later,

jahst

---

