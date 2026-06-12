---
title: "Imaging From One to Many"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by anon98sz on 2008-05-12
Alright, so normally when a new release drops I install all the packages I want, change the UUIDs to LABELs in fstab and grub, create a tar file and push it out to a bunch of machines.  I have done this countless times with 7.04 and 7.10 on i386 and x64.

However, with 8.04 when I boot up another machine with the new image there are several issues.  The first noticeable one is that DHCP does not work.  Then trying to mount drives through Nautilus returns a DBUS error.  There are other permission issues as well relating to some of the apps under Administration.

Looking through the /var/log/daemon.log the problem with DHCP is that is says permission denied executing /lib/dhcp3-client/call-dhclient-script.  Other than the terse DBUS error, I could not find anything telling me why the other things were failing.

The fix is to run `apt-get install --reinstall dhcp3-client dbus` and then reboot.  However soon I am going to be pushing out an image to a very large number of machines and would like to avoid this step.

So please, why is this happening?  Has tar let me down?  Is 8.04 using some sort of ACL?  I am pretty sure that I have "imaged" from one drive on a machine to another drive on the same machine without this issue.  Any insight would be appreciated.

---

### Post by anon98sz on 2008-05-13
Alright, so after poking around the system it seems like tar might actually be the issue.  I used the 'p' flag with tar but there was a mismatch between the numeric IDs of the files and the IDs in /etc/passwd.  For example files that should have belonged to 'mysql' were pointing to 'slocate' instead.

---

