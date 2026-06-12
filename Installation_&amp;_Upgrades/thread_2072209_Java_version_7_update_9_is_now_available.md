---
title: "Java version 7 update 9 is now available"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2012-10-17
Java version 7.9 just came out today or last night. The link to **Check your Java version** is in my signature. 
If you have to click on **All java downloads** on the left and you will see that 7.9 is available for download.
Download the **Linux** version for 32 bit machines or the **Linux x64** version for 64 bit machines.
The .RPM version is for other Linux Distros.
Choose "save file" when prompted and then the instructions to install it are in the other link in my signature **How to manually update Java**.
The How to link is Oracle (Sun) Java JRE for **Ubuntu, Linux Mint and Debian**.
The instructions have been updated to 7.9 so just copying and pasting is all that is needed.
For 32 bit the instructions are on the left and for 64 bit the instructions are on the right.
It will tell you to remove any older version first and provides instructions for doing so.

I am aware there is a repository for this but, if you like installing it the manual way, this will work.

When you get it installed open a tab and enter
```
about:plugins
```It should show this:

**Java(TM) Plug-in 1.7.0_09**

---

### Post by Cavsfan on 2012-10-17
I just updated my 3 Ubuntus to 7.9. It was a piece of cake.

---

### Post by offgridguy on 2012-10-17
:pThanks for the info.

---

### Post by Cavsfan on 2012-10-17
> **offgridguy said:**
> :pThanks for the info.

You are welcome! :P

---

### Post by QIII on 2012-10-17
Again, **the very easiest way to keep Oracle Java 7 updated** without fuss is to use the webupd8 PPA as described in the wiki link in my signature, under "Oracle Java 7", "Command line methods", "Using webupd8.org's strikingly simple method".

Adding and installing from the PPA will ensure that as Oracle produces outputs, your machine will be updated automatically as you do your normal Ubuntu updates.

There is NO reason for an Ubuntu user to go through the complexity of installing Java from the Oracle website and then reinstalling when a new update comes out.  No more copying and pasting.  I no longer recommend the Easy Linux Tips method.

The folks at webupd8.org handle all of that for you.  The installer for Oracle Java 7u9 is in their PPA.  If you have installed the webupd8.org installer, there is nothing you have to do but update Ubuntu.

Note the following from the wiki:  "*Using webupd8.org's method has a great benefit in that the package will  be updated as Oracle releases Java updates, which means that there will  be no need to keep track of updates and reinstall them manually.* "

---

### Post by Cavsfan on 2012-10-18
I know **QIII** you have told me before and that is fine. I guess I am just a CLI kind of guy.

More power to the people that want to choose your method. I have done this CLI method so many times that it is easy for me.
Yesterday my windows 7 install notified me that there was a java update and I installed it.
I knew the 7.9 version was out for all operating systems.

Plus, this method works for **Ubuntu, Linux Mint and Debian**.

---

### Post by QIII on 2012-10-18
Fair enough.  The following is not meant to be argumentative, only informational for other users.  They can certainly choose the method they will.

According to some threads on the Mint forums, the webupd8 PPA also works for Mint.  I suspect the same may be true for many Ubuntu derivatives.  I believe I used it to install Oracle Java on Bodhi Linux.

Webupd8.org also has a Debian method, which requires only two more lines in the CLI.  The package is the one from their Precise repo, the difference being that Debian users have to explicitly add the key.

The webupd8.org process installs the entire JDK (which includes the JRE), while the Easy Linux Tips method installs only the JRE.

The JDK can be useful for those who want to modify/recompile Java applications to suit their needs.  There are those who might also wish to dabble in learning Java.  I also took part in a thread in which a poster needed to modify a game to work in Ubuntu and the presence of the JDK was required.

The very problematic downside to the Easy Linux Tips method is that the user must be aware, by some means, that there is a new update available.  This can be downright dangerous in a situation like happened a month or two ago where Oracle pumped out an off-cycle security update because of the sandbox-jumping vulnerabilities discovered and exploited.  A user, caught unaware, might have been exploited long after the update had been published if they did not know an update was available (or even that the exploit had occurred to begin with!)  Java's perennial security issues are bad enough already.

That downside is the reason I no longer recommend the Easy Linux Tips method -- which I actually did recommend for several years.  I even communicated with the maintainers on a couple of occasions to offer recommendations.  Notice that in the wiki in my signature I did not remove the reference to that method, although I was tempted to.  Whether or not to use it is certainly up to the user.

I wouldn't even recommend Oracle Java at all, except that much of the world simply does not recognize OpenJDK as "Java", despite the fact that OpenJDK is the open source reference implementation for all things Java -- including Oracle Java.  Even Oracle accepts OpenJDK as the "standard".  They pushed for it and are the largest mover and shaker in its development.

---

### Post by Cavsfan on 2012-10-18
I don't use the JDK anyway and I have no use for it.

When the windows 7 installer runs it says Billions of things use Oracle java. 
I can't even start to mention any of them but, I remember Bank ATM machines were one of them.

I think others that do not need the JDK are satisfied with this method as well.

Thanks for the post. As long as this works for me I will use it.

---

### Post by GreenTaurus on 2012-10-18
Funny enough I just installed this (CLI) last night... I'll have to check out your method QIII.

---

### Post by Cavsfan on 2012-10-19
Works fine for me. I don't like that icedtea stuff etc. I want Oracle Java and however secure it is has never been 
an issue for me. I use NoScript and WOT so I know what I am getting into.

I just installed java from this link this morning. Piece of cake since it was a fresh install of Quantal and had no java installed.

---

### Post by Cavsfan on 2012-10-25
Here are the two links as I am removing them from my signature.

[[COLOR=red]_Check Java Version_[/COLOR]]("http://www.java.com/en/download/installed.jsp") | [[COLOR=green]_Manually Update Java_[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by Cavsfan on 2012-11-11
Added the 2 links back to my signature. This method is exclusively for those who like me prefer to update java the manual way.

---

