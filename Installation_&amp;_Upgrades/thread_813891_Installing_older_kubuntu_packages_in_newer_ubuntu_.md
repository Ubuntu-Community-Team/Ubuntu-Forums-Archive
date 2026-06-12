---
title: "Installing older kubuntu packages in newer ubuntu installation."
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by redr on 2008-05-31
I have got cds of ubuntu 7.10 and kubuntu 6.06. 
I have ubuntu 7.10 installed on my system. I dont have broadbad connection so  I can't download and install kubuntu 7.10 packages from repos. Now, I want to install some kde tools/packages. Is it possible to use that kubuntu 6.06 cd as a repository?
I tried by adding that CD using 'apt-cdrom add'. Apparently it got added in sources.list. But whenever I search for any kde packages, it says 'Couldn't find package'. When I tried using synaptic and listing packages using origin,  Kubuntu 6.06.1/main has only few packages like g++, gcc, linux kernel headers . No kpdf, kwrite and other packages could be found.

Please help.
Thanks

---

### Post by bwhite82 on 2008-05-31
redr,

Thats because your kubuntu CD is probably a LiveCD which doesn't contain packages per-se, but rather an image that gets copied to your HD when you install. In order to use a CD as a repo, you usually have to use an 'Alternate installer' cd.

---

### Post by redr on 2008-05-31
thanks soldireboy.
is there anyway to use that image to install packages?
something like coping files from live environment to hard disk.
problem is how to select required files and their respective locations?

---

### Post by bwhite82 on 2008-05-31
Its probably possible somehow but I'm sorry I do not know the answer to that one. I think it would be a huge pain to do so. You don't have a connection at all?

---

### Post by redr on 2008-06-01
I realize it's a pain to copy those files.
It seems better option is to download packages. 
Anyway,
Thanks for your response.

---

### Post by zvacet on 2008-06-01
If you can use broadband somewhere else you can do it with [nonetdebs.]("http://nonetdebs.unixpod.com/")

---

