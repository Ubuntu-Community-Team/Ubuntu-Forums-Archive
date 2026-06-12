---
title: "Can't log in as Edubuntu client"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by hsweet on 2007-03-05
Finally got Edubuntu server installed on new hardware (only took a week) but I can't log in as a client.  The client finds an address, gets the kernel and enough of gnome to give me a proper log in screen.  So I know that dhcp, tftp and all that is working. 

When I try to log in on the client it won't let me in and goes back to the log in screen after a few seconds.

I noticed these gconfd errors.

Mar  5 08:31:07 edubuntu gconfd (tech-9937): starting (version 2.16.0), pid 9937 user 'tech'
Mar  5 08:31:07 edubuntu gconfd (tech-9937): Failed to get lock for daemon, exiting: Failed to lock '/tmp/gconfd-tech/lock/ior': probably another process has the lock, or your operating system has NFS file locking misconfigured (Resource temporarily unavailable)

Any ideas.. 

thanks

---

### Post by hsweet on 2007-03-06
I found the problem.  The locked file contained the ssh key which was not valid because Ubuntu was installed by removing the hard drive and moving it back into the original box.  That was done as a workaround for a hardware problem with a new Intel board.  Resetting the key solved the problem.

---

