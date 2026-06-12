---
title: "Nvidia driver problem ( again )"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by shawfield on 2008-11-03
Apologies - I posted this on a 'solved' thread a few mins ago, so am now reposting to a new message.

Hi

I have Nvidia driver problems after upgrading to Intrepid.

I have the GEforce 6100 graphics on the motherboard, with an AMD Athlon x2 .

After installing & booting, I got only 640x480 resolution & attempting to invoke the Nvidia driver via preferences, showed me that the nvidia driver was disabled. It would not allow me to enable it.

After 5 or 6 reboots, my machine managed to find a driver to use ( clever machine ! ) & I now have 1440 x 900 resolution, but clearly not with an Nvidia driver, as the quality on screen is poor & text is barely readable.

Tried to use the Ubuntu update which tells me there are 652 updates available, & its only possible to do a partial upgrade ; but when I try to install them, I am told that "an upgrade from intrepid to Hardy is not supported with this tool"

So - bottom line - Do I need to re-try my Intrpid upgrade or can I update via the command line with a specific nvidia driver update request ?

Many Thanks

---

### Post by tuxxy on 2008-11-03
What driver version are you currently using and what was you using when it was fine v173?

---

### Post by shawfield on 2008-11-03
Good question - How do I find out ?

the Ubuntu Hardware drivers app simply tells me that 'no proprietory drivers are in use on this system'

Beneath that message it informs me that "Nvidia accelerated graphics driver ( latest cards )' is available. But it will not let me tick the 'enable' box.

No doubt there will be some other way of querying which driver is in use. A terminal command maybe ?

Thanks again

---

### Post by shawfield on 2008-11-03
I've checked on Nvidia's website & its 173 that is correct one for my Graphics chipset.

I've been unable to figure out how to download & run that without using synaptic package manager. I saw references to 'aptitude' & ran that from the command line. There were no Nvida drivers there. There are none in the upgrade manager either.

---

