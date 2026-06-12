---
title: "Intel Pentium M &amp; Lubuntu 14.04"
date: 2016-09-27
forum: Installation &amp; Upgrades
---

### Post by jburges2 on 2016-09-27
As the title indicates I have an older IBM laptop with a 1.5Ghz Pentium M class processor which does not have native PAE, and 1.5GBs of system memory. I downloaded and tried to install the latest x86 CD (14.04), but I get the usual error message indicating that I cannot install it due to my CPU not having PAE support. I wanted to install to disk, and not run from a USB or CD, but I cannot find a way to bypass this. I had read that previous distros of Lubuntu had PAE disabled by default. Should I download an old version and upgrade?

What are my options to get this installed? Appreciate any insight.

---

### Post by Dragonbite on 2016-09-27
Having a laptop with no PAE support means you have to use a 32bit system.  I didn't know 14.04 comes in 32bit but maybe try 12.04 instead.  I think Xubuntu 12.04 is what I have running on my IBM Thinkpad (Pentium M, 2 GB RAM).

If the .ISO has "x86" or "i386" or "i586" or "i686" and not "x86_64" or "amd" then it may work.

I don't know who still provides 32 bit system images anymore.  I haven't used those laptops in a loooong time.  I don't know if you have to move to something like Puppy.

---

### Post by deadflowr on 2016-09-27
32-bit is still around for all Ubuntu flavors.
Just hard to find on Ubuntu.com, as they only really list the 64-bit version there:
Lubuntu download page: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Standard_PC]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Standard_PC")

On PAE/forcepae:[https://help.ubuntu.com/community/PAE]("https://help.ubuntu.com/community/PAE")

and how to add boot options: [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by jburges2 on 2016-09-27
Thank you both for replying. I'm pretty sure the version of Lubuntu I downloaded was the 32-bit version, the main issue being the PAE error on attempted install.

The links you provided on the Force PAE, as well as the boot options are super helpful, I appreciate it. I will give this a go and see how it pans out.

---

### Post by jburges2 on 2016-09-27
Update, I followed the directions for adding the forcepae to the end of the boot options, and I have it successfully installed now, so thank you. Now begins my endeavor of delving deeper into packages, configuration, etc.

---

### Post by deadflowr on 2016-09-27
Congrats.
If you feel that the solution to this particular problem helped, please help others who may come across in the future by marking this thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by jburges2 on 2016-09-29
Ok, thanks again, marked as solved.

---

