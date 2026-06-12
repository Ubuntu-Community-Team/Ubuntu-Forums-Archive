---
title: "disabling packages from update-manager"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by Klegger on 2010-06-27
Hello, 

Update-manager starts up every time I log in to my 10.04 installation. This is fine. What is not fine is that every time it starts, it asks me if I want to upgrade any of 50 CUPS-related packages. This is severely annoying, because I don't have a printer. 

  Now, given the interface provided, if I wanted to actually let it install the things I do need, I would first have to manually unselect all those CUPS packages, clearly too much work for nothing.  

   How may I tell the upgrade manager never to bother me again about CUPS? More generally, how do I tell it that certain packages are of no use to me? 

    Thanks,   

Christian

---

### Post by kaibob on 2010-06-28
You can lock the version of a particular package by opening the Synaptic Package Manager and by selecting that particular package and by selecting "Package>Lock Version" from the top menu. If a package is of no use to you then you can simply uninstall that package.

---

### Post by Klegger on 2010-06-28
Thanks for the reply. 

I had tried using apt-get to remove 'cups', but evidently that wasn't enough. I went into synaptic, and marked many cups-related packages for removal (carefully leaving in place the ones which were needed by other desired packages) and removed them. Things seem a little better now. 

One question I've had for a long time, which remains: how do I prevent an upgrade from installing things I don't need or want? The last time I upgraded from 9.10 to 10.04, a lot of packages were removed, including some that I used regularly (eg, galeon), and many, many new packages were installed that I have nothing to do with. Someone told me I can control upgrades, but I never saw the button that is supposed to open up a menu to allow me to customize the upgrade. Does such a button exist? 

Thanks.

---

