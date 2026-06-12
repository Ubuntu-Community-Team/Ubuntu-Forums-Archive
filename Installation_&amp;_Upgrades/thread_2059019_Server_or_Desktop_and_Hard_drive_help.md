---
title: "Server or Desktop and Hard drive help"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by np123 on 2012-09-17
Hi there,

I have a HP microserver at home, and im getting a little miffed by WHS 2011 not playing nicely.

So im trying to decide what way is best to install Ubuntu for my server.

I want GUI. I know you dont advise it but I want to be able to VNC on to the desktop at times through an SSH tunnel. 

So, is it better to install server edition and install a GUI which needs to start at each boot....

or,

Is it better to go with desktop and then install the server bits like SSH etc on top.

Also, my machine has 1 250GB HDD, a 2 TB HDD, and a 1TB HDD.

The server will be used for downloading media and for media storage and streaming around the home.

Anyone have any idea of the best way to go about the install? Is it possible to mount all the drives via the installer?

Many thanks, you guys rock! :guitar:

---

### Post by darkod on 2012-09-17
I would say go with Server OS + lightweight GUI. Not the ubuntu desktop GUI, some other smaller GUI. Google around for options and look at the screenshots so you can decide. You can go with the ubuntu desktop GUI if you want to also.

The Desktop OS will not install only the GUI, it will install all sorts of things that you will never run on a server, like Libre Office, etc. Are you going to do document editing on a server? Doubt it...

Yes, you can make mount points for all disks during the install, just decide what you want them to be. You can even "invent" non existing mount point and it will create them for you.

For example, you can have /data1 and /data2 for the big disks.

---

