---
title: "Xubuntu = AMAZING! but - cannot see other machines on my net"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by jstevans on 2008-11-24
Hello,

I've been trying for weeks to get a small Linux distro running and booting on my beloved Sony 505 mini notebook by placing its HD into one of my desktop machines and configuring it there (the Sony cannot netboot and has no CD or floppy - both lost long ago) .  I've tried half a dozen distros, many would not even boot in the desktop I'm using to host the laptop's drive, others were painful to install to the HD or, even after all the annoyance, never could be convinced to boot properly from the HD.  Xubuntu 8.10 booted, installed with incredible ease, automatically connected to the Internet via my home network, etc.  Absolutely amazing!  Thanks to all who made this possible.  If Linux is ever going to gain significant end-user market share this is a model of how to get there.

However, it's only 99% perfect.  Well, maybe 98%.  I had, and still have, some networking issues.

Initially I could not figure out how to make the Xubuntu machine visible to my Windows PCs.  The Xubuntu instructions say I can change the host name by using "Applications &#8594; System &#8594; Network."  But, there's no such command in Xubuntu 8.1.0.  So, I started hunting for a likely candidate.

It turns out that "Applications &#8594; System &#8594; Shared Folders" produced an alert saying I needed to install Samba and NFS.  So, I told it to go ahead and do so.  I also used the "Shared Folders" GUI to rename the workgroup.  Well, all that didn't enable my Windows machines to see the Xubuntu one or it to see the Windows machines.  So, making a guess, I rebooted and now my Windows PCs can see the Xubuntu one - solid progress - yay.

However, I still cannot figure out how to see the Windows machines from the Xubuntu one.

The "File System" window does not even hint at there being machines out on my network.  It does show (in the sidebar) the folder on the Xubuntu machine that I have shared and which can be seen by my Windows machines.

So, with that background, can anyone help me figure out how to see the Windows machines from my shiny new Xubuntu one?

Thanks.

---

### Post by LDRoamer on 2008-11-24
This is not much help but I have exactly the same problem with Ubuntu 8.04. My windows boxes can see shared folders on the ubuntu machine but ubuntu cannot see the shared folders on the windows machine. When I say that what I mean is that it appears that nautilus cannot see the folders. I have installed Gnome Commander and it does see all the share folders on my windows boxes.

There is an extensive thread elsewhere on Ubuntu 8.10 and similar problems to yours that you might want to check out.

---

### Post by jstevans on 2008-11-24
Thanks for the kind reply.  A couple months ago I spent weeks trying to get Ubuntu and a couple other heavyweight distros running on another machine - just for my own education.  After a couple dozen postings on forums and getting many suggestions I had to give up.  It just wasn't worth the effort.  I'm not striving for a graduate degree in Linux here, I just want a working machine so I can become familiar with it.

I was stunned at how easily and quickly Xubuntu got up and running.  It is the first Linux distro I've tried that automatically connected me to the Internet through my LAN.  All the others made me go through a manual configure - not one of which was obvious or easy.

I was likewise surprised at how easy it was in Xubuntu to enable my Windows machines to see it - in past experiences I was told to get into Terminal, execute numerous commands to turn on Samba and make it turn on with every reboot.  Yikes!!  Such a high level of hassle.  I understand having options and security and all but at least make it easy for the user by providing a check list menu of "Things you might want to turn on" and then automatically doing so.

Thanks again for your reply.  Here's hoping there's a wizard out there somewhere who can get this fixed for both of us.

Jay

---

