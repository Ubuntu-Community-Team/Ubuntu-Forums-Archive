---
title: "newbie help with CVS &amp; Eclipse from workstation"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by kerry165 on 2006-05-16
Can someone give me guidance?

I am having to learn the Eclipse environment on a Windows PC. Going through the PC tutorial now. Got to section "Team CVS Tutorial".

As I have a computer with Ubuntu on it and I can see from Synaptic that I can have CVS I thought I would try and set it up as a CVS repository.
Now I am struggling.
Have installed CVS.
[http://cvsbook.red-bean.com/cvsbook.html#](http://cvsbook.red-bean.com/cvsbook.html#)
is helping me with the set up. It suggests modifying the /etc/services file and the inetd.conf file.
The inetd script doesn't do anything and has text init saying that the xinetd.conf is superceding it. Do I just put the same lines into Xinetd.conf?

I have done the mods for both ext & pserver but unless I can kick start the services I am stuffed? 

when I try and connect using eclipse (pserver) I get the error
Connection refused

and with the default "ext" I get the error
I/O exception occurred create process: ssh 192.168.0.150 -l testusr cvs server error=2

testusr is the user I use to login using remote Xwin (via cygwin)

Kerry

---

### Post by kerry165 on 2006-05-17
I have now found that the default settings for the CVS (1.12.9) using the package manager that Eclipse 3.1 on the PC can connect to it happily if I select connection type "extssh". I have had two Windows based PC's (2K & XP) each running Eclipse 3.1 to go through the CVS "Working with another user" tutorial.

I then thought. Great I should be able to also put CVS on my Ubuntu box (the same one as the CVS is installed on) and also see the repository. Wrong!

Eclipse (base, sdk ecj and jdt - can't remember what was dependent and what was chosen) was installed onto the unit. It starts beautifully and runs as a stand-alone.

When I try to create a CVS entry (pserver & ext fail) I am using connection type extssh (as with Windows) Host is localhost (also tried 127.0.0.1 and its own IP address) and default port.

If I tell the connection to "refresh Branches" no faults actually appear on screen but if I try and see what the children of "HEAD" actually are I get the dialog box saying:
An internal error occurred during: "Fetching children of HEAD".

If I try to import a project from the CVS repository. No errors are shown but no modules are shown in the "Select Module" box even though 3 are shown in the Windows equivalent.

Anyone now why my Ubuntu Eclipse app cannot see the Ubuntu CVS?

Kerry

---

### Post by curtisf14 on 2006-09-08
You might want to take a look at [this post]("http://ubuntuforums.org/showthread.php?t=206209").  It should lead you in the right direction.  Hope this helps!

---

