---
title: "Problem Installing Java JDK 6 Update 6 with NetBeans 6.1"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by hquijanog on 2008-06-04
Hi!. I have a compaq presario R3000 notebook with pentium 4. I had installed Ubuntu 7.10 But I formated the computer and installed the new Ubuntu 8.04.

In the 7.10 version I went to the java sun web page (this page: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)) and downloaded the JDK 6 Update 6 with NetBeans 6.1 for linux version (a .sh file)

It worked fine in the 7.10 version. Nevertheless, in Ubuntu 8.04 I downloaded the same file, I give it execution permisions and run it. The installer displays a empty window that says "Java SE Development Kit and NetBeans IDE Installer" and I can't install it.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72974&stc=1&d=1212623440[/IMG]

I attached a png file which displays the window.

On Ubuntu 7.10 that window wasn't empty it showed an agrement license and an accept and cancel button.

But why in version 8.04 the installer is not runing as it should?. what I need to do to solve this?

---

### Post by ohiomoto on 2008-06-04
I had the same issue on my laptop running 8.04.  I had to install the JDK first and then NetBeans.  Everything works fine that way.

---

### Post by hquijanog on 2008-06-06
I founded the solution to the problem!!!.

If you go to System/Preferences/Appearance then to visual effects and select none, the problem will be fixed. The next time you run the .sh it will show right.

Ubuntu 7.10 had none visual effects as default and the 8.04 has normal visual effects as default, that was the reason it worked on 7.10 version.

It's strange, but the visual effects seems to be the reason of the malfunction.

Anyone knows why is happening that? its strange that whole problem was just the visual effect. Any FAQ?

---

