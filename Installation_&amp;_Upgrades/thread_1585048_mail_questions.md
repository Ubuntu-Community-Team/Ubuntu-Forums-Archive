---
title: "mail questions"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2010-09-30
I'm having trouble with mail on my two boxes recently upgraded to 10.04.  

I don't think I need a mail server, but the packages seem to have been installed on one machine - perhaps as a result of installing apticron.  How can I uninstall the packages?  Synaptic has a way to figure out the group of packages to install, but doesn't seem to have the reverse.

Does apticron (or any other package that sends mail) need a mail server, or can I just configure something to use my external SMTP server?  I thought that's what I had before.

TIA.
Mike

---

### Post by P4man on 2010-09-30
Synaptic does have the "reverse". If you select postfix (which I suspect is the mail server you ended up with) for removal, it will prompt you with all packages that depend on postfix, and that therefore will have to be removed as well.

BTW, having postfix installed I dont think autmatically runs the mailserver service. I dont think its a problem having it installed, and a lot of apps depend on it for some reason.

---

### Post by 5circles on 2010-09-30
Thanks.  I selected Postfix for uninstallation, and Synaptic added bsdmailx and apticron too.   Now the 'choose packages by task' no longer shows mail server checked so that's reassuring.

You may be right about Postfix not being much of an issue - and apticron seems to require it - but I wasn't able to figure out how to configure postfix quickly so no mail was being sent by apticron.

I don't understand why apticron expects a mail server as all it has to do is send mail.  I was just hoping to send mail via my external smtp server.  But I guess I'll have to figure out the mail server.

---

