---
title: "Web browser only"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by timjohnarm on 2011-05-25
I am running Ubuntu 11.04 and want to create a second bootable partition that functions as a locked down Web Browser only. Namely the one I do my online purchases and the like from.

Now without going to the extreme of killing off the entire GNOME desktop I'm looking for advice on which packages I need to retain or delete, whichever is easier.

Steps I have already taken are to follow the forums guide on further locking down Ubuntu and I will be creating a very limited Desktop user with no Admin rights.

One of the apparent holes seems to be SSH and whilst it can be configured to be tougher to hack if its just not there then it can't be used at all. However I don't know if removing it is going to cause me all sorts of problems and I've now spent quite a bit of time on the new environment I'm creating. Aside from anything else would it kill my ability to get the automatic updates to happen?

---

### Post by uRock on 2011-05-25
A basic install is very secure. The only things I would do is add the NoScript add-on in Firefox and enable UFW(Uncomplicated FireWall) by running **sudo ufw enable** in a terminal or install and run GUFW(Gui for UFW) and block all incoming. 

Once UFW is enabled, incoming SSH packets will be dropped unless you configure the firewall to accept incoming connections on port 22.

---

### Post by tommcd on 2011-05-26
You can do a minimal install of Ubuntu like this: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)
This way you can add only the stuff you want.

---

