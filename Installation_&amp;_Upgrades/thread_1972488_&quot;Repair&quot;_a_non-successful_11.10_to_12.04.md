---
title: "&quot;Repair&quot; a non-successful 11.10 to 12.04 upgrade"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by kabeza on 2012-05-03
Hi
I've done the upgrade from 11.10 to 12.04 using alternate cdrom. Upgrade went fine until "installer" tried to reboot but got the background and mouse pointer only, so after some time of no activity at all, I decided to restart PC manually.

After reboot, all went bad, I had to do a repair system from cd, reinstall grub from rescue mode, repair damaged packages, etc. Now Ubuntu 12.04 starts **"fine"** except

- System settings doesn't run, shows->closes
- Change background applet shows then closes
- Firefox (etc) run with a default gnome theme, ugly
- When I insert 12.04 cdrom it asks for "partial upgrade"

[B]What should I try to fix all these problems, without reinstalling Ubuntu from scratch and loosing any /home (etc) of my files? Is there a way? 
[/B]
Thanks

---

### Post by mörgæs on 2012-05-03
A backup and a reinstall does not take that long. You are likely to spend much longer time trying to fix a damaged system.

---

### Post by kabeza on 2012-05-03
> **mörgæs said:**
> A backup and a reinstall does not take that long. You are likely to spend much longer time trying to fix a damaged system.

The problem is that I will loose much more time re-configuring and restoring the thunderbird files, filezilla, and all the apps I use :(

---

### Post by 2ta8gdfte on 2012-05-03
> **kabeza said:**
> The problem is that I will loose much more time re-configuring and restoring the thunderbird files, filezilla, and all the apps I use :(

 You can save the Thunderbird folder and back up other things. You can run a command like this to have a list of everything installed for re-installation. 
  
Code: dpkg --get-selections > installed-software 
 
And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,  

Code: dpkg --set-selections < installed-software 
 
followed by Code: dselect  

Save the extras repos you have installed and put them in there on the fresh install  run the dpkg and dselect and have a cup oh coffee.  You could also just save home so you have access to stuff there besides Thunderbird.

---

### Post by rigelstar on 2012-05-03
> **kabeza said:**
> The problem is that I will loose much more time re-configuring and restoring the thunderbird files, filezilla, and all the apps I use :(

It is always a good idea to make a separate partition for your /home user directory.  If you do when you install from scratch you can simply not format that partition and set that as your home directory and all is good.  I have much of the linux system set in separate partitions for this reason.  It comes in handy when in a bind.

---

### Post by kabeza on 2012-05-04
Thanks for the suggestions. I've finally decided to backup and do a clean install again

Hope Ubuntu upgrade process to be less painful in future. I can't believe I could do an upgrade from 11.10 clean install to 12.04. Seem this version was released with some problems not solved

---

