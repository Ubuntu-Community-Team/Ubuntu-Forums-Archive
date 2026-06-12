---
title: "Dependency Probems"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2006-06-04
It appears that my problem all along has been dependencies. I have read the advice at the head of this forum on solving dependencies, but the directions cause me concern. They come with warning "be careful of what you delete." Fine, but I have no idea what will happen with some apps I use all the time (e.g., open office). I've tried navigating through Synapic to solve the dependency problems but I can't seem to get anything resolved. I know Dapper will be great if I can ever get in installed, I've been very happy with Breezy and Dapper has to be better still. 
This is my third or fourth thread, and I've tried all the suggestions. Each try comes down to these dependencies. Now I'm on my knees: Will somebody dig me out of this hole?](*,) 

Here are the unmet dependencies:


The following packages have unmet dependencies:
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: deskbar-applet but it is not going to be installed
                  Depends: ekiga but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be installed
                  Depends: gnome-screensaver but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be installed
                  Depends: gnome-volume-manager but it is not going to be installed
                  Depends: gnopernicus but it is not going to be installed
                  Depends: gok but it is not going to be installed
                  Depends: libgnomevfs2-bin but it is not going to be installed
                  Depends: libgnomevfs2-extra but it is not going to be installed
                  Depends: openoffice.org-gnome but it is not going to be installed
E: Broken packages

---

### Post by az on 2006-06-04
So, all of your sources are dapper and you have updated and now are dist-upgrading?

Is that so?

Have you ever installed stuff from other repositories?  If so, what?

If the above answers are yes, yes and no, what is the output from

sudo apt-get install gok

---

### Post by lakelovers on 2006-06-04
Yes to your first question. I have changed all the sources to dapper (in fact used the recommended source list. And I updated, more than once and upgraded more than once without success. I think I have installed apps from other repositories but I cannot say what. I can't run "sudo apt-get install gok" because I just lost my X server, after rebooting. So, now I have that problem to fix before I can do anything more in Ubuntu. I must say this has turned into a nightmare. Thank you for your response. If you can help me out of this mess it will be much appreciated. Fortunately, I have my wife's laptop  running with WinXP to keep me in touch with this forum.
Jerry

---

### Post by az on 2006-06-05
Are you upgrading or dist-upgrading?

You need to be dist-upgrading.

And probably fixing this problem will fix your X problems.  Boot into recovery mode and 

apt-get dist-upgrade

---

### Post by lakelovers on 2006-06-05
[QUOTE=azz]Are you upgrading or dist-upgrading?

You need to be dist-upgrading.

And probably fixing this problem will fix your X problems.  Boot into recovery mode and 

apt-get dist-upgrade[/QUOTE]

I don't know how I did it but I got Dapper Upgraded successfully. I think it's great and darn fast. I did get a couple of errors but, apparently, they're not serious because everything seems to be working.
Jerry

---

### Post by az on 2006-06-05
What did you do, and does

sudo apt-get -f install

still give you errors? - that command should complete the installation of any half-installed packages.

---

### Post by lakelovers on 2006-06-05
As best as I can recall, here's what I did: After three or four attemps, I reboot and found that I lost access to the xserver. I messed around most of the day recovering from that, and at one point I think I used the code your refer to: "sudo apt-get -f install." That and reconfiguring xserver got me back into the Breezy desktop. Then, I tried upgrading again with this code:  "sudo apt-get update && apt-get dist-upgrade," and to my surprise, all worked with just a couple of errors, which don't seem to effect the operation at this point.

One error: "backuppc sub-process /usr/bin/dpkg returned an error code (1) Could not load /con/con'000-write not found. I may have that /con/con'000 wrong. I wrote it down and can't read my writing.

Another error appeared after loading the desktop which said that an icon could not be found.

I installed Openoffice Writer, which also ended with an error saying it was not completely installed, but it seems to work okay.

I'll try your code "sudo apt-get -f install" to see if it clears things up.

---

### Post by lakelovers on 2006-06-05
Azz. . .
Here's what I got after running "sudo apt-get -f install:" What action should I take to clean this?

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up backuppc (2.1.2-2ubuntu5) ...
 * Starting backuppc... 2006-06-05 20:05:19 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by az on 2006-06-06
sudo apt-get install --reinstall backuppc

or

sudo apt-get remove backuppc

---

### Post by lakelovers on 2006-06-06
[QUOTE=azz]sudo apt-get install --reinstall backuppc

or

sudo apt-get remove backuppc[/QUOTE]

azz. . . 

Thank for your help. I removed it. I find that my printer is not printing, I have a Canon i560 using TurboPrint. I've had problems with it before whenever I install a new system, so I guess I'll figure it out. There's always something . . . which make me very appreciative of these forums.

Jerry

---

