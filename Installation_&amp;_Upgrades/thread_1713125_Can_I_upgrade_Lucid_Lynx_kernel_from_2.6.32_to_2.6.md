---
title: "Can I upgrade Lucid Lynx kernel from 2.6.32 to 2.6.38.1?"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by Louisraritan on 2011-03-23
Hi, noob question:  Can I upgrade lucid lynx kernel from 2.6.32 to 2.6.38?  If so, how do I do it from command line?  Thanks for help.

---

### Post by falko on 2011-03-23
Basically yes, but as this kernel is not available through Ubuntu's package manager, you'd have to build it yourself, and you shouldn't try this on a production system as lots of things can go wrong. Try it on a test system (like a virtual machine) first.

This link (although a few years old) might help: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Louisraritan on 2011-03-23
Hey Falco and thanks for the response.  You are right, it isn't in the Ubuntu repos.  I ended up digging around and figured out how to wget the kernel.  Am testing it out in virtual box on my custom lucid distro.  I have run into quite a few obstacles (limited knowlege).  Is great though because command line tells me what I can and can't do as well as what I need to get in order to make something work.  The link you provided has answered my questions well.  Thank you.  Will let you kno if I hit another snag.

---

### Post by halj32 on 2011-03-23
the easiest way is to add the kernel ppa
have a look at this page
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)
remember you may have to rebuild your drivers if you dont have dkms installed
[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)
goodluck

---

### Post by Louisraritan on 2011-03-24
Okay, followed Falco's instructions and got to complilation stage.  Need to learn what all the settings in make menu are, will get back at it today.
 
Tried the ppa route, first run added the sources to synaptic.  Added 2.6.38.1 and nada.  Read that synaptic limits what can do with kernel.  Is that accurate?

---

### Post by mörgæs on 2011-03-24
If you want 2.6.38, it is easier to install 11.04. As it is still in alpha, you should not expect a completely stable system, though.

---

### Post by Louisraritan on 2011-03-24
I should have been more clear about what I am trying to do.  Keep in mind that I am thinking in windows and playing with linux (that current stable drivers are backwards compatible).  I have Lucid and am very happy with it.  Is it possible to upgrade to the most recent kernel and switch to gnome shell 3 and still keep everything I like in Lucid?  Lucid is stable, kernel 2.6.38.1 is stable and Gnome 3 shell kinda (assuming I will have to disable everything compiz and add different update sources to synaptic).  Basically, rather than upgrade to Natty, I want to upgrade the kernel and desktop environment of lucid.  Any takers?

---

### Post by halj32 on 2011-03-25
Ive updated mine to 2.6.38.7 generic
dont forget to install both headers too
everything works fine & I use lucid both Gnome & KDE

---

### Post by Frogs Hair on 2011-03-25
You may continue to receive updates for the old kernel , so be careful not to revert.

---

