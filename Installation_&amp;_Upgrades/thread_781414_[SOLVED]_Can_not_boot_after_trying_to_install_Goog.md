---
title: "[SOLVED] Can not boot after trying to install Google Earth"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by glowplug61 on 2008-05-04
I have just performed a fresh installation (except for the /home partition) of Hardy Heron.
AMD64 4400+ nvidia 6800 gt.

Post O.S. installs include netbeans 6.01 (Sun package with glassfish etc not Synaptic), MySQL 5 (Q.A + Admin from Synaptic) and a few other things that should not relate to the following.

Google Earth (downloaded from Google) install failed so I googled on the error message…
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
and found…
[http://groups.google.com/group/earth-linux/browse_thread/thread/d7bb6e1608cbf5fd](http://groups.google.com/group/earth-linux/browse_thread/thread/d7bb6e1608cbf5fd)

Installing ia32-libs FROM Synaptic, it failed with quite a lot of errors in the result list.
I apologize for not taking note of those however most of the text was out of scroll view and the system locked up.

Ctrl+Alt+F1, clicking etc did nothing so I finally resorted to the reset button.

Regular reboot locks up soon enough to freeze the progress bar.
Recovery mode stops at…

[  44.570150] Kernel; panic – not syncing: Attempting to kill init!

I have the ubuntu-8.04-desktop-amd64.iso burned to cd, running on win32 at moment but have 20g spare on fat32 to temp any linux image, files whatever. 

 
Thanks in advance
Greg

---

### Post by glowplug61 on 2008-05-04
bump
While I don't wish to be rude I simply can not keep wasting so much time this.

Is it worth, let alone possible to use a live cd to request something like "sudo apt-get update" (repair whatever) on inactive OS.

If not I at least be able to seriously restrict download and formatting with reinstall.

My partitions are /tmp, /etc, swap /home, /, /var

---

### Post by nanog on 2008-05-04
This guide should help you fix your broken install. It is not for the new user.

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

You installed two non-ubuntu packages. This often causes problems with a new release as changes are rolling in fast and third party packages (or source code) do not get updated as often. 

In the future I recommend you use the medibuntu repository for google earth (and other nonfree packages):

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I also believe that the full java jdk is now available from the ubuntu repos. Make sure you enable universe multiverse etc.

---

### Post by glowplug61 on 2008-05-04
Double thanks for both the hd fix and Medibuntu reference.

Just to clarify I opted for the all in one Netbeans 6.01, Glassfish etc installer from Sun for cross platform convenience.
I can develop on Ubuntu then finish testing for IE7 on win32 then win64 all on one machine.

I appreciate what you are saying about non tested packages etc.
With that said the Ubuntu/synaptic solution has provided me with relatively up to date office, development and server software for almost 3 years if I remember correctly.

So again, thanks nanog and to those who make this possible.

---

### Post by glowplug61 on 2008-05-04
Okay, still get "Accessing a corrupted shared library" the same as recovery mode boot.
The fix hd thread only has sudo mount /dev/**** /media/hardy whereas I have 7 partitions for linux let alone all my ntfs and fat etc.
Just the same I have successfully mounted multi partition file systems for repair before and the 2 error messages are a bit of a coincidence.

Everything was working fine (including non synaptic netbeans) for around half a day before I tried to install Google Earth.
Even then the installer did not get off the ground - after which the system was still running fine for me to use Firefox, gnome-terminal, nautilus and a some other programs.

It was only after trying to Apply ia32-libs install through Synaptic that the system locked up and hasn't worked since.

Please don't get me wrong, I do not wish to complain I just expect that somebody will want the Synaptic ia32-libs problem drawn to their attention.

Again it is possibly unique to my hardware/driver and/or post OS installed software but I think my hardware combo is relatively common.

Okay, I'm off to reinstall, then check out Medibuntu again.

---

