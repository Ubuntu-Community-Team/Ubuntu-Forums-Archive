---
title: "Boinc upgrade"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by nixie21 on 2008-10-07
The Boinc manager is behind a couple versions in the repositories (Kubuntu)

How can I upgrade the one I have to the new version?

I do not know how to replace my version if I download it, any help would be great...

thanks!

---

### Post by Braytok on 2008-10-07
1.) Download the latest (version 6.2.15) from [BOINC]("http://boinc.berkeley.edu/download.php") to your desktop

2.) From a terminal:
```
cd /home/YOUR_USER_NAME/Desktop/
```

3.)From the same terminal:
```
sudo ./boinc_6*
```

Hope I got it right. :P I've never used it but the install seamed pretty straight forward.

Edit: I just noticed you were wanting to upgrade. this was for the regular install so I don't now if it will use your old config files or not.

---

### Post by nixie21 on 2008-10-07
Thanks

I get an error

nixie21@Kubuntu:~/Desktop$ sudo ./boinc_6*
sudo: ./boinc_6.2.15_i686-pc-linux-gnu.sh: command not found

Thanks

---

### Post by Partyboi2 on 2008-10-07
try
```
 sh boinc_6.2.15_i686-pc-linux-gnu.sh 
```
from the Desktop directory

---

### Post by Braytok on 2008-10-07
My deepest apology, I goofed.

the command should be 

```
sudo sh boinc_6*
```

sorry about that.:(

edit: :) Partyboi2 beat me to it.

---

### Post by lotharjade on 2008-10-12
Is this going to get fixed in the repositories at some point?  Your solution does not update the info in the package manager, or the link in the application drop down.

---

### Post by Partyboi2 on 2008-10-13
> **lotharjade said:**
> Is this going to get fixed in the repositories at some point?  Your solution does not update the info in the package manager, or the link in the application drop down.
The version in the hardy repo's will probably stay the same. An updated version (boinc 6.2) will be available if you ugrade to intrepid when it is released.

---

### Post by Philk on 2008-10-13
Thanks for that help and for the information about Intrepid - I've been looking forward to that release, too.

I'm using the 64-bit version and received a response of "use /home/phil/Desktop/BOINC/run_manager to start BOINC" to that sh command.  The suggested command does generate BOINC, but I get a recurrent warning as follows:
 (boincmgr:10828): Gtk-WARNING **: /build/buildd/gtk+2.0-2.12.9/gtk/gtkwidget.c:8547: widget class `GtkPizza' has no property named `row-ending-details'

Is this something to be concerned about?  Should I just go back to using the earlier version of BOINC until Intrepid?

---

### Post by Partyboi2 on 2008-10-13
From what I have read it is  a warning and it should be safe to ignore 
> [I](python:9250): Gtk-WARNING **:
[/I]>[I] > /build/buildd/gtk+2.0-2.12.9/gtk/gtkwidget.c:8547: widget class
[/I]>[I] > `GtkPizza' has no property named `row-ending-details'
[/I]>[I] >
[/I]>>[I]  GtkPizza is the name of a custom GTK widget that wxWidgets has implemented
[/I]>[I] to help with things like wx.Panel, generic controls, etc. Apparently GTK
[/I]>[I] 2.12 has added a new standard slot that wx isn't implementing yet.  It
[/I]>[I] should be safe to ignore it for now as GTK should have an appropriate
[/I]>* default for the property.*
[FONT=monospace]**[/FONT]

---

