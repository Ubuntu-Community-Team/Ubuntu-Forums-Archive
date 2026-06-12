---
title: "A way to do a &quot;full&quot; install."
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by Anton_Solovyev on 2014-06-16
New to Ubuntu. I tend to like to install Linux in a fullest configuration possible. With RH and clones I just force all packages in the kickstart file or do it manually during package config stage.

Is there a way to do this with Ubnuntu install? What I am looking for is the most complete installation reasonably possible. I often do not have Internet connectivity, and/or may not be able to execute a tool and dependency install later on due to time constraints. I have found that none of the vendor offered configurations works for me as a rule.

Thank you in advance!

---

### Post by grahammechanical on 2014-06-16
With Ubuntu we get what the developers have decided should be the default installation and then we install other software afterwards. It is done this way to keep the ISO image download size as small as possible and to make sure that Ubuntu is simple to install for the person new not only to Ubuntu but to computers. A design decision was taken not to inflict upon the potential user what is often a confusing number of choices.

Regards.

---

### Post by sudodus on 2014-06-16
Welcome to the Ubuntu Forums :-)

Directly after the installation (while you are still connected to the internet), you reboot and install a few packages, that we can recommend here in your thread.

For multimedia etc:

```
sudo apt-get install ubuntu-restricted-extras
```

For graphics:

```
sudo apt-get install gimp
```

For editing partitions:

```
sudo apt-get install gparted
```

...

Tell us what you want, and we can tell you if it comes with the installation or if you should install some package for it.

Edit: By the way, if you tell us about your computer, we can give better advice concerning which flavour of Ubuntu to install.

---

### Post by Anton_Solovyev on 2014-06-16
> **grahammechanical said:**
> With Ubuntu we get what the developers have decided should be the default installation and then we install other software afterwards. It is done this way to keep the ISO image download size as small as possible and to make sure that Ubuntu is simple to install for the person new not only to Ubuntu but to computers. A design decision was taken not to inflict upon the potential user what is often a confusing number of choices.

Regards.

Understood. I was just wondering if there was a choice. I like to keep my systems "immutable" for the reasons outlined previously, so this does not really suit me all that well. Thank you!

---

### Post by Anton_Solovyev on 2014-06-16
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Edit: By the way, if you tell us about your computer, we can give better advice concerning which flavour of Ubuntu to install.

It's really hard to tell, obviously. I find that a full install of a RH based distro keeps me reasonably happy. Any of the predetermined configurations ("Workstation", "Server", "Developer workstation") gets me to something trivial missing within a couple of hours. Thanks!

---

### Post by oldfred on 2014-06-16
If you install the gui of your choice which includes many apps, you can use the server install's selection menu to add just about anything or everything you want.

 [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

And you can go berserk on desktops and add them all. I really do not suggest this as it gets confusing.
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)

---

### Post by Anton_Solovyev on 2014-06-16
> **oldfred said:**
> If you install the gui of your choice which includes many apps, you can use the server install's selection menu to add just about anything or everything you want.

 [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

And you can go berserk on desktops and add them all. I really do not suggest this as it gets confusing.
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)

So, I guess this is more of the same: choose what you want. It basically shifts the decision (and testing whether it all works together) to the end user. I understand. This does not really help with what I'd like. I guess I need to decide whether I can live with this system or not. Thanks!

I'll close the thread since the answer is simply "no, there's no such thing as a full install". I just was wondering if there was a magic incantation kickstart style "install all".

Thank you!

---

