---
title: "Maverick netbook upgrade disaster"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by Wtwine on 2010-10-21
Hi

I was running my Sony Vaio netbook on Lucid netbook edition.  I had set it up so that it ran in a Gnome session so that it had the netbook edition layout but I could add and remove applets, which you can't do in netbook session (very irritating!)

Well, last night I upgraded to Maverick, but forgot that I was running Gnome  session at the time.  The result is a bit of a disaster.  If I log into a netbook session, I see the Unity launcher on the left BUT also the old Lucid-style netbook launcher underneath! (See screen shot).  Both launchers work BUT when I click on the Ubuntu logo in top left and click oon an icon like "Office", I get a message saying that there are no office applications installed on this computer.  I can however access the office submenu from the Lucid-style launcher.   If I log into a Gnome session, the layout is like the Lucid netbook edition but there is no panel!

Also, when I try upgrade (apt-get or aptitude safe)  I get a long string of  error messages such as :
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of at-spi:
 at-spi depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

and it ends with 

Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried 
sudo dpkg --configure -a
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get --fix-missing upgrade
sudo apt-get -f install
sudo apt-get --reinstall install memtest86+

But to no avail.  Any suggestions??

thanks

---

### Post by Wtwine on 2010-10-24
Anybody? Can somebody at least explain why I am not able to install or remove any software?  See error message below after upgrades have been downloaded and are about to be installed.  There seems to be a problem with gconf2 but reconfiguring or uninstalling and reinstalling gconf2 did not solve it.  By the way, just realised that Gnome is not installed at all, and I get these errors when I try installing Gnome. 

(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `memtest86+' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 162, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 121, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory: '/usr/share/gconf/mandatory/share'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-common:
 totem-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

---

