---
title: "Creating a bugreport without the bugreport tool"
date: 2022-02-07
forum: Installation &amp; Upgrades
---

### Post by 9hax on 2022-02-07
Hi to you all,

I found a bug in the installation program at the step where you do the user setup.
If you intend to use Active Directory, entering an invalid user name in the user setup Softlocks you in the Active Directory Setup screen.
For example: set up the login name of your local user as "admin", which is invalid, since its already being used by ubuntu, then click on "Use Active Directory" and click next.
Since the Back Button is greyed out in the AD Setup screen, you cannot go back to fix the "admin" login name, and after entering your AD credentials you are not brought back.
This effectively softlocks the installer.

My question is: where do I submit a bugreport for the installer?
Running the ubuntu-bug utility says that it cannot find the installer PID and therefore cant generate a bug report.

Thanks in advance, 
9hax

---

### Post by MAFoElffen on 2022-02-07
In the installer... Press <Alt><F2> to get to a shell...
```

ubuntu-bug <package_name>

```
The package_name will be either 'debian-installer' (old installer) or 'ubiquity' (newer installer), depending if you are installing 20.04 Desktop, 20.04 Server or later of either...

For instance for 21.10 Desktop Edition:
```

ubuntu-bug ubiquity

```

---

