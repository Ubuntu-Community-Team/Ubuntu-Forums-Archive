---
title: "failed installation/ login in"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by anyutka2009 on 2012-05-05
Was upgrading to Ubuntu 12.04. As it was installing, shut off my laptop. now turned it on and tried to login. it won't let me and i can't log in. anything i can do? can i log in with recovery console?? really needd help here

---

### Post by carl4926 on 2012-05-05
You basically borked everything.

Re-install from scratch.

A live CD will let you get to your files in your /home/username
to back them up to a safe place

Then do a clean install

---

### Post by carl4926 on 2012-05-05
There is a remote possibility that you could chroot in to your installation and use synaptic from there to repair the mess you have.

What version were you upgrading from? Do you have the install CD for it?

---

### Post by anyutka2009 on 2012-05-05
will a usb work? and how do i save my files?

---

### Post by carl4926 on 2012-05-05
A live USB will be OK
You need a partition to save the files to (Unless you have a separate /home partition, in which case you can do a new install and leave that un-formatted) or an external HD to backup the files to? I've used a windows partition before on computers I've repaired, assuming it has the space. I just create a folder on the C, call it linux_files or whatever you like. Copy your files over. Re-insatall Ubu. Copy the files back once Ub is up and running.

---

### Post by anyutka2009 on 2012-05-05
i'll be prompted when i reinstall with the usb what i want to do, right?
i've intalled it before when i had all my files backed up, but this time nothing is backed up.

---

### Post by anyutka2009 on 2012-05-05
> **carl4926 said:**
> There is a remote possibility that you could chroot in to your installation and use synaptic from there to repair the mess you have.

What version were you upgrading from? Do you have the install CD for it?


i was upgrading from ubuntu 11.10 to ubuntu 12.04. 
what do u mean by chroot?
i have a live usb, not cd

---

### Post by carl4926 on 2012-05-05
Don't you know if you have a separate /home or not? Don't you have a windows installation?

The installer will not prompt you to backup. And it may well make a suggestion for the install that is not ideal. I always choose something else here: [http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/4_install_custom.jpeg](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/4_install_custom.jpeg)
And manage my partition manually

---

### Post by anyutka2009 on 2012-05-05
i don't have windows installation.... guess ill have to have my bro do this for me

---

