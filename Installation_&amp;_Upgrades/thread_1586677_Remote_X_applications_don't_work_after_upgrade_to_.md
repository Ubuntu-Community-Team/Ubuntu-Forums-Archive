---
title: "Remote X applications don't work after upgrade to Lucid (Ubuntu 10.04)"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by aajax on 2010-10-02
I upgraded my Ubuntu 8.04 (Hardy) system to 10.04 (Lucid) and my remote X applications no longer work.  The problem seems to pertain to Xauthority.  When the remote X client attempts to access the X server on Lucid it receives an error indicating that there is no matching MIT Magic Cookie (hereafter cookie) for the display.  It turns out that this is true.  I'm of the belief that the subject cookie should be generated for my display when the X session is started on Lucid.  I thought this was being done by GDM when I logged on.  However, $HOME/.Xauthority contains only 1 cookie which is for the display identified as "Pluto/Unix:0" (Pluto is the name of the host).  I'm expecting a cookie for a display identified as "Pluto.my.test:0" where "my.test" is the domain name for my network.  This is the display name that is used on a remote host.

Other strange findings include the following:
- There is no file named /etc/gdm/gdm.conf only /etc/gdm/gdm.conf.dpkg-bak
- There is a file /etc/gdm/custom.conf which contains a statement "DisallowTCP=false".  I suspect the upgrade was able to figure out that I was permitting remote X sessions and therefore created this statement.  Possibly this also explains why I have this file.
- Unlike the predecessor system "sudo gdmsetup" doesn't allow me to do anything that looks like it will help configure my system for remote X sessions.  Possibly the absence of gdm.conf is affecting the behavior of gdmsetup.
- The gdm man page discusses the purpose of various config files but doesn't mention custom.conf
- When I ping to pluto.my.test I receive replies from 127.0.1.1.  What is that?  My localhost is 127.0.0.1.  Why don't I receive replies from the network interface defined in my name server, which is what happens on other Ubuntu systems I'm running.
- If I run "nslookup pluto.my.test" I receive the proper network address for my host.

---

