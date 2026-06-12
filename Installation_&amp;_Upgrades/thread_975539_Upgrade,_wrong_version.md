---
title: "Upgrade, wrong version????"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by quikone8 on 2008-11-08
I have upgraded from 8.04 to 8.10 on a Dell laptop and notice a few bugs! One is no sound and the other is it seems that the software configured as server rather than desktop. When shutdown or restart is started the laptop goes through a few shutdown steps, which seem rather odd; one is it attempts to shutdown a non-existent Apache server, Cups server and a few other server related functions. Could it be that one of the upgrade servers had the wrong instructions or the wrong upgrade? If not why won't the laptop shutdown, it just hangs.:confused:

---

### Post by cariboo on 2008-11-08
To check what version you are running in a terminal type:

```
uname -a
```

If you are running the desktop version you should get an output something like this:

```
 uname -a
Linux alexis 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
```

If you are running the server the output should look like this:

```
 uname -a
Linux willy 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux

```

Cups is the printing service, you need this to print, you may have installed a package that needs apache2.

To see what services are running on your computer, and what ports are open go to System-->Administration-->Network Tools-->Port Scan,
enter localhost for network address. If you are running a default installation the only port open should be 631 which cups uses and is only accessible from your computer. Any other open ports mean you have installed other services.

Jim

---

### Post by quikone8 on 2008-11-08
This is what it looks like;

80     open    www
139    open    netbios-ssn
445    open    microsoft-ds
631    open    ipp
58724  open    unknown

How can I close these permanetly without hurting anything?

---

