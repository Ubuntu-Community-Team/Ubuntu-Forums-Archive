---
title: "Changing network location edits /etc/hosts"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by supergrover1981 on 2008-04-29
Hi gang,

I've just upgraded from Gutsy to Hardy, and I'm having a problem with network locations. Specifically, as soon as I choose a wireless location, any action which requires sudo brings up 'unable to resolve host linuxlaptop'.

I've tried adding "IP Address: 127.0.1.1, Aliases: linuxlaptop" to hosts, but it doesn't seem to have any effect.

Any suggestions deeply appreciated.

Cheers,
       - Supergrover

---

### Post by nowshining on 2008-04-29
it's 127.0.0.1 is your computer ip:

```
 

HOSTNAME="botnetgodalphamale" 
lo="lo 127.0.0.1"
INTERFACES=(lo)
127.0.0.1 localhost.localdomain localhost botnetgodalphamale


```

copy and paste that @ the top of your hosts file, but change botnetgodalphamale to your computers name.

Also if i'm a bit wrong as I don't have a network,

it's

ip url

ex:

127.0.0.1 [www.google.com](www.google.com)

means that if you tried visitting that site [www.google.com](www.google.com) ie: if you put that in the url box it will only connect back to your computer.

---

### Post by supergrover1981 on 2008-04-29
Hi,

Many thanks newshining for the reply. Your suggestion worked, but as before the /etc/hosts file reverted back to its default state as soon as I chose a location in network settings.

In short:
 (1) I could login, use sudo fine, and see my /etc/hosts edits
 (2) As soon as I chose a location in network-settings, the /etc/hosts file reverted back to its default state
 (3) Consequently, I could no longer use sudo

I eventually managed to work around it by removing "WORKGROUP" from the domain name in the network-settings location. The /etc/hosts file was rewriting 127.0.0.1 linuxlaptop to 127.0.0.1 linuxlaptop.WORKGROUP - removing the WORKGROUP parameter got rid of this problem. I'm not sure if this will effect my connection to networked windows machines, but at the moment I don't need that connectivity. :-)

Cheers,
         - Supergrover

---

### Post by nowshining on 2008-04-29
your welcome. :) I'm glad it all worked out for you.

---

