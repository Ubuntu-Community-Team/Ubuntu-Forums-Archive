---
title: "Few questions about Alternate CD"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Zombithium on 2006-06-04
Hi,

I am currently on Breezy and am going to upgrade to Dapper. I have downloaded the alternate CD (because my broadband connection is unreliable). 
Just wanted to know if there are any precautions to be taken when installing from Alternate CD. And whats the general upgrade procedure to be followed for that ? 
I have seen many posts regarding dist-upgrade using apt and downloading files from the web but didn't find much information on how to use the alternate CD.
Also i should write the iso image downloaded from the web (ubuntu-6.06-alternate-i386.iso) as the normal disk image - right?

thanks.

---

### Post by llamakc on 2006-06-04
Yep, just burn it like you would any iso. You can then add it as a repository with `sudo apt-cdrom add` (I believe). You could do this with the regular install iso image also.

---

### Post by llamakc on 2006-06-04
Heck, you don't even have to burn it. Just mount it;

mount -o loop /path/to/install.iso /media/temporaryapt

(create whatever storage dir you want to mount at)

And add a line to sources.list:

deb file://media/temporaryapt dapper main contrib universe multiverse

and apt-get update should pick up the repository. I'd probably comment out any breezy entries in sources.list too.

I _think_ this would work. Somebody smarter should come along.

---

### Post by Zombithium on 2006-06-04
Well you have saved me a few bucks but have send me to a confused state now :-)
I'll wait for some more post just to confirm if that will work.
I wonder why this point has not been listed at [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)
But it seems to be a very valid one.
More Help Please.

---

