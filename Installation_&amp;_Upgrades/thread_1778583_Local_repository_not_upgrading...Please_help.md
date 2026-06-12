---
title: "Local repository not upgrading...Please help"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by dannelb on 2011-06-09
Hello,

The school where my wife works has a local repository, which makes upgrading really easy (considering I live in Ethiopia and bandwidth is limited...). But the problem is that I don't know how to upgrade the sources. They are all still saying Lucid instead of Natty.

So, my question is, how do I update my sources so that they are relevant for Natty? Is it just a matter of changing "lucid" to "natty"? Or something more complicated?

Thanks!

---

### Post by ivanovnegro on 2011-06-09
As you are using an LTS version the update manager is set by default to only point to the next LTS version, apparently not Natty.
To change this, open the update manager and change this behavior, somewhere in the options you will see updates, in your case its checked LTS, you have to change this into "normal releases".

Backup your data first and good luck!

If you have limited bandwidth it could take HOURS to upgrade your system, because it will first upgrade to Maverick and then to Natty.
Are you sure you want to go this path, if you are happy, better stay on 10.04? Read the release notes of Natty to see what is new, nameley the new UI Unity. I would try it first on a Live CD before doing anything, could save your time.

---

### Post by dannelb on 2011-06-09
Sorry, I should have made myself more clear. And I think I figured out what to do...

I'm actually already on Natty (one of the IT guys downloads all the ISOs whenever a new Ubuntu comes out...). But my sources.list for the local repository on the local network here still was for Lucid.

Anyway, I backed up my sources.list and then did replaced all the "Lucid" references with "Natty". I am currently running apt-get and all seems to be working fine...

Thanks for the help though

---

### Post by ivanovnegro on 2011-06-09
Ok, I understand now. Good that it works. :D

---

