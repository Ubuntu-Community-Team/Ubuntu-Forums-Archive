---
title: "Attempting to install dapper using debootstrap"
date: 2006-02-27
forum: Installation &amp; Upgrades
---

### Post by themindlessmatt on 2006-02-27
Am attempting to install dapper onto a spare partition from breezy using debootstap, and the instructions in the wiki [https://wiki.ubuntu.com/Installation/FromKnoppix]("https://wiki.ubuntu.com/Installation/FromKnoppix")

Am up to the stage where running /usr/sbin/base-config.

However, it does not exist. Indeed the base-config package is not installed.

Installation using apt-get install base-config results in the removal of other packages. Proceeding anyway still does not provide base-config on the system.

Downloading the deb from archive.ubuntu.com/pool/ and forcing installation (after re-installing the removed packages) provides /usr/sbin/base-config. Running /usr/sbin/base-config new results in Terminated.

Any ideas.

Matt

---

### Post by themindlessmatt on 2006-02-27
Ok... looking on packages.ubuntu.com tells me that base-config is depreciated for dapper.

Have manually added my self as a user, altered grub, and can boot into my minimal dapper installation. Currently doing apt-get install ubuntu-desktop.

What is the new set-up system for dapper? How will i add my new user to the right groups etc?

Anyone?

Matt

---

### Post by CallMeAl on 2006-05-31
Hi,

I typically hate replying to a question with, "I'm having the same problem', but unfortunately, I'm having the same problem.

i've seen this question asked in two different threads, but no answer as of yet, so just thought I would give it a bump in hopes of some feedback.

--Al

---

### Post by garyng on 2006-05-31
you can do what base-config does manually, It kinds of :

1. set the time zone stuff
2. adduser and passwd settings
3. apt repository location
4. create the first system user
5. dselect task(desktop/server etc.)

I think deprecating it is a bad move, making debian more like windows where without actually booting and install, you can't have a nicely setup system, the beauty of debootstrap(up to sarge).

EDIT:

BTW, I faintly remember I need to create something(host file?) in /etc to make the deprecated base-config works. It is just a shell script so you can trace it if you want.

---

### Post by ubuntu_demon on 2006-06-03
Is there a way to install Dapper (from a messed up Dapper installation) using debootstrap without being able to boot from cd-rom ?

---

