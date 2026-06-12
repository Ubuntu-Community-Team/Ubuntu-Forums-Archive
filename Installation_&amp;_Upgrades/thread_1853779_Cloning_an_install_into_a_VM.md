---
title: "Cloning an install into a VM"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by Ghosthaven on 2011-10-03
I've used a home filesharing server for several months now, but
due to various bugs and issues, I've decided to go with a setup
that uses several VMs to manage the server's various functions.

This'll take me a while to setup and customize, so I'd like some
way to keep the current functionality intact while I create the
new VMs on a fresh install.

Is there some way for me to create a VM then copy the entire
contents of my Ubuntu 10.10 install into it?

Since linux uses a fairly flexible kernal, would it be possible
to simply format the VM's drive for booting and just copy the
files over?

Would installing a fresh copy of 10.10 and then overwriting it
with my fully customized files be a better option?

What's the best way to go about something like this?

Current setup:
Ubuntu 10.10
Setup as Samba, FTP, Telnet, MUD, Web, several other tasks server. Also setup as a home media PC

Intended setup:
Windows XP (works better as a home media PC) running Virtualbox
and at least 2 VMs with Ubuntu 10.10 server to perform the
various server tasks.

(Please don't hate me for going back to windows, I'm just tired
of samba and media issues. I just want the danged thing to work)

---

### Post by 2F4U on 2011-10-03
According to this post, VMWare is able to do this:

[http://community.spiceworks.com/how_to/show/483](http://community.spiceworks.com/how_to/show/483)

---

### Post by haqking on 2011-10-03
> **Ghosthaven said:**
> I've used a home filesharing server for several months now, but
due to various bugs and issues, I've decided to go with a setup
that uses several VMs to manage the server's various functions.

This'll take me a while to setup and customize, so I'd like some
way to keep the current functionality intact while I create the
new VMs on a fresh install.

Is there some way for me to create a VM then copy the entire
contents of my Ubuntu 10.10 install into it?

Since linux uses a fairly flexible kernal, would it be possible
to simply format the VM's drive for booting and just copy the
files over?

Would installing a fresh copy of 10.10 and then overwriting it
with my fully customized files be a better option?

What's the best way to go about something like this?

Current setup:
Ubuntu 10.10
Setup as Samba, FTP, Telnet, MUD, Web, several other tasks server. Also setup as a home media PC

Intended setup:
Windows XP (works better as a home media PC) running Virtualbox
and at least 2 VMs with Ubuntu 10.10 server to perform the
various server tasks.

(Please don't hate me for going back to windows, I'm just tired
of samba and media issues. I just want the danged thing to work)

Use [clonezilla]("http://www.clonezilla.org/") to take a clone of your system, clone it to a image file then fire up your VM and boot it to the clonezilla LIve CD .iso, activate your external device such as USB HDD where the image file is and clone it back into your VM.

---

