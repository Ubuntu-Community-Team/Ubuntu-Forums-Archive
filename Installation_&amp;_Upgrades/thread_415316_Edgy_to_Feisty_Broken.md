---
title: "Edgy to Feisty: Broken"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by horatiub on 2007-04-20
of course, I used apt-get to upgrade from Edgy to Feisty and now my system is broken.

The following packages have unmet dependencies.
  gconf2: Depends: python (>= 2.5) but 2.4.3-11ubuntu3 is installed
  gnome-applets: Depends: libgnomekbd1 but it is not installed
                 Depends: libxklavier11 but it is not installed
  gnome-control-center: Depends: libgnomekbd1 but it is not installed
                        Depends: libxklavier11 but it is not installed
  hal-device-manager: Depends: python-dbus but it is not installed
                      Depends: hwdb-client-gnome but it is not installed
  libgnomekbdui1: Depends: libgnomekbd1 but it is not installed
                  Depends: libxklavier11 but it is not installed
  libmetacity0: Depends: metacity-common (>= 1:2.18) but it is not installed
                Depends: metacity-common (< 1:2.19) but it is not installed
E: Unmet dependencies. Try using -f.

i tried the apt-get -f install and No Go.

what other options do I have? I really don't wanna reinstall the whole thing.

Thanks

---

### Post by horatiub on 2007-04-20
anybody? Please

---

### Post by Nobber on 2007-04-20
Did you do 'apt-get upgrade' or 'apt-get dist-upgrade'?

---

### Post by horatiub on 2007-04-20
apt-get dist-upgrade

---

### Post by Rui Pais on 2007-04-20
hi,
check if you haven't any edgy entry on your /etc/apt/sources.list.

How do you upgraded? 

if you used apt-get dist-upgrade try with:
```
gksu "update-manager -c"
```

If you already try that, close any gnome session, go to a console (press Ctrl+Alt+F1)
and try:
```
sudo aptitude dist-upgrade
```
and if that fails
```
sudo aptitude install
```
(without no package name)

---

### Post by Nobber on 2007-04-20
Hmm. I would try another round of:

  sudo apt-get update

and

  sudo apt-get dist-upgrade

to see whether the missing dependencies get filled in.

---

### Post by horatiub on 2007-04-20
tried all of them through the command line, none of those commands work. 

and I have no edgy in my sources.list

I get the same dependency errors: 

Reading package lists... Done
Building dependency tree... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
  gconf2: Depends: python (>= 2.5) but 2.4.3-11ubuntu3 is installed
  gnome-applets: Depends: libgnomekbd1 but it is not installed
                 Depends: libxklavier11 but it is not installed
  gnome-control-center: Depends: libgnomekbd1 but it is not installed
                        Depends: libxklavier11 but it is not installed
  hal-device-manager: Depends: python-dbus but it is not installed
                      Depends: hwdb-client-gnome but it is not installed
  libgnomekbdui1: Depends: libgnomekbd1 but it is not installed
                  Depends: libxklavier11 but it is not installed
  libmetacity0: Depends: metacity-common (>= 1:2.18) but it is not installed
                Depends: metacity-common (< 1:2.19) but it is not installed
E: Unmet dependencies. Try using -f.

I guess it needs python 2.5 but I can't install it

---

### Post by Rui Pais on 2007-04-20
uhmm... bad luck.

You can try then with synaptic and install/upgrade only python (seems to be the first broken). 
Check too if you haven't any package at 'Broken' section. Check if you have ubuntu-desktop installed (it's a fundamental package for a successful upgrade).

If synaptic fails, my other suggestion would be, close any gnome session. Go to a console and try:
```
sudo aptitude install python
```
with aptitude not apt-get. 
Aptitude should offer you a series of option to solve any dependency issues.

If still fails.. you may want to try to remove python first and then try continue with the upgrade.

---

### Post by danbh on 2007-04-20
Hey man, I used apt-get to upgrade also, and had lots of failures.  The recommended method is to use the update manager, and in this case, its actually true.  

But, you are in the bind already.  Here are the commands that I would run, not sure what order:

sudo apt-get install ubuntu-desktop^
sudo apt-get install linux-generic
sudo apt-get dselect-upgrade
sudo apt-get autoremove

And, when there are errors, run whatever command the error suggests to run.  I always find those commands to be helpful.  

Hopefully, you can get into x with this.  I do have another tip (gtkorphan), but you should first find a way into x.

---

