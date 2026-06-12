---
title: "Any hopes of rescue?"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by mo0nl0rd on 2007-12-16
i had a pretty nicely working installation of ubuntu. however i needed to reposition the / partition so i copied everything on / to another oartition using a rescue cd and the editing menu.lst to the new partition

well everything almost worked and my ubntu boots successfully except that all the permission have quite obviously changed. so i was trying to fix ubuntu one component at a time T_T..  managed to get xsession and gnomepanels working.
however i stll havent been unable to get the network working yet with the message
localhost dhcdbd: message_handler: message handler not
found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
in var/log/messages

well a fix to this would be welcome but i am sure that this would be just one of the many faulty components that i have now.. so is there a way to reinstall all the packages forcefully all over so that i donot need to actually reinstall? or to revert most files to their default ownerships/permisions??

i know better to use rsync next time now >_<

---

### Post by dixonp on 2007-12-18
For future reference, when doing this kind of manual procedure, you need to: preserve not only file permissions (+setuid bits +sticky bits) but also ownership, handle nested filesystems independently (e.g. /var not on /), skip dynamic filesystems (/dev, /proc, /sys), copy the static /dev normally hidden by udev/devfs (mount --bind / /myotherroot, then copy /myotherroot/dev), update the new /etc/fstab, and update your bootloader config.

This is something I have to do once in a while, but I wouldn't recommend you to try to attempt it if you are not an experienced sysadmin.

Now you are probably not going to like what I am going to say but: the easiest way to fix this mess is to back up your personal data, and reinstall Ubuntu. Your system files probably have incorrect perms/owners throughout your entire filesystem (which might lead to security issues if users can write to files they are not supposed to write to), and your /dev is probably a snapshot of your udev/devfs state... The only way to restore  correct perms and ownership would be to do a clean install of Ubuntu somewhere, and write a shell script that compare this clean system with yours and fix things that differ...

---

