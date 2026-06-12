---
title: "samba"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by leteci on 2005-09-21
I install samba with synaptic, but it's not working! When i type /etc/init.d/samba start get message fail. quick howto or help?

thnx

---

### Post by davmac on 2005-09-21
Have you seen [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver) ?

This covers installation and set up of Samba pretty well IMO.

Regards,

Dave Mac

---

### Post by tenjin on 2005-09-21
Hi,

Post the error message and let's go from there.

Cheers

D.

---

### Post by leteci on 2005-09-21
sudo testparm:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.

sudo /etc/init.d/samba start

 * Starting Samba daemons..                                              [fail]

---

### Post by tenjin on 2005-09-21
Hi,

Okay, can you post your samba config file as well please (star out anything you don't want the world to see).

Cheers

D.

---

### Post by leteci on 2005-09-21
my config

---

### Post by tenjin on 2005-09-21
Hi,

Looking at the error message I would comment out this section as a first try:

[]
path = /home/ubuntu
available = yes
browseable = yes
public = yes
writable = yes


I'll look at this in more detail later (off out now).

Cheers

D.

---

### Post by leteci on 2005-09-23
If I comment out this section, then samba start, 

* Starting Samba daemons.. [OK]

but now nothing is shared!

---

### Post by davmac on 2005-09-23
I think the problem is possibly that you haven't given the section a name. Try replacing the "[]" with "[myshare]". Does this solve the problem?

Dave Mac

---

### Post by fordfan753 on 2005-09-23
[QUOTE=davmac]I think the problem is possibly that you haven't given the section a name. Try replacing the "[]" with "[myshare]". Does this solve the problem?

Dave Mac[/QUOTE]

This is one problem...also, it is a good idea to add
```
netbios name = machine_name
``` 
Just put this on a new line underneath the workgroup setting.

---

