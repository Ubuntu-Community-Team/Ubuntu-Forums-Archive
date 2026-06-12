---
title: "windows to ubuntu upgrade"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by bobo99 on 2007-05-22
Hi there, my windows installation crashed recently (never has happened with Ubuntu) and I remember the last time I installed Windows on top of Ubuntu, the grub selection screen (i'm not sure if I'm referring to the right thing, but the selection screen when you boot up, where you select the operating system) dissapears. How can I avoid losing the grub screen after I do my fresh install of windows?

bojan

---

### Post by merlinus on 2007-05-22
Even if grub disappears after reinstalling windows, here is how to restore it:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

You probably already know this, but make sure to install windows on your first partition, and don't let it use the entire disk!

Good luck!

-merlin

---

### Post by bobo99 on 2007-05-23
Thanks for the help!, now another problem from another thread that no one replied to :(

hey there, i was using the version of ubuntu prior to fiesty fawn, and after I upgraded to fiesty, my samba installation crashed. When I go to my update manager and try to update packages it says
"It is impossible to install or remove any software. please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix the issue first" which I of course did. Once i run this in the terminal i get an error,

"dpkg: error processing /var/cache/apt/archives/samba_3.0.24-2ubuntu1_i386.deb (--unpack):
subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
/var/cache/apt/archives/samba_3.0.24-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I then try and use synaptic package manger and find the "broken" package and try to remove, upgrade, or really do anything to it, and I get the message,

"E:sub-process pre-removal script returned error exit status 102"

I'm really confused I've tried removing, re-installing and such but it seems completely corrupted. Its a real pain because ubuntu wont let me install any new applications or upgrades,
thanks in advance,

bojan
Edit/Delete Message

---

