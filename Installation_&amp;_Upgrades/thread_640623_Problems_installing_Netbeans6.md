---
title: "Problems installing Netbeans6"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by lulon on 2007-12-14
Hi!

I have Ubuntu7.10 and I have already installed JDK well.

I want to install Netbeans6 now and I have done it:

[INDENT]./netbeans-6.0-linux.sh --javahome /usr/lib/j2sdk1.5-sun
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring[/INDENT] 

It doesn't work because the installation stops. I only can see a grey window...

I have been searching and I have found this:

[INDENT]sudo gedit /etc/environment
and add in that file: AWT_TOOLKIT="MToolkit"[/INDENT]

But it doesn't work either.

What can I do?

Thanks a lot.

---

### Post by Jimmy_r on 2007-12-15
Wild guess based on the error messages: 
Try setting the theme back to the default 'Human' while installing.

---

