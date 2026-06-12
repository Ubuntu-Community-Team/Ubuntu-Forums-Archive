---
title: "Can't boot, update, upgrade or run a cd"
date: 2008-08-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Karnex420 on 2008-08-31
I left my computer for 8 months and when I came back, I saw my cd rom player was unplugged and wouldn't work after I plugged it in.  When Intrepid came out, I decided to see if this would fix the problem.  Installation went fine by downloading the upgrade but firefox browser was too large for the screen, something else that carried over from Hardy so I uninstalled firefox and when I went to reinstall, intrepid crashed so I can't get back into ubuntu at all.  
  I was able once to get into the repositories to update but only for a short time.  I only got half an update.  
  I've been studying ubuntu now for three weeks but I can't find the problem.
  Are the repositories too busy?  I am in China but surely everyone here isn't waiting to get in.  Is there another way to go back to a working system?  If not, then is there an area I should study first?  I would gladly start typing new files if there are samples.

On start up I notice:
Failed to start the X server.
Then it disables the X server and says to restart the GDM when it is confiegured correctly.

mkdir cannot create directory-read only-fail

Starting SFS Client software: cannot find fully qualified domain name of this host.
set system name to fully-qualified domain name or fix /etc/resolv.conf sfscd. 
 
Apache 2 could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for server name.

Freezes on: 
Checking battery state.
Reloading web server config apache2
Reloading system log daemon...

I'm using:  
GNU Grub version 1.96
version 2.6.26-5 generic

When I run: fsck from the single user safe mode, 
I get:
/dev/sda1: 320959/14467072 files (1.8% non-contiguous), 2713197/28927032 blocks

When I run: sudo dpkg-reconfigure xserver-xorg, 
I get:  
debconf: Problem setting up the database defined by stanza 5 of /etc/debconf.conf.
Can't locate Debconf/DbDriver/Stack.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/per15 /usr/share/per15 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 19) line 2, <DEBCONF-CONFIG> chunk 5.
BEGIN failed--compilation aborted at (eval 19) line2, <DEBCONF-CONFIG> chunk5.

I will look for replacement files to copy.

---

