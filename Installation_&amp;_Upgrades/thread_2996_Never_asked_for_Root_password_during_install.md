---
title: "Never asked for Root password during install"
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by jriis on 2004-11-02
Hi 

I just installed Ubuntu, but was never asked for a Root password during install, only a user and password. Now I cannot log in as root for maintenance and such. What did I miss ?

Regards

Jan Riis Soerensen
Denmark

---

### Post by TimL on 2004-11-02
[QUOTE=jriis]Hi 

I just installed Ubuntu, but was never asked for a Root password during install, only a user and password. Now I cannot log in as root for maintenance and such. What did I miss ?

Regards

Jan Riis Soerensen
Denmark[/QUOTE]
 Hi,

Ubuntu uses sudo for the user you added during installation.
It's all outlined here: [http://www.ubuntulinux.org/support/documentation/faq/root/view?searchterm=sudo](http://www.ubuntulinux.org/support/documentation/faq/root/view?searchterm=sudo)

Basically, any command you need to do as root, just type "sudo command" and you will be prompted for YOUR OWN USER PASSWORD.

Cheers,

Tim

---

### Post by p__wack on 2004-11-02
[QUOTE=TimL]Hi,

Ubuntu uses sudo for the user you added during installation.
It's all outlined here: [http://www.ubuntulinux.org/support/documentation/faq/root/view?searchterm=sudo](http://www.ubuntulinux.org/support/documentation/faq/root/view?searchterm=sudo)

Basically, any command you need to do as root, just type "sudo command" and you will be prompted for YOUR OWN USER PASSWORD.

Cheers,

Tim[/QUOTE]
 damn!, and is no oportunity to create the root user in the setup?

I'm a root fan!

so no +

---

### Post by jdong on 2004-11-02
sudo is better; it keeps a log of every action, so it's really easy to trace that mistype that deleted 100 files... ;)

---

### Post by fng on 2004-11-02
If you are a root fan, there is a menu option to have a root console
applications -> System tools -> root terminal

If that isnt enough, you can even enable the root account :
sudo passwd root

I dont recommand this last 1
sudo is also better imho
But isnt linux all about choices? :)

---

### Post by FLeiXiuS on 2004-11-02
[QUOTE=fng]If you are a root fan, there is a menu option to have a root console
applications -> System tools -> root terminal

If that isnt enough, you can even enable the root account :
sudo passwd root

I dont recommand this last 1
sudo is also better imho
But isnt linux all about choices? :)[/QUOTE]

sudo passwd root doesn't enable it, its already enabled.  This command would just give more system protection.

But on the other hand sudo > all :-)

---

### Post by Vulc on 2004-11-03
sudo is indeed teh win so to speak, but passwd root works if you just gotta su =p

---

### Post by jdusablon on 2004-11-03
All security people will tell you NOT to use root (or local/domain admin in Windows.) It's a hard habit to break, but it's worth it. Also, it's actually very workable in unix/linux systems, whereas in Windows it's a pain in the behind to implement. You can't Run As... everything, only certain things.

---

### Post by jwenting on 2004-11-04
[QUOTE=jdusablon]All security people will tell you NOT to use root (or local/domain admin in Windows.) It's a hard habit to break, but it's worth it. Also, it's actually very workable in unix/linux systems, whereas in Windows it's a pain in the behind to implement. You can't Run As... everything, only certain things.[/QUOTE]
 Sometimes root is needed, simple as that.
Example might be a kernel compile and install. Sure you can type sudo xxxxx for a dozen or so commands but it gets old quickly.

Other things might be restarting certain services that only root has access to.

The mantra is to use root for as short a time as needed, not to use it at all (though I can see where many typical desktop users will never have a need to use the root account which makes disabling it by default a good choice for them).

---

### Post by rstark on 2004-11-05
Don't forget there's always:   sudo su -

RS

---

