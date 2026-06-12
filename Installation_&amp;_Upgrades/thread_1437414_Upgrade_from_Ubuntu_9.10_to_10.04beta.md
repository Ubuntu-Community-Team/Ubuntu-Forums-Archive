---
title: "Upgrade from Ubuntu 9.10 to 10.04beta"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by jervin2 on 2010-03-23
When I try to upgrade from Ubuntu 9.10 to 10.04beta after typing 
update-manager -d from a window, I get:

lucid

Error During Update

A Problem occurred during the update

This is usually some sort of network problem, please check your network connection and retry.

W: Failed to fetch [http://astromirror.uchicago.edu/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://astromirror.uchicago.edu/ubuntu/dists/lucid/main/binary-i386/Packages.gz) . . .

Then a bunch more of the same, with all libraries starting with [http://astromirror.uchicago.edu/ubuntu/lucid/](http://astromirror.uchicago.edu/ubuntu/lucid/)[main/restricted/universe/multiverse]....

When I go to the website [http://astromirror.uchicago.edu/ubuntu](http://astromirror.uchicago.edu/ubuntu) , I don't see a lucid subdirectory.

Any ideas?

---

### Post by lidex on 2010-03-23
> **jervin2 said:**
> When I try to upgrade from Ubuntu 9.10 to 10.04beta after typing 
update-manager -d from a window, I get:

lucid

Error During Update

A Problem occurred during the update

This is usually some sort of network problem, please check your network connection and retry.

W: Failed to fetch [http://astromirror.uchicago.edu/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://astromirror.uchicago.edu/ubuntu/dists/lucid/main/binary-i386/Packages.gz) . . .

Then a bunch more of the same, with all libraries starting with [http://astromirror.uchicago.edu/ubuntu/lucid/](http://astromirror.uchicago.edu/ubuntu/lucid/)[main/restricted/universe/multiverse]....

When I go to the website [http://astromirror.uchicago.edu/ubuntu](http://astromirror.uchicago.edu/ubuntu) , I don't see a lucid subdirectory.

Any ideas?
Yeah, don't do it. Lucid is in beta (not stable) right now so I would not recommend upgrading your current distro (not sure you can anyway). Instead, download the beta iso and install to another partition if you want to test it. You can find it here:
[http://www.ubuntu.com/testing]("http://www.ubuntu.com/testing")

---

### Post by mkvnmtr on 2010-03-23
Sounds like you might need to change your mirror.
But like the other poster said it is not wise for you to use only 10.04. From time to time it will be broken.

---

### Post by utkarsh2012 on 2010-03-24
I upgraded from 9.10 to 10.04 and now I have lost my graphics!

When I boot my computer, I am logged in directly into my console. Now how do I revert back or solve this problem?

Thanks

---

### Post by skidaddy on 2010-03-24
try adding sudo to front of command

---

### Post by utkarsh2012 on 2010-03-24
> **skidaddy said:**
> try adding sudo to front of command

sudo in front of what command? I am logged in to the console and I need to get my GUI.

---

### Post by jervin2 on 2010-03-24
Yeah, I wrote the original message and for some reason I was using a mirror that didn't have the lucid subdirectories on their mirror.  Just had to switch it to the default one on my sources.  Figured it out about 2 minutes after entering the questions.

---

### Post by Slim Odds on 2010-03-24
> **skidaddy said:**
> try adding sudo to front of command

update-manager is GUI application. Use gksudo not sudo

---

### Post by lidex on 2010-03-24
> **utkarsh2012 said:**
> I upgraded from 9.10 to 10.04 and now I have lost my graphics!

When I boot my computer, I am logged in directly into my console. Now how do I revert back or solve this problem?

Thanks

> Ubuntu Lucid Lynx is in development, use only for testing purposes!!!

Read the first post here:
[http://ubuntuforums.org/showthread.php?t=1433791]("http://ubuntuforums.org/showthread.php?t=1433791")

---

