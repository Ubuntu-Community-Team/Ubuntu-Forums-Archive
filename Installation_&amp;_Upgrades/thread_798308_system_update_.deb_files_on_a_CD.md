---
title: "system update .deb files on a CD?"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by sstewart207 on 2008-05-18
is it possible that you could download the .deb files that are in a system update to a CD or USB drive so that you have the latest updates


I am talking about the red exclamation mark on the top panel of the screen that says new updates are available.


I was thinking I could just use a different computer to download the update packages then transfer them to my  ubuntu pc because I have a very slow dial-up connection. But I haven't been able to find a way that you can externally download the packages (http without a package manager)

---

### Post by Partyboi2 on 2008-05-18
You could try something like [[COLOR=Blue]nonetdebs[/COLOR]]("http://nonetdebs.unixpod.com/")
or you could use the "generate package download script" in synaptic package manager to create a script of the updates you need then run the script on the machine that you plan to download the updates.

Edit: [[COLOR=Blue]Here[/COLOR]]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/") is a link to how to make the "generate package manager script" If the machine you are planning to use to download from only has windows not ubuntu you should be able to retrieve the upgrades using a ubuntu live cd.

---

### Post by teaker1s on 2008-05-18
link in my signature to download debs

then add cd as source in synaptic

---

### Post by sstewart207 on 2008-05-19
thanks guys but is there a way you can get the latest updates without going through catagories.

---

### Post by iaculallad on 2008-05-19
There could be a way like using AptOnCD, but this of course requires you to have another PC installed with Ubuntu updated on the net so AptOnCD could copy the update files saved in /var/cache/apt/archives and create an archive readily available for restoration in your target PC.

---

### Post by ZIS on 2008-05-29
Thanks

---

### Post by rogerdean on 2008-05-31
aptoncd is broken in hardy just now - there's a fix coming. in the meantime you can install the unreleased fix from

[http://www.cypherbios.org/aptoncd/pa...buntu1_all.deb](http://www.cypherbios.org/aptoncd/pa...buntu1_all.deb)

---

