---
title: "Recovery Partitions"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by Jonny87 on 2013-09-06
I'm planing to do OEM installs of Ubuntu and would like to set up a recovery partition to restore the system back to the oem state it was when I gave it to them. So that if the user needs to they can easily restore their system back to the way it was. Now I'll have a image anyway and would be able to restore it for them but I'd like to make it possible for the user to do it with out having to bring it back to me.

I was thinking of creating a partition with something like Redo in it. But I'd like some thing with less options if possible. Or having a minimal Ubuntu install that would instantly run a script for the user run through.

Conditions;
Must be very User friendly, alot of my customers aren't very computer savy.
Quick and simple to recover to original state.
Gui preferred. 

Has any one got any experience in this? or any ideas. At the moment I'm thinking I'll go with Redo.

---

### Post by sudodus on 2013-09-07
I suggest that you try the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971"), that can manage that task using compressed tar archives, ***tarballs***.

[SIZE=3]**Typical cases for the One Button Installer**[/SIZE]

**Tool that is easy to use and just works**

 The normal linux installers that come with iso files are complicated to  use or freeze during the installation process, and you want a tool that  is easier to use and just works. 
 
**Replace Windows XP**

 Replace Windows XP because you want the computer to work faster or  smoother with an Ubuntu based linux operating system, or at the end of  life in April 2014, when there will be no more security updates for  Windows XP. 
 
[COLOR=#008000]**Backup**[/COLOR]

 You want a simple method to backup (and restore) your whole installed  linux system. The One Button Installer combines installation, backup and  restore in one set of tools. 
 
**Your own portable Ubuntu based linux system**

 You want to make your own linux system portable and port it to a USB  pendrive or to be installed in another computer to be used by yourself,  or to be uploaded to the internet for sharing with other people. The One  Button Installer can do it in a simpler way than to remaster the code  and make an own iso file.

---

### Post by Jonny87 on 2013-09-07
Thanks I'll keep in mind, though I'm worried it might be a little complicated and the text screen may scare some users.

---

### Post by sudodus on 2013-09-07
***Try it!*** If it is 'a little complicated' I need to improve it. Because it is made to be simple. Right now it would reside in another mass storage device, typically a USB pendrive.

But it would be fairly easy to make a simpler version to put into a recovery partition, and from there have only three choices

- Backup (make a tarball)
- Restore system from a tarball (your original one or a newer one made by the user)
- Exit to the bash shell and/or maybe start a graphical desktop environment, if you like

and to keep fixed partition numbers, for example

/dev/sda1: restore (and probably also boot)
/dev/sda5: root file system
/dev/sda6: swap

---

