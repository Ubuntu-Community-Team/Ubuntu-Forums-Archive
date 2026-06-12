---
title: "SSH Tunneling questions"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-13
When I use SSH in winXP I have the following options under Tunneling->Outgoing:

Display name:
Type:
Listen port:
Allow Local connection only:
Destination Host:
Destination port:

Is it possible to specify the same options in linux in my ssh_config file and what are they called??

---

### Post by dataw0lf on 2005-04-13
These are all passed as arguments to the ssh -L command.

---

### Post by pestilence4hr on 2005-04-13
[QUOTE=bigblop]When I use SSH in winXP I have the following options under Tunneling->Outgoing:

Display name:
Type:
Listen port:
Allow Local connection only:
Destination Host:
Destination port:

Is it possible to specify the same options in linux in my ssh_config file and what are they called??[/QUOTE]
 To elaborate on dataw0lf's comment:  (I don't think you should modify the ssh configs to accomplish this)

here are a couple of examples.  To tunnel a vnc session on display :1, do this:

ssh -N -n -L 5901:localhost:5901 username@remotehost

To tunnel a the standard X connections, do this:

ssh -X username@localhost

Note that with the "realvnc" client, you can accompish the first example through "vncviewer -via username@remotehost localhost:1" command.

---

