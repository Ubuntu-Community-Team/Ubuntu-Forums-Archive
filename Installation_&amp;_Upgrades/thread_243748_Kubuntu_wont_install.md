---
title: "Kubuntu wont install?"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by Captain Kirk76 on 2006-08-25
Kubuntu wont install, it gives this error. It is a CD i ordered through ShipIt Free CDs 


```
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 311, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 731, in process_step
    self.gparted_to_mountpoints()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 804, in gparted_to_mountpoints
    print >>self.qtparted_subp.stdin, "apply"
AttributeError: 'NoneType' object has no attribute 'stdin'

```

I currently have Ubuntu & Windows installed, but i also want Kubuntu. any ideas how to get it to work?

---

### Post by Captain Kirk76 on 2006-08-25
bump

---

### Post by thibeaz on 2006-08-25
well to get kubuntu you add it in your current ubuntu system by opening the terminal and typi```
sudo aptitude install kubuntu-desktop
``` after that is done and I mean done installing you log off and on the login screen click on options and find something about sessions and click kde or whatever... I can't remember because of that xserver error I thought I lost ubuntu so I installed freespire until edgy comes out stable. But I hope this was helpfull

---

### Post by Captain Kirk76 on 2006-08-26
I ADD it to Ubuntu? Then what do i do with the Kubuntu disc i got?

---

### Post by Captain Kirk76 on 2006-08-26
Bump

---

### Post by Captain Kirk76 on 2006-08-27
Yes. Another Bump

---

### Post by bcw on 2006-08-27
> **Captain Kirk76 said:**
> I ADD it to Ubuntu? Then what do i do with the Kubuntu disc i got?

Ubuntu is ubuntu.  When you install from an "Ubuntu" CD, you get the OS plus the Gnome desktop.  You can add in packages to use any desktop you want, and they will co-exist.

When you install from a "kubuntu" CD, you get the OS plus the KDE desktop by default, and the "xubuntu" CD is the OS plus the XFCE desktop.

The OS is the same - the desktop changes.

You can add (or remove) any of them from any other install through the network update mechanism:
```
aptitude install xubuntu-desktop
```

At the login window, depending on which login manager you installed - gdm, kdm, or xdm - there will be some place to pull down a menu and select which desktop manager you want for that session when you login.  Poke around before logging in.

You may be able to add your new CD to your sources so you can get the packages off it instead of the network.  I haven't done it and can't tell you more than this:
```
sudo apt-cdrom add
```

Follow the prompts and after that you're on your own.  But it's no big deal if you have network access - aptitude (or adept or synaptic) will do it as noted above.

Cheers,
Bret

---

