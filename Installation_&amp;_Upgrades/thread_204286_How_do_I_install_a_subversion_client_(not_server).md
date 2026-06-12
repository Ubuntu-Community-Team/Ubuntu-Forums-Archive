---
title: "How do I install a subversion client (not server)"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by Dan Hinojosa on 2006-06-26
I need to install the subversion client, and I did apt query and it wasn't on the list nor was it on package install.  Any hints.

Your help is appreciated.
Thanks 
Danno

---

### Post by scxtt on 2006-06-26
do you have the "Development" repo. enabled? -- i can see subversion in synaptic ...

---

### Post by markmark on 2006-06-26
I'm pretty sure you just install the subversion package. It contains the client, and no repositories or anything will be set up unless you choose to do it manually.

[edit]svn is in Universe I think, you'll need to enable that.

---

### Post by Dan Hinojosa on 2006-06-26
[QUOTE=scxtt]do you have the "Development" repo. enabled? -- i can see subversion in synaptic ...[/QUOTE]

Thanks, I needed an update, took a while though for Ubuntu to tell me. ;)

---

### Post by kvdbreem on 2006-08-05
Yeah, I'd have to agree with Dan here.  Looks like somehting like apt-get install subversion will just fetch both client and server.  Of course, if you're looking to do editing of repoes on the same machine then you'll need both.  As to stand-alone clients, looks like you need to get one of the graphical ones.  

In my home coding factory I'm looking to set up a SVN server on VMWare and then use SubClipse plugin to access it and keep track of code.  I'd put the repo on the same machine, but I like the practice of doing it across multiple machines.

---

