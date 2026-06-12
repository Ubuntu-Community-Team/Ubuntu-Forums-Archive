---
title: "Ltsp - Ubuntu server 7.10 - trying connect to windows"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by Gcentenari on 2008-02-09
Hi, I am new in ubuntu and my english is not so good...I'm sorry

I installed ubuntu server 7.10, then I installed x.org, gnome and LTSP. every works fine.
When I start a thin client using PXE, the system start up, using gnome and works fantastic. Using  gnome, I connect to a windows server via rdesktop and run perfectly.

The problem is I need to startup using rdesktop to connect to the windows server, I touch lts.conf reading the documentantion but don't work.

My lts.conf is ( I moved the file lts.conf to  /var/lib/tftpboot/ltsp/i386/  )

# This is the default lts.conf file for ltsp 5.
# For more information about valid options please see:
# /usr/share/doc/ltsp-client/examples/lts-parameters.txt.gz
# in the client environment.
#
# Note that things like sound and local device support are
# auto-enabled if the corresponding packages are installed,
# there is no need to manually set these options anymore.
#
# **** THIS FILE SHOULD NO LONGER BE USED FROM HERE !!! ****
#
# With the introduction of the nbd/unionfs/squashfs structure
# the lts.conf file moved to the tftp root please create:
# /var/lib/tftpboot/ltsp/i386/lts.conf instead for your changes
#
# In case you want to use the lts.conf here, this still works,
# but you need to run ltsp-update-image after every change.
[default]
  LTSP_VERSION=5.0.39

This file work fine , but when I add:
[default]
  LTSP_VERSION=5.0.39
  SCREEN_01    = rdesktop -f -a 8 -g 1024x768 -N 192.168.1.2

don't work  (this command works find if i start up via gnome)

I tried difrentes ways...
[default]
   LTSP_VERSION=5.0.39
   SERVER           = 192.168.1.200
   RDP_SERVER       = 192.168.1.2
   DNS_SERVER       = 192.168.1.1
   XSERVER          = auto
   SCREEN_01        = startx
   SCREEN_02        = shell
   SCREEN_03        = rdesktop
   SOUND            = Y
   XkbLayout        = "es"
   SEARCH_DOMAIN    = clinicasanfernando.com.ar

and don't work !!!

Please help me
Thanks a lot, (sorry for my English)

---

### Post by Gcentenari on 2008-02-12
Thank irc Ubuntu!!!!

Solutions:  instal rdesktop in the ltsp

type this command

sudo chroot /opt/ltsp/i386
apt-get install rdesktop
exit

then...

ltsp-update-image

Thank irc Ubuntu    Again !!!!

---

### Post by stangman on 2008-03-18
Ok, I've got a similar situation,
it's just that the LTSP Ubuntu package is not running on a Ubuntu distro,
so the 'apt-get install rdesktop' command doens't work for me.

How can I get the rdesktop script running?
Is there a location where I can download the required files?
I tried scripts for LTSP4.2 and placed them into the screen.d directory, but they require specific LTSP 4.2 files, so that will not work...

Many thanks in advance.

---

