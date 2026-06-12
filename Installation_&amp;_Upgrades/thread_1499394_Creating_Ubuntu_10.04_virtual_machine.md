---
title: "Creating Ubuntu 10.04 virtual machine"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by andywhoa on 2010-06-01
Hi,

I'm having some trouble creating a VM of Ubuntu 10.04.

I've downloaded the ISO.  I've created a new VM using the VM Assistant.  I selected "Use operating system installation disc image file" and chosen the ISO.

When I run the VM, it sits at the following screen:

[IMG]http://i46.tinypic.com/a9n18y.png[/IMG]



I've selected Virtual Machine > Install VMware Tools.  Nothing happens.

Could someone point me in the right direction?


Thanks for your help

---

### Post by max.goedjen on 2010-06-01
The VMWare installer thing is unrelated, it always shows up if you haven't installed it. As to what it's sitting on, it looks like an accessibility icon. Check the preferences/settings on that virtual machine?

---

### Post by andywhoa on 2010-06-01
Thanks for your reply

For what?  The VM settings say the CD/DVD ROM is pointed at an installation image and that it's connected.  I'm not really sure where to go from here.

---

### Post by max.goedjen on 2010-06-01
Did you validate the installation image? (MD5/SHA?)

---

### Post by andywhoa on 2010-06-01
I'm not sure what the value of the installation ISO is supposed to be.

I've downloaded the minimal CD image and that seems to be running

---

### Post by max.goedjen on 2010-06-01
Did you try deleting that VM and trying again?
(and checksum values are next to the download links)

---

### Post by andywhoa on 2010-06-01
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

This page does not list any checksum values

I tried deleting the VM and trying again several times to no avail




So far so good with the minimal CD installer, though; so I'm hopeful


Thank you for your help so far

---

### Post by andywhoa on 2010-06-01
So it has finished installing.

When I boot I see "Ubuntu 10.04"

Then it essentially becomes a command prompt.  It wants the user/pw I set up and then it sits at a prompt waiting.

What do I type to boot into the desktop?  Did the gnome package not install or something?

---

