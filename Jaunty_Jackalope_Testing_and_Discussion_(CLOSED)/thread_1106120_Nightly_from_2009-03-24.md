---
title: "Nightly from 2009-03-24"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pinus on 2009-03-25
I installed the nightly build from 2009-03-24 on a PII 720 system.
I used the 64 bit version on this box because it has 8GB of RAM.
The installation worked ok and even the integrated graphic (AMD 790FX) works out of the box. The visual effects (3D) are disabled and do not work with the default driver.

But the Java stuff doesn't work so well. The OpenJDK packages don't tell you if they are 32 or 64 bit. They also don't tell you which SUN JDK version they match or if they support the 64 bit Mozilla plugin (as version 6 update 13).
The SUN JRE doesn't install the thunderbird plugin and I could not install it (select it). I could not even remove the SUN package without using synaptic :-(.
I installed the icedtea plugin and OpenJDK but could not start the JavaFX samples at javafx.com. I would expect for a 64 bit system to support the 64 bit browser plugin and to be able to run the examples of SUN. This doesn't work, yet.

Synaptic also has its problems. The search for java doesn't return a match. Using Applications/add or remove works and shows the Java packages.

And the German texts, well, they have 4 weeks left.

---

### Post by dBuster on 2009-03-25
As far as the 64bit flash plugin, before you even went and loaded icedtea there is a thread with an install script to install the 64bit plugin.  You can still run the script with a modification to it for the current file name of the latest release.  That can be found at [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

As far as the Synaptic Package Manager not containing Java or being able to return anything related to Java when you search, it works for me.  I have installed the SUN Java that way after I had the script run to get the plugin.

Also, I found out that on my machine, the 64bit flash plugin DOES NOT like icedtea installed...  So it may choke on your machine also.  I think though the script will remove it for you.

---

### Post by Kow on 2009-03-25
> **pinus said:**
> I installed the nightly build from 2009-03-24 on a PII 720 system.
I used the 64 bit version on this box because it has 8GB of RAM.
The installation worked ok and even the integrated graphic (AMD 790FX) works out of the box. The visual effects (3D) are disabled and do not work with the default driver.

But the Java stuff doesn't work so well. The OpenJDK packages don't tell you if they are 32 or 64 bit. They also don't tell you which SUN JDK version they match or if they support the 64 bit Mozilla plugin (as version 6 update 13).
The SUN JRE doesn't install the thunderbird plugin and I could not install it (select it). I could not even remove the SUN package without using synaptic :-(.
I installed the icedtea plugin and OpenJDK but could not start the JavaFX samples at javafx.com. I would expect for a 64 bit system to support the 64 bit browser plugin and to be able to run the examples of SUN. This doesn't work, yet.

Synaptic also has its problems. The search for java doesn't return a match. Using Applications/add or remove works and shows the Java packages.

And the German texts, well, they have 4 weeks left.

I'm scratching my head here because I can't figure out how a Pentium II will be able to understand 64-bit binaries. Is the Pentium II a different system from what you are having issues on?

EDIT: Ahh PII looks like the model name of a new CPU? Yay for ambiguity.

---

