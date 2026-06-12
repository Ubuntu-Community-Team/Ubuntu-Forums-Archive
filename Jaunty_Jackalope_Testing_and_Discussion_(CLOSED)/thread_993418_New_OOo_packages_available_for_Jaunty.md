---
title: "New OOo packages available for Jaunty"
date: 2008-11-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2008-11-25
I've just noticed that new (unofficial) packages are available for Jaunty in PPA (3.0.0-2 for Intrepid have gone, to be replaced by 3.0.0-4).

However, if you simply upgrade OOo refuses to start - if you remove 'openoffice.org-gnome' it will work. This will have the side-effect of aptitude wanting to remove 'openoffice.org-gtk' too; without the gtk package OOo looks pretty dire.

## OOo
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) jaunty main
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) jaunty main

---

### Post by Trueno22 on 2008-11-25
sweetness

---

### Post by calc on 2008-11-25
> **jfernyhough said:**
> I've just noticed that new (unofficial) packages are available for Jaunty in PPA (3.0.0-2 for Intrepid have gone, to be replaced by 3.0.0-4).

However, if you simply upgrade OOo refuses to start - if you remove 'openoffice.org-gnome' it will work. This will have the side-effect of aptitude wanting to remove 'openoffice.org-gtk' too; without the gtk package OOo looks pretty dire.

I will see if I can track down why it crashes and get it fixed by next week.

---

### Post by autocrosser on 2008-11-25
I used Synaptic to remove OOO-gnome & it didn't complain about -gtk---Still looks ok here....

---

### Post by punischdude on 2008-11-26
The OOo Packages have been deleted. [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

I guess OOo 3 will hit Intrepid backports soon. :guitar:

// edit: No, heres the reason: > The packages were buggy and crashed when openoffice.org-gnome was installed, they will be reuploaded when the bug has been resolved.

---

### Post by philinux on 2008-11-26
Is this the place to check pending backport updates?
[http://people.ubuntu.com/~ubuntu-archive/pending-sru.html](http://people.ubuntu.com/~ubuntu-archive/pending-sru.html)

Or is there another link I need.

---

### Post by olskar on 2008-11-26
Is this why I can not get the updates on openoffice my updatemanagers wants me to in Intrepid?

---

### Post by punischdude on 2008-11-26
> **calc said:**
> I will see if I can track down why it crashes and get it fixed by next week.

There is the same/a similar issue with **openoffice-kde**

---

### Post by jfernyhough on 2008-11-26
> **calc said:**
> I will see if I can track down why it crashes and get it fixed by next week.Where do we report bugs for PPA packages? Obviously it wouldn't be helpful for me to report against the official Ubuntu openoffice.org packages. :D

> **autocrosser said:**
> I used Synaptic to remove OOO-gnome & it didn't complain about -gtk---Still looks ok here....

-gtk will be seen as autoremovable as no other packages require it. You can check in synaptic by filtering by Status in the bottom-left. Because it's set as autoremovable aptitude will automatically remove. ;)

---

### Post by caryb on 2008-11-26
I update from the repo yesterday & now any ooo app I open wants to recover some lost document & no matter what I select it crashes:confused:


Cary

---

### Post by frankleeee on 2008-11-26
> **caryb said:**
> I update from the repo yesterday & now any ooo app I open wants to recover some lost document & no matter what I select it crashes:confused:


Cary

The repository has had 00o3 removed for a couple of days I believe what is actually installed in your computer is it 00o3. you may also need to do the OO-gnome mentioned earlier in this thread to get it working be careful.

---

