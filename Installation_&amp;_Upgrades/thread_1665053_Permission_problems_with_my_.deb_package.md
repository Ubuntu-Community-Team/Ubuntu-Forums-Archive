---
title: "Permission problems with my .deb package"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by MrQuan on 2011-01-11
I've been working at creating a debian package installer (.DEB) for a Java application using these instructions as a guide: [http://www.offbyzero.com/resources/java_deb_ubuntu](http://www.offbyzero.com/resources/java_deb_ubuntu)

I've get as far as testing the deb when I'm having some trouble.  I've created a .deb, installed it, checked it put everything in the right place (it does), and then try to run it - but I get a permission error.

I've looked at the main installation path in /usr/share/APP-TITLE/.... and the owner is set as root with limited permissions and no execute permissions for the java file.

I read somewhere in my past few hours of Googling that the .deb creator will copy the permissions for the source files.  I've checked that the source directory has the correct permissions, execute permissions, and owned by $USER, but the created .deb is still owned by root and restricted.

Can anyone please offer some advice?  I'm fairly novice to this and I'm a bit lost :confused:  I need it to install with permission for the user to execute, read, and write.

Many thanks,
MrQuan


_**EDIT:**_

I've noticed that the 'execute' permission is maintained for root user.  I was thinking of adding a chown command on all of the installed files after they are installed with the *postinst *script.  This doesn't seem like the correct method though and would be a workaround at best if it does work.  I'll report back later.... until then, any suggestions would be greatly appreciated! :)

---

### Post by MrQuan on 2011-01-12
I found that dh_fixperms in my build script was setting all the deb files to root (as it is intended to).

I was able to exclude all java executables (.JAR file) like this:
dh_fixperms -Xjar

All good! :-)

---

