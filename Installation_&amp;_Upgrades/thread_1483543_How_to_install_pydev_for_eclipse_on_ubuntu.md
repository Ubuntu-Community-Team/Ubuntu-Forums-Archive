---
title: "How to install pydev for eclipse on ubuntu"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by Scottty on 2010-05-14
Hello

I have tried several methods of installing pydev for eclipse on Ubuntu 10.04.

I have gone to help in Eclipse and selected Install New Software, from there I entered

Pydev and Pydev Extensions - [http://pydev.org/updates](http://pydev.org/updates)
and found 
    PyDev for Eclipse	1.5.7.2010050621

so I selected it and
seemed to be installing then came the following message
> 
Install has encountered a problem.
An error occurred while installing the items.

```

An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.cvs 1.0.400.v201002111343, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  The artifact file for osgi.bundle,org.eclipse.cvs,1.0.400.v201002111343 was not found.

```

Can someone let me know how I can get this installed for Ubuntu 10.04

Thank you,
Scott

---

### Post by TTown on 2010-05-21
Nope,

I wish I could. I encountered the same problem.

---

### Post by TTown on 2010-05-22
The trick is to run eclipse as super user (open a terminal and run 'sudo eclipse') while installing pydev. You may want to go as far as to run 'sudo eclipse -debug -consolelog' to learn more about what is happening.

[http://linuxforhumanbeings.blogspot.com/2009/10/how-to-integrate-pydev-in-eclipse-for.html](http://linuxforhumanbeings.blogspot.com/2009/10/how-to-integrate-pydev-in-eclipse-for.html) helped me.

---

### Post by ryan461 on 2010-05-24
Open synaptic and make sure you've installed eclipse-pde. Its what allowed pydev to install for me.

---

### Post by huzzak on 2010-07-07
ryan461's solution worked for me.

Ubuntu 10.04, Eclipse 3.5.2.

---

### Post by fazza on 2010-07-13
This is excellent thanks, I couldn't get it to install either. I'm just install eclipse-pde now :)

---

### Post by fazza on 2010-07-13
YES! This eclipse-pde worked for me, though I also had to run it as root.
Thanks very much

---

### Post by rammbhat on 2010-10-02
> **TTown said:**
> The trick is to run eclipse as super user (open a terminal and run 'sudo eclipse') while installing pydev. You may want to go as far as to run 'sudo eclipse -debug -consolelog' to learn more about what is happening.

[http://linuxforhumanbeings.blogspot.com/2009/10/how-to-integrate-pydev-in-eclipse-for.html](http://linuxforhumanbeings.blogspot.com/2009/10/how-to-integrate-pydev-in-eclipse-for.html) helped me.
This worked! Thanks!

---

### Post by Amndeep7 on 2012-12-25
Sorry for bringing this thread back up - I just wanted to provide further proof that installing the software while running Eclipse under sudo does work.

---

