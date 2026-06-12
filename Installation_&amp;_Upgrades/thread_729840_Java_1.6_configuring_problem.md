---
title: "Java 1.6 configuring problem"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Vuddha on 2008-03-20
Hi All,

I'm install Jabref (from the repos) and I'm assuming the Jabref install is upgrading Java from 1.5 to 1.6. 

Prior to installing Jabref, I had Java 1.5.

However, now all that appears in the terminal is a blue window that says "Package configuration", stating "Configuring sun-java6-bin". This is followed with the Sun Microsystems software agreement. 

It seems to be stuck on this screen, as I don't think it would take this long to "configure Java". I've tried searching the forums and the internet for a similar issue, but no luck. Also, I don't want to close the terminal before it's done "configuring", as it might do something nasty.

What do I do to solve this problem? Thanks.

---

### Post by Bablefish on 2008-03-20
To set everything use this

To set java use this command in terminal



sudo update-alternatives --config java

---

### Post by Vuddha on 2008-03-20
Can I use that in a separate terminal (while leaving the other one open?).

Actually, I opened another terminal and did that, and the result was this:


There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.



Seems strange, and I'm not really familiar with this stuff.

Thanks for the help.

---

