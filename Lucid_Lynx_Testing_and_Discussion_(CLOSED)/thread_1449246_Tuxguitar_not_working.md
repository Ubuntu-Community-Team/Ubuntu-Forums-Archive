---
title: "Tuxguitar not working?"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by robertneville777 on 2010-04-07
I had Tuxguitar working great under 9.10, but after I upgraded to 10.04 Beta, Tuxguitar wouldn't launch. I reinstalled it through synaptic, but it still won't start up. Here's what happens when I try to launch from terminal.

> robertneville777@robertneville777:~$ tuxguitar
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Control
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Control
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 1 more
robertneville777@robertneville777:~$ 

I just want to see if others have this problem before I file a bug. It could be me doing something wrong.

Thanks!

---

### Post by Killigrew on 2010-04-07
Hi

i don't have any problem with tuxguitar
i have the openjdk installed

greetings

---

### Post by cpmman on 2010-04-07
> **killigrew said:**
> hi

i don't have any problem with tuxguitar
i have the openjdk installed

greetings

+1

---

### Post by billyShears on 2010-04-08
I was affected by this bug too, to fix it try to reinstall the libswt-gtk-3.5 packages.
The same bug has been fixed in Debian ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569910]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569910")), I think we should file a bug asking to backport the patches.

---

### Post by robertneville777 on 2010-04-08
> **billyShears said:**
> I was affected by this bug too, to fix it try to reinstall the libswt-gtk-3.5 packages.
The same bug has been fixed in Debian ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569910]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569910")), I think we should file a bug asking to backport the patches.

Dude, thank you Billy! It works now! So should I file a bug report, and if I need to, how would I do that?

---

### Post by billyShears on 2010-04-08
> **robertneville777 said:**
> Dude, thank you Billy! It works now! So should I file a bug report, and if I need to, how would I do that?

I've filed a bug report ([#558672]("https://bugs.launchpad.net/ubuntu/+source/swt-gtk/+bug/558672"))

You could confirm it and/or add a comment.

---

### Post by robertneville777 on 2010-04-08
> **billyShears said:**
> I've filed a bug report ([#558672]("https://bugs.launchpad.net/ubuntu/+source/swt-gtk/+bug/558672"))

You could confirm it and/or add a comment.

Will do buddy, thanks!

---

