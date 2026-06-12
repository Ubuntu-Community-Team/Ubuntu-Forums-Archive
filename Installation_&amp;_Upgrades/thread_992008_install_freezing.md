---
title: "install freezing"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by ryansheakennedy on 2008-11-24
i have tried both 8.10 and 8.04 and they have the same problem. When the orange loading bar starts to fill it freezes at around 80%. A few times it will make it past that and get to a black screen with a text prompt in the top left corner that sits blinking. 


General specs are 2gb ram, amd 3400, geforce 7950, 32 bit...

i had suse working on it for a little but wanted to try ubuntu. Currently XP is on it running fine. 

also...if i install ubuntu, can i switch it to kde after the install if i find that i dont like gnome?

Any suggestions? and sorry if this is a double post.

---

### Post by lemming465 on 2008-11-25
You may need to try booting with options such as "noapic" or "nolapic" or "noapm" or all three (press F6 at the initial live CD boot menu for other options.

Assuming you get Ubuntu to install and boot, install the "kubuntu-desktop" metapackage.  That will give you the option of either kind of login; they are complementary, not mutually exclusive.  E.g.```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
You will have to choose whether gdm or kdm is the manager for the login screen.  But you can switch back and forth as you please.

---

### Post by ryansheakennedy on 2008-11-26
What do those commands do?

---

### Post by ryansheakennedy on 2008-11-27
well i used noapic and noalpic and it ra. Its up and running now. While installing it had a few weird problems:

buffering SR0 I/O Error
black screen white text save one letter that was pink.
error informing kernel of disc size change. Device or resource busy


Any ideas about these? Please tell me it doesn't mean my hardware is failing

=P

---

### Post by lemming465 on 2008-11-28
The symptoms you describe aren't reassuring, but if the install otherwise appeared to run to completion normally and the resulting systems boots and runs, I expect you are OK.  Dire errors would be things like invalid package checksums or disk write errors.

The boot time arguments change the way the linux kernel does hardware initialization.  Some hardware is buggier than others, and sometims the BIOS and firmware vendors don't properly implement the industry specifications, and only test with windows.  If you can avoid tripping over the bugs, you can sometimes manage to use the hardware anyway.

*apt-get* is a command line front end to the underlying *dpkg* tools used to manage the debian-style packages Ubuntu uses for software management.  *apt-get update* checks to see if you have the most recent package lists from the repositories you have enabled in /etc/apt/sources.list.  *apt-get install* does what it sounds like; it installs a new package, plus any required dependent packages it specifies as needing to run properly.  It will used cached copies from /var/cache/apt if available, otherwise it will download them.  You can get the same effect from GUI front-ends to dpkg such as *synaptic*.

*kubuntu-desktop* is a "metapackage", a package with no contents of its own, that exists solely to depend on a coordinated set of other packages.  Another example is "build-essentials".  There are also "ubuntu-desktop" and "xubuntu-desktop" meta-packages.  The purpose of these is to pull in the complete set of libraries and applications you need to run the Gnome, Xfce, or KDE display managers, desktops, and utilities.  If you install the "kubuntu-desktop" package, run KDM as the display manager, and do a KDE login, it's just like you had installed Kubuntu in the first place.  All the Ubuntu variants share the same back-end repositories with roughly 18,000 packages; it's just a question of which subset you have installed and what you choose to run.

There is documentation on what kernel options are available,  man pages for all of the commands, and descriptive text for all of the packages.  Depending on how much unix, linux, or computer science background you have, they will make more or less sense.

---

### Post by icanfly0307 on 2008-11-28
Did you burn the CD at low speed? Most of the freezes that occur are due to bad burns and such. Also, if you enable the acpi=off and other options, you will have to get rid of them in your actual installation; otherwise, your computer won't shutdown completely!!! This is simple enough and you can fix it after your installation.

---

