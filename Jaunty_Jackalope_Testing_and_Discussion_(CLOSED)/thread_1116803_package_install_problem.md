---
title: "package install problem"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Lucretius on 2009-04-05
tried to upgrade yesterday and found several packages would not install...

here is my terminal output.

Do you want to continue [Y/n]? y
(Reading database ... 170216 files and directories currently installed.)
Preparing to replace libgutenprint2 5.2.3-0ubuntu2 (using .../libgutenprint2_5.2.3-0ubuntu5_i386.deb) ...
Unpacking replacement libgutenprint2 ...
dpkg: error processing /var/cache/apt/archives/libgutenprint2_5.2.3-0ubuntu5_i386.deb (--unpack):
 unable to stat `./usr/share/gutenprint/5.2/xml/escp2/inks/claria.xml' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace python-gtksourceview2 2.5.0-0ubuntu1 (using .../python-gtksourceview2_2.6.0-0ubuntu1_i386.deb) ...
Unpacking replacement python-gtksourceview2 ...
dpkg: error processing /var/cache/apt/archives/python-gtksourceview2_2.6.0-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/gtk-doc/html/pygtksourceview2/style.css' (which I was about to install): Input/output error
Preparing to replace gnome-pilot 2.0.15-2.4ubuntu2 (using .../gnome-pilot_2.0.17-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-pilot ...
dpkg: error processing /var/cache/apt/archives/gnome-pilot_2.0.17-0ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/share/gnome-pilot/glade/pilot-applet.glade' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgutenprint2_5.2.3-0ubuntu5_i386.deb
 /var/cache/apt/archives/python-gtksourceview2_2.6.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-pilot_2.0.17-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any suggestions? my attempts with dpkg have been less than succesfull

---

### Post by ajgreeny on 2009-04-05
Try ```
sudo apt-get install -f
``` just in case you have broken packages.

---

### Post by Lucretius on 2009-04-05
command had no effect... synaptic claims I have no broken packages

---

### Post by lamalex on 2009-04-05
You could try 
 dpkg --clean-avail
 aptitude update

you might also want to fsck your disk, could be losing your hard drive.

---

### Post by Lucretius on 2009-04-06
hmm dpkg --clean-avail came up with a "command not found" error

hopefully the hard drive is not on the way out... it's an asus aspire one and it's less than 4 months old

---

### Post by psyke83 on 2009-04-06
> **Lucretius said:**
> hmm dpkg --clean-avail came up with a "command not found" error

hopefully the hard drive is not on the way out... it's an asus aspire one and it's less than 4 months old

Is your disk full? 

```
$ df -m
```

---

### Post by Lucretius on 2009-04-06
no it's a 120gb hard disk and jaunty is the only thing on it...

i'll re-install and see if that solves it

---

### Post by lamalex on 2009-04-06
> **Lucretius said:**
> hmm dpkg --clean-avail came up with a "command not found" error

hopefully the hard drive is not on the way out... it's an asus aspire one and it's less than 4 months old

Sorry, typo. Should have been dpkg --clear-avail

---

