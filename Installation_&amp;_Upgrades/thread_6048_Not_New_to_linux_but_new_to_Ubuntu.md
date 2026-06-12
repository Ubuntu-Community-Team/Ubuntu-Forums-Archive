---
title: "Not New to linux but new to Ubuntu"
date: 2004-11-24
forum: Installation &amp; Upgrades
---

### Post by d3c3it on 2004-11-24
Hi everybody
Long story short im a debian 'sid' user wanting a change, mostly because ubuntu has got a fully setup gnome 2.8 and xorg (in The Hoary Hedgehog array1) but ive got a couple of questions before i install.

First of all. Can i still do my usual apt-get <command> from the cmdline. Sounds silly i know but so far ive just seen screenshots that show synaptic(sp) just wondered can i still do it the old fasioned way. Sounds silly i know, i just want to double check.

If i install hoary array 1, and i do a apt-get update apt-get dist-upgrade will the system be 100% up to date or when "The Hoary Hedgehog" goes stable do i have to reinstall?

Can i still make my own kernels with make-kpkg or is it the preferred way to stay with binary premade kernels?

I presume with ubuntu being based on debian all the above is a resounding yes i just wanted to check as i know ubuntu is based on debian just wondered if some things were different?

Sorry for sounding like such a newbie. :-(

---

### Post by p!=f on 2004-11-24
[QUOTE=d3c3it]
First of all. Can i still do my usual apt-get <command> from the cmdline. Sounds silly i know but so far ive just seen screenshots that show synaptic(sp) just wondered can i still do it the old fasioned way. Sounds silly i know, i just want to double check.
[/QUOTE]
Sure you can use apt-get or wajig (apt-get frontend for the command line). We're technically still on Debian. :)

[QUOTE=d3c3it]
If i install hoary array 1, and i do a apt-get update apt-get dist-upgrade will the system be 100% up to date or when "The Hoary Hedgehog" goes stable do i have to reinstall?
[/QUOTE]
Array 1?
It depends what you mean up-to-date. But basically yes. With Hoary you're running bleeding edge.
No. There's no need to reinstall. Hey, we use APT which has the supercow powers. :) So updating and upgrading and sometimes dist-upgrading will point you to the final Hoary.

[QUOTE=d3c3it]
Can i still make my own kernels with make-kpkg or is it the preferred way to stay with binary premade kernels?
[/QUOTE]
As on almost every Linux distro out there it's up to you if you want the "stock" kernel or you compile your own.
Kernel-package is recommended way to compile kernels on all Debian-based distros.

[QUOTE=d3c3it]
I presume with ubuntu being based on debian all the above is a resounding yes i just wanted to check as i know ubuntu is based on debian just wondered if some things were different?
[/QUOTE]

Debian and Ubuntu
[http://www.ubuntulinux.org/ubuntu/relationship/document_view](http://www.ubuntulinux.org/ubuntu/relationship/document_view)

---

### Post by d3c3it on 2004-11-24
[QUOTE=p!=f]Sure you can use apt-get or wajig (apt-get frontend for the command line). We're technically still on Debian. :)


Array 1?
It depends what you mean up-to-date. But basically yes. With Hoary you're running bleeding edge.
No. There's no need to reinstall. Hey, we use APT which has the supercow powers. :) So updating and upgrading and sometimes dist-upgrading will point you to the final Hoary.


As on almost every Linux distro out there it's up to you if you want the "stock" kernel or you compile your own.
Kernel-package is recommended way to compile kernels on all Debian-based distros.



Debian and Ubuntu
[http://www.ubuntulinux.org/ubuntu/relationship/document_view](http://www.ubuntulinux.org/ubuntu/relationship/document_view)[/QUOTE]

Thats great, thanks very much for the input. Ahh yes, the apt super powers i forgot about that  :D 

Well what i meant by up todate was really if i install hoary array 1 and then just use apt to update will i be well uptodate but you answered that. Well ill be install ubuntu this weekend on my new laptop, no doubt ill be plagueing the forums.

Thanks again :)

EDIT I've got another question, i run a debian server, samba, icecast2 couple of other things, and apt-cacher. Would i be able to use my apt-cacher setup for the ubuntu repo's?

---

### Post by p!=f on 2004-11-24
[QUOTE=d3c3it]
EDIT I've got another question, i run a debian server, samba, icecast2 couple of other things, and apt-cacher. Would i be able to use my apt-cacher setup for the ubuntu repo's?[/QUOTE]
Sure.

---

### Post by d3c3it on 2004-11-25
[QUOTE=p!=f]Sure.[/QUOTE]
Great, well ill give it ago this weekend, thanks again for the input

---

