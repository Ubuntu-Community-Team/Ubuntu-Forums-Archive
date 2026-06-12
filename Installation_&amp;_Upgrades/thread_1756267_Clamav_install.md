---
title: "Clamav install"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by jkgoose937 on 2011-05-12
I've been trying to install clamav for the last 5 days and can't find any answers anywhere so this is my last hope. using kubuntu 11.04 

*** My error message from konsole: ***
sudo apt-get install -f clamav-freshclam clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav is already the newest version.
clamav-freshclam is already the newest version.
The following packages were automatically installed and are no longer required:
  mesa-utils wine1.3-gecko
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up clamav-freshclam (0.97+dfsg-2ubuntu1) ...
chown: invalid group: `clamav:adm'
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)

*** My error message from Synaptic: ***
Gtk-CRITICAL **: IA__gtk_assistant_set_page_header_image: assertion `child != NULL' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 27, <> line 1.
Preconfiguring packages ...
groups: cannot find name for group ID 124
(Reading database ... 167766 files and directories currently installed.)
Preparing to replace clamav-base 0.97+dfsg-2ubuntu1 (using .../clamav-base_0.97+dfsg-2ubuntu1_all.deb) ...
Unpacking replacement clamav-base ...
Processing triggers for man-db ...
Gtk-CRITICAL **: IA__gtk_assistant_set_page_header_image: assertion `child != NULL' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 27.
Setting up clamav-base (0.97+dfsg-2ubuntu1) ...
Gtk-CRITICAL **: IA__gtk_assistant_set_page_header_image: assertion `child != NULL' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 27.
groups: cannot find name for group ID 124
chown: invalid group: `clamav:clamav'
chown: invalid group: `clamav:clamav'
Setting up clamav-freshclam (0.97+dfsg-2ubuntu1) ...
Gtk-CRITICAL **: IA__gtk_assistant_set_page_header_image: assertion `child != NULL' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 27.
chown: invalid group: `clamav:adm'
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-freshclam (0.97+dfsg-2ubuntu1) ...
Gtk-CRITICAL **: IA__gtk_assistant_set_page_header_image: assertion `child != NULL' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 27.
chown: invalid group: `clamav:adm'
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-freshclam
 clamav

---

### Post by wilee-nilee on 2011-05-12
Bitdefender is a bit easier to use and has a nice shiny gui, and is a top rated scanner.
[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html)

---

### Post by wandalalakers on 2011-05-12
Just curious, when you install klamav, what happens?  I haven't installed 11.04 yet.
Oops, I just did a package search and see that klamav isn't available with Natty.

---

### Post by jkgoose937 on 2011-05-13
i've downloaded the clamav source tried complieing got a bunch of errors there too. some reason clamav isn't creating a clamav-data file or it's not avail for install or something. if anyone know the people that maintain clamav for ubuntu if they can look into what's happening too. i've even been looking into getting files from debian squeeze. klamav isn't avail for download in this new version of ubuntu too. so i've downloaded it and tried installing that way too. 

i'm thinking it has to do with: Gtk-CRITICAL **: IA__gtk_assistant_set_page_header_image: assertion `child != NULL' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 27.

what ever that is?

---

### Post by SeijiSensei on 2011-05-13
Try 

```
sudo apt-get -f install clamav clamav-*
```

That should clear up any missing dependencies.

The clamav-data package contains the database of virus signatures that clamav uses to detect malware.  It's updated nearly every day, so it's packaged separately from the clamav program itself.

---

### Post by jkgoose937 on 2011-05-30
I've tried "sudo apt-get -f install clamav clamav-*", doesn't work.
I've tried commenting out lines 26-28 of file "Gnome.pm", didn't work.
I've installed Gnome desktop environment and reinstalled that way, didn't work.
I've deleted my "/var/lib/dpkg/available" file and recreated it, didn't work.

I'm not a programmer and I don't know what "Gnome.pm" and specificity lines 26-28 of the file do. Since this issue doesn't seem to have a working solution I may just end up reinstalling kubuntu or an earlier version and then upgrade from that. Now luckily my home folder is on a different partition (I've learned my lesson years ago on this one), but it's just having to reinstall all the other programs I use too.

---

