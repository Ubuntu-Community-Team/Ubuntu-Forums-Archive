---
title: "dpkg error coded 1 when removing gnome-shell"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by 45acp on 2010-06-22
Tried sudo apt-get remove gnome-shell -f Didn't work Still returns:
 Errors were encountered while processing:
 gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)

How so I fix this?

Thanks in advance.

---

### Post by 45acp on 2010-06-22
I also got:

E: gnome-shell: subprocess installed post-removal script returned error exit status 127 

when I tried to remove it with synaptic.

---

### Post by wojox on 2010-06-22
Try try **apt-get -f install**

**apt-get upgrade**

---

### Post by 45acp on 2010-06-22
Now I got this after running the above:

james@james-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-shell
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,245kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 213323 files and directories currently installed.)
Removing gnome-shell ...
/var/lib/dpkg/info/gnome-shell.postrm: 10: glib-compile-schemas: not found
dpkg: error processing gnome-shell (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)


james@james-desktop:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  gnome-shell
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,245kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 213323 files and directories currently installed.)
Removing gnome-shell ...
/var/lib/dpkg/info/gnome-shell.postrm: 10: glib-compile-schemas: not found
dpkg: error processing gnome-shell (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wojox on 2010-06-22
Back to square one :p

---

### Post by wojox on 2010-06-22
sudo apt-get clean
sudo apt-get update

---

### Post by 45acp on 2010-06-22
I deleted everything in /var/lib/dpkg/info/ that had to do with gnome-shell. Now I am no longer getting the error message. When I removed it I got:

james@james-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-shell
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,245kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `gnome-shell' missing, assuming package has no files currently installed.
(Reading database ... 213322 files and directories currently installed.)
Removing gnome-shell ...
  

I don't know if I actually removed gnome-shell but I can add and remove programs now.

---

### Post by rp88 on 2010-06-22
I also had the same problem. Here is what i did to fix it.

sudo gedit /var/lib/dpkg/info/gnome-shell.postrm

in that file there is a line: [COLOR="#a0522d"]remove|purge)	glib-compile-schemas /usr/share/glib-2.0/schemas ;;[/COLOR]

replace that line with: [COLOR="Sienna"]install)	glib-compile-schemas /usr/share/glib-2.0/schemas ;;[/COLOR]

Save and close it. 

Then run: sudo apt-get purge gnome-shell

---

### Post by Da CalebMan on 2010-06-24
Dude, it's illegal to be that smart ;)

Thanks man, you're a life-saver :D

~STEELBANANA

---

### Post by starnixsa on 2010-06-25
@rp88

Thanks, that fixed it! :)

---

