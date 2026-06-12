---
title: "Need Help Moving Files To New Install"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Boni Boy Blue on 2010-07-12
Hey everyone,

For the few past years what I have been doing is moving the files from my old Ubuntu install to my new one through a USB Flash drive (or more recently external hard drive). When I do it this why I have to change the owner on my new install and the file permissions. I gets a bit tiring now.

I'm preparing to upgrade from Karmic to Lucid on my grandparents computer and I was wondering if there is a way to move these files without any permissions or a more easier way to actually do it.

Thanks in advance.

---

### Post by Zimmer on 2010-07-12
> **Boni Boy Blue said:**
> Hey everyone,

... why I have to change the owner on my new install and the file permissions. I gets a bit tiring now.

I'm preparing to upgrade from Karmic to Lucid on my grandparents computer and I was wondering if there is a way to move these files without any permissions or a more easier way to actually do it.

Thanks in advance.
I can only assume you are setting the new install with a different username than the old install.
And that the  copy or move command is preserving the permissions for the original username.

Personally, I use a separate partition (not the /Home directory) to store documents etc..  and when I create a new install ensure I use the same username as before.

This means that the files I have stored can be accessed without changing permissions, ownership etc...

OTOH if you wish to copy and move files and NOT preserve their attributes I believe there should be an option to add to the cp or mv command.

Or you could use rsync (which I do) to copy your files. 

If you use the -a (archive option) you can adapt that to NOT copy the ownership and permissions attributes..

man rsync   for full details

Hope this helps :)

---

