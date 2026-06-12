---
title: "Version merging"
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by chips2 on 2014-10-01
Downloaded 13.10 to DVD.
Did live boot and run the install.

Allowed me to go online with a usb dongle.

Upgraded the installation.
Did dpkg the Lazarus packages.
Dependicies ??
Did apt-get -f install

Package errors,tried system suggestion to repair.
failed.
I now get about 12 messages as to failure.

Someone may solve this.

However :
My question is

If I have a 13.10 DVD for instance, can I merge the upgrades to create say: 13.10.0.1 DVD version.

APT approach to versioning is commendable.However, if it renders the system to 
the average user more questions, what then.

Also, how about (1) one error Log message.
Then a informative error message queue.

I am a ex Data General Nova,PDP 11, IBM Dos/Vse,MVS,IBM 36/4700,farmer,widow.
Do dabble in antiques and Windows 95/98/Me/XP.

---

### Post by Vladlenin5000 on 2014-10-01
Hi, welcome.

13.10 is EoL. Please install a supported version -> 14.04.

---

### Post by grahammechanical on 2014-10-01
I do not know what you mean by "merge the upgrades."

Ubuntu 13.10 has reached end of life. Ubuntu LTS (Long Term Support) now have support for 5 years but the six monthly Standard (Interim) releases only have 9 months support. 

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

You do not tell us what those error messages were saying. I am guessing that they come from the fact that the 13.10 repositories are now closed and have in fact been relocated. The URLs to them in the software sources lists are now pointing to the wrong servers.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You say that you upgraded the installation. You do not make it clear if you updated/upgraded or upgraded to 14.04. If you want to have 14.04 then a fresh install of 14.04 is much better than installing an end of life version and upgrading to 14.04. It might avoid some of these problems.

What is Lazarus? Is it this?

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

So, is the problem with Ubuntu or with the installation of a specific item of software?

Regards.

---

### Post by Bucky Ball on 2014-10-01
Welcome. As suggested by Vladlenin5000 and grahammechanical, see here:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

13.10 = EOL release. No longer supported by Canonical or these forums. Please install a supported release and post a new thread with any further issues. Good luck. ;)

Also, yes, just install 14.04 or 12.04 LTS. If you are just starting on your Ubuntu adventure, advisable and a smoother ride.

---

