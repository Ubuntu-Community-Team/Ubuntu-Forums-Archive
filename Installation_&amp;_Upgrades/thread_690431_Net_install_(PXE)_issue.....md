---
title: "Net install (PXE) issue...."
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Shrek X on 2008-02-07
Hi all...

I am hopeful one of you gurus can give me a hand. 

I am using PXE to do a netboot/netinstall.  I have the PXE server up and running fine using the guide here
[http://home.allegiance.tv/~joem298/](http://home.allegiance.tv/~joem298/)


I can boot into the system I an trying to install to, and it starts the process including net detect.  

I am using the distro setup found here
[http://ubuntuforums.org/showthread.p...nstall+netboot](http://ubuntuforums.org/showthread.p...nstall+netboot)


Everything starts up, and the install begins, going through net, keyboard, local, etc.  

When the system starts to try and find a mirror, I select the us (I have tried others).  It returns us.archive.ubuntu.com.  I accept that....

It then asks for proxy, I choose blank (the default)

After I continue through this I get

Bad archive mirror
The specified ubuntu archive mirrors is either not available or does not have a valid release file on it.  


any help?

---

### Post by Shrek X on 2008-02-07
Not really sure what I did, but I tried again (for the 40th time it seems), and it worked.  I dont think I changed any settings....

maybe it was having trouble connecting, but it looks like it is working

---

### Post by Shrek X on 2008-02-07
arrrggg....

the install was started, then froze, now back at square 1 trying to get this going.... :(

frustrating.

---

### Post by Shrek X on 2008-02-07
sorry for posting on my own thread, but I think I figured it out and others may find it useful

After you start your install (going to select keyboard and stuff, but before net detect), shut down your PXE server, this seems to be giving conflicting DHCP information to the unit your installing to.

And while the install is going, at the "select and install software" screen, apparently it is not unusual to have it sit at 6% for a couple of hours.

---

