---
title: "server+ or desktop+"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by tonylinde on 2007-12-08
I want to set up a desktop with underlying server software so that I can develop python, php and rails applications and test them out. The best fit appliance is the [Web Developer one]("http://www.vmware.com/vmtn/appliances/directory/134") but that is on breezy and breaks every time I try to upgrade it.

Is it better to create a server installation and install the GUI and development packages on top of that or to create a desktop installation, adding apache etc on top of that? I'll be installing in a VMWare workstation with gutsy and am a fairly naive Linux user. If there are any websites which address this issue or previous threads (I did try a couple of searches), please point me to them.

Many thanks,
Tony.

---

### Post by Pumalite on 2007-12-08
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by tonylinde on 2007-12-08
Thanks, Pumalite - that is a good resource. But I was looking for a GUI-based setup which included apache and web development tools like python, php and ruby/rails. Your link was how to install a fully spec'ed server itself.

T.

---

### Post by Pumalite on 2007-12-08
To that you can add a GUI:
sudo apt-get install ubuntu-desktop

---

### Post by eptech1 on 2007-12-08
Alternatively, install your Ubuntu Desktop, open up Synaptic and from the dropdowns at the top choose to Select Files by Task to get the Lamp and openssh installed.  Rails would be using gems most likely.

---

