---
title: "Removing packages and dependencies"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by JoeS on 2005-08-10
I tried to remove sudo through the Synaptic Package Manager. It then told me it was going to remove the following packages:

**gdm gksu gnome-netstatus-applet gnome-system-tools sudo ubuntu-base**

I checked the summary on these packages and I don't understand why it wants to remove some of these programs.  Is Synaptic wanting to remove programs that are being used by Sudo or programs that I might need for other things?

I checked the **properties for Sudo** and found  under dependencies: 
Dependencies
Dependent packages
Provided packages

Can someone explain what these are?  I couldn't find an explanation in Synaptic. I'm new to this and don't understand much about dependencies.I don't want to remove something I might need for something else.

---

### Post by adwait on 2005-08-10
Why would you like to do a thing like that? Removing sudo could cause quite some problems, especially in Ubuntu as it doesn't have a root account, out of the box.

---

### Post by JoeS on 2005-08-11
[QUOTE=adwait]Why would you like to do a thing like that? Removing sudo could cause quite some problems, especially in Ubuntu as it doesn't have a root account, out of the box.[/QUOTE]

I enabled the root account,   What problems would there be in removing Sudo?;  if I have a root account would I still need Sudo?

I also need some help in knowing what to do with dependencies when removing and installing programs.

---

### Post by varunus on 2005-08-11
Even though you've enabled the root account, its better to keep sudo around.  Ubuntu is set up so that some of its programs are dependent on sudo; even if you can use su instead, you'll have to do some crazy apt-get stuff to force those packages to install without sudo installed.

Instead of uninstalling sudo, just do the following in a terminal:
```
su
visudo

``` 

Once in this file, press the INSERT key.  Then scroll down, and remove all of the users in it except root, so it looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

``` 

That way, no one can sudo anymore.  (Leave root there, otherwise it might break stuff.)

---

