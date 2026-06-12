---
title: "Package Not Upgraded"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2012-10-30
[INDENT][I]arv@arv-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
arv@arv-desktop:~$ [/I][/INDENT]

Which package was not upgraded?
Why was it not upgraded?
Do I need to do anything about this?

---

### Post by snowpine on 2012-10-30
I recommend:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then you will see what the upgrade is and you'll have the opportunty to choose Y or N. If you're not sure then choose N and post back here (copy & paste the terminal output).

---

### Post by arvevans on 2012-11-09
That was helpful and informative:

[INDENT]Reading package lists... Done
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
arv@arv-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grace
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
arv@arv-desktop:~$ [/INDENT]

Seems that "grace" is the package that was not upgraded.

After the "dist-upgrade" I was able to do "sudo apt-get install grace" successfully.  From the install output it looks as if grace was actually installed but 2 needed libraries were missing:

[INDENT]Setting up libhdf5-7 (1.8.8-9) ...
Setting up libnetcdfc7 (1:4.1.3-6) ...
Setting up grace (1:5.1.22-13) ...[/INDENT]

Now "grace" works and I don't have the error message.

Thanks for the assistance.

---

