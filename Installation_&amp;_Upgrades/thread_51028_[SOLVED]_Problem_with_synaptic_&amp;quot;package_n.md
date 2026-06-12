---
title: "[SOLVED] Problem with synaptic: &amp;quot;package needs to be reinstalled, can't find arc"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by Juggernaut on 2005-07-22
First of all, sorry for double-posting this, but I guess no one's reading the Warty messages anymore. 

I have a Brother HL 5130 laser printer.

Gnome was able to detect it, but didn't have the according driver. I thought I wouldn't get the best results when using a driver for a similar model (5040 I think).

Brother provides drivers for Linux on their homepage, even in deb-format. The name is something like hl5130.deb

I tried to install it wih dpkg, but it wouldn't work because some dirs were missing.

I tried to create those missing directories manually and sort of messed everything up.

It's still not working, but now whenever I start synaptics, I get this error message:
E: The package hl5130 needs to be reinstalled, but I can't find an archive for it.

I tried to de-install the driver with dpkg -r --force-remove-reinstreq hl5130 but it always tells me that it can't find anything to remove.

Tried sudo apt-get autoclean, update, upgrade and the like, but to no avail.

Synaptic will crash whenever I try to update all packages.  :-(

It'd be great if someone could help me with this!

---

### Post by Juggernaut on 2005-07-22
Problem solved.

Created all missing directories manually, then I was able to install that drive.

Now I can use apt-get again. Will worry about printing later.

---

### Post by tokyo_ on 2006-08-09
Thanks, this worked also for me.

---

### Post by stego_s_aurus on 2007-09-02
To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".

---

### Post by Cullen on 2007-09-21
I did what stegosaurus suggested but that still didn't resolve the issue. In the end I searched for the package in question in the /var/lib/dpkg/status file and deleted everything under that heading.  Then synaptic was fixed, AND I was able to reinstall the package and it worked properly.

* It did take an ENORMOUS amount of time to perform the re-install.

---

