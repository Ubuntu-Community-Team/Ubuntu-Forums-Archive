---
title: "All installations return error 139. can't install anything"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by rumo_orbis on 2007-05-22
since i tried to install mplayer last night it seems that i am unable to install anything.
i get the following error (this is when installing gconf-editor... but it happens with any program)
```
Setting up gconf-editor (2.18.0-0ubuntu1) ...

(update-desktop-database:17713): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gconf-editor (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gconf-editor
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i can't reinstall nor remove these broken packages, except if i do it manually. but that still does not fix the problem that im blocked from installing any programs.

would be really glad if you could help. would be most stupid to have to set up the system again just to fix this problem.

thanks, rumo.

---

### Post by rumo_orbis on 2007-05-23
Please... if you know any help... it would be really annoying having to reinstall the whole thing...

---

### Post by Hendrik-Jan on 2007-05-24
Sub-process /usr/bin/dpkg returned an error code (1)

I have the same problem

IM trying to remove vmware but i cant. from the synaptic manager its sias.. preoblem removing vmware you should ... (and nothing appears LOL)

what dooo ii dooooo ?

---

### Post by rumo_orbis on 2007-05-24
i read in an other thread how to manually uninstall something. maybe that solves the issue for you (i am not an linux pro... so i dont know about any possible negative effects):
```
dpkg-query -L vmware
```
this will list all the files that vmware installed. manually remove those, then:
```
sudo gedit /var/lib/dpkg/status
```
search for vmware and delete the entry.

now you can start synaptic and vmware shouldn't be installed anymore. my problem is though that i can't install anything anymore, cause it always gives my an error (look at post 1). but maybe it solves your problem.

i would still be very glad about any help. or even if someone could tell me that its an hopeless case. does someone know a more stable, lightweight debian-derived distro. should i try debian itself?

rumo

---

### Post by rumo_orbis on 2007-05-24
just another question... is your error also the 139 one?

---

### Post by rumo_orbis on 2007-05-26
i've found the issue... my mistake. i read in another post that in order to get rid of some xubuntu menu entries you should uncomment them. but apparently that leads to exactly the issue that i had to deal with.
so i changed that and it works again. do you maybe know how to get rid of unwanted menu entries without breaking your system? maybe a command to hide them?

thx
julian

---

### Post by rumo_orbis on 2007-05-26
found the solution in another thread. you have to add
```
NoDisplay=true
```
at the end of the .desktop files

---

