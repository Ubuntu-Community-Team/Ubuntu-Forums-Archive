---
title: "glassfish asadmin start-domain domain1 ERROR"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by cemaytar on 2008-04-30
I had installed glassfish on gutsy.
But when I try to execute:
```
asadmin start-domain domain1
```

it first asks for admin port, then I enter 4848.
After some time it says:
```

keytool error: java.io.IOException: Invalid keystore format
 
CLI130 Could not create domain, domain1

```

I'am new at application server usage, so there may be something I miss.

Thanks ..

---

### Post by togo59 on 2008-04-30
Strange, I've done this under Gutsy and not been asked for the port when running asadmin. Same under Scientific Linux: it never asks for a port number.

Normally the admin port is supplied during the install process.

Try a reinstall? Do you use Netbeans by any chance?

---

### Post by cemaytar on 2008-04-30
I use Netbeans. 
First I installed glassfish from netbeans plugins. But I think it only includes the bindings (it was just 2 mb)

Then I installed glassfish via synaptic. Then I tried-> asadmin start-domain domain1

---

### Post by togo59 on 2008-04-30
The full NB download (from the NB site) contains the latest glassfish (not just a plugin). I.e. either select "EE & web" or "All" on the download page. Advice: Go for "All" :)

When I installed it I did so without Synaptic. Anyways NB 6.1 is so cool you just have to have the latest version.

My advice: uninstall gf and download NB 6.1 (full version). The installer takes you through all the gf set-ups including ports, admin password etc.

\\:D/However, make sure you switch your display visual effects to none. The installer doesn't work otherwise. See [http://wiki.netbeans.org/InstallingNetbeansUbuntu7.04](http://wiki.netbeans.org/InstallingNetbeansUbuntu7.04)
for the full monty.

---

### Post by cemaytar on 2008-05-01
thanks ..

---

