---
title: "update manager wants to install ant/openjdk/gcj and many others"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by Chninkel on 2010-10-26
Hello (not 100% sure to be in the appropriate section)

I'm using 9.10 (x64) and since this morning the update manager is trying to force me to install (not update) ant, ant-gcj, ant-..., openjdk (and associate packages), gcj, jruby, jetty, ... (~190Mb of new install, about 70 new packages).

Some are listed in the "important security update" (ant, openjdk) section, others in "recommended update" (libasm2-java, libregexp-java, ...) and "distribution update" (gcj, jetty, jruby, libswing, ...) (sorry, I don't know the actual English names of the sections since I use a French ubuntu).

They are all tagged with "(New install)" (which I had already seen for some kernel "update", but never for non-installed packages).

It also proposes an update to my current sun-java install (in "important security update")

I searched synaptic for pending installation, just in case I'd have accidentally checked some box, causing those packages to be needed (i.e. because of some dependency ...) and none are checked/nothing is marked as broken.

Is there any reason the update manager is trying to install these packages ?

I know I can uncheck the boxes ;-) , but still this is "unusual" (to say the least)

---

### Post by SeTsU on 2010-10-26
Same here, also on 9.10.

I wonder if it has something to do with the recent Oracle/Java drama.

---

### Post by Chninkel on 2010-10-26
> **SeTsU said:**
> I wonder if it has something to do with the recent Oracle/Java drama.
That was my first thought as well but then why install *ant* and *gcj* which are developer/compilation tools ?

---

### Post by Chninkel on 2010-10-27
a little more details ...

here is the list of the 5 sun-java-... packages  already installed that can be updated on my computer:

 sun-java-bin
 sun-java-jdk
 sun-java-jre
 sun-java-plugin
 sun-java-source

When I mark for update (in synaptic) either *bin*, *jre* or *plugin*, it wants to update *bin*, *jdk*, *jre* and *plugin* (not *source* which is not a dependency). Everything is normal so far.

Now if I mark for update either *jdk* or *source* instead, apt/synaptic wants to install *ant*, *openjdk*, *gcj* and all the others (+ *bin*, *jre* and *plugin* of course). Nothing in the properties/package informations (see [http://packages.ubuntu.com/karmic/sun-java6-jdk](http://packages.ubuntu.com/karmic/sun-java6-jdk) ) of *sun-java-jdk* indicates any dependency to these new packages. 

Besides (as noted above) updating *bin*, *jre* or *plugin* triggers update for *jdk* but _not_ the installation of the new packages (ant, gcj, openjdk, ...) 

So what I did is select sun-java-bin for update, accept to update jdk, jre and plugin as well, then update, then select sun-java-source and update it.

I guess I won't put the [solved] mark since the question remain as to why this happened in the first place ...

---

### Post by hurinth on 2010-10-31
Same over here. Furthermore, unchecking all Java related upgrades (in fear it would mess up my working Cisco java-based applications) and leaving only Firefox updates checked, resulted in all those Java packages being intalled regardless!

Can someone explain why all these packages were forcibly installed? Are we migrating from sun-java to open-java for good?

Would appreciate any light on this matter.

---

### Post by hurinth on 2010-11-02
Bump??

---

### Post by Chninkel on 2010-11-03
> **Chninkel said:**
> So what I did is select sun-java-bin for update, accept to update jdk, jre and plugin as well, then update, then select sun-java-source and update it.
I forgot to say that of course this made synaptic install **only** the 5 sun-java-... updates (which was the intended result), none of the openjdk-related packages were installed and they do not appear anymore in the update-manager (even though they are not installed and were supposedly required to update sun-java-jdk).

---

### Post by hurinth on 2010-11-03
So if you query the packages they show up uninstalled?:

dpkg -l opendj*

---

### Post by Chninkel on 2010-11-06
the command (with openjd*) returns "un" for every openjd* package (the "n" meaning "not installed")

NB: just to be clear : note that I never installed them in the first place (I never allowed the update-manager to do it) and I made the update through synaptic instead of the update-manager.

---

