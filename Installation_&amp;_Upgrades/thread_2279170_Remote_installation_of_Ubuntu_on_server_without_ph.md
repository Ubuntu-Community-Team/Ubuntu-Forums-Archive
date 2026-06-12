---
title: "Remote installation of Ubuntu on server without physical access"
date: 2015-05-21
forum: Installation &amp; Upgrades
---

### Post by Cogito² on 2015-05-21
This may be crazy, but it seems theoretically possible. I've basically decided it's unrealistic, but I'd like to know if anyone's ever managed to do something like this.

I have a remove server which will be hard to access physically. It was set up by others with an Ubuntu 12.04 server edition, but they seem to have messed with things enough that it would probably be easier just to totally reinstall (not upgrade) to Ubuntu 14.04. I was trying to figure out how to do this remotely.

I don't think I have serial access to grub. My idea was to copy the 14.04 image the server's non-attached hard drive (the one that will not be the boot drive). Then I would set grub to boot off of that iso image. Then I would boot into a live version which I would use to set things up.

Problems:

1) How will I get the live version to have ssh access set up from the get go? Otherwise how can I continue? How will I have access to the installer from the outside at all?
2) How will I ensure that after it's installed I will have access to the server on the next reboot?

I guess if I could set up the install to go from start to finish without asking any questions, and then for it to reboot by itself, then I'd be good, but I'm not sure if that's possible.


Caveats:

1) Of course this is pretty crazy since a lot of different mistakes could render the whole thing totally unusable...


Thoughts?

---

### Post by TheFu on 2015-05-21
You need "console" access.  

Many servers provide this through DRAC/RIBLO/IPMI hardware. With this hardware, it is possible for someone to put a DVD in the optical drive and you can access the box remotely, power it up, have complete console and power control to load the OS. Simple.  Just need a HW guy to put the DVD media into the tray.

So - the question is does your server have this OOB connection to make this a trivial thing?  The extremely low-end servers don't, but it is a common option for servers over $500.

---

