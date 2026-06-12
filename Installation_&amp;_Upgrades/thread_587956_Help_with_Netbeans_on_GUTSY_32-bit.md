---
title: "Help with Netbeans on GUTSY 32-bit"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by eric_son on 2007-10-23
Hi,

This is the first time for me to install NetBeans on LINUX (UBUNTU 7.10 32-bit).
Initially, I installed NetBeans using Synaptic.  When I started NetBeans, this is what I got:
[IMG]http://i107.photobucket.com/albums/m295/eric_son/misc%20stuff/Netbeans.png[/IMG]

Thinking that NetBeans was still loading, I waited like 10 or so minutes.  Unfortunately, the screen remains unchanged.  The application is alive though.  I can use **ALT-F -> O** and the File Open dialog will pop-up.  

I also tried uninstalling NetBeans from Synaptic, then re-installing it using the standard installer which I downloaded from the NetBeans site.  The exact same thing happens.

I have the **sun-java5-jdk** installed.

What could be the problem, and how can I fix this?

Thanks.

Eric

---

### Post by pilsna on 2007-10-23
This problem is related to compiz. Netbeans works fine for me until I turn on Desktop effects.
It seems to be a Java bug. There is a bug report [here]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775"). 
You could try to update to Java 6, which should work better, but not 100%.

---

### Post by eric_son on 2007-10-23
Dang!  
You are right.  I disabled desktop effects and NetBeans worked normally.
The weird thing is... I can enable desktop effects afterwards and NetBeans would still work.  But when I quit and restart NetBeans, it would go back to its usual non-working behavior.

:(

---

### Post by dewey on 2007-10-24
Java6 may be the answer you're looking for, I just installed netbeans from the repo's, and am running Desktop Effects, and they work together without problem.

---

### Post by eric_son on 2007-10-25
Installing Java 6 did the trick.  Thanks!  :)

(However, installing Java 6 alone didn't fix the problem.  I had to uninstall then re-install NetBeans after installing Java 6 before it worked.)

---

### Post by apoth on 2007-11-03
> **eric_son said:**
> (However, installing Java 6 alone didn't fix the problem.  I had to uninstall then re-install NetBeans after installing Java 6 before it worked.)

For anyone else's future reference, you can edit the value for netbeans_jdkhome in etc/netbeans.conf (which is in /usr/local/netbeans-6.0beta2 for me at the moment) to change the JDK Netbeans uses rather than reinstalling.

---

### Post by eric_son on 2007-11-03
> **apoth said:**
> For anyone else's future reference, you can edit the value for netbeans_jdkhome in etc/netbeans.conf (which is in /usr/local/netbeans-6.0beta2 for me at the moment) to change the JDK Netbeans uses rather than reinstalling.

Thanks. :)

---

### Post by belda on 2007-11-21
you can add this to the netbeans starter or put it in session startup settings
```
export AWT_TOOLKIT=MToolkit
```
its more simple and more linuxy than installing and reinstalling :-)))

---

### Post by eric_son on 2007-11-21
Indeed!  Thanks for the great tips.

---

### Post by tarekeldeeb on 2007-11-30
> **eric_son said:**
> Dang!  
You are right.  I disabled desktop effects and NetBeans worked normally.
The weird thing is... I can enable desktop effects afterwards and NetBeans would still work.  But when I quit and restart NetBeans, it would go back to its usual non-working behavior.

:(

same here on Gutsy 64bit AMD !

---

### Post by lifewithryan on 2007-12-05
the whole export AWT_TOOLKIT=MToolkit worked for me..

I have no idea why...but it does :)  Java 1.5.0_09 from Sun (not the ubuntu package) and Gusty with Desktop Effect turned on.

Thanks!

---

