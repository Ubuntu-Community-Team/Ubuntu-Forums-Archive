---
title: "Error during samba update"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by JackTheKnife on 2012-04-23
I'm getting that error during update process:

```

Can't exec "/tmp/libssl0.9.8.config.296591": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /tmp/libssl0.9.8.config.296591 configure 0.9.8k-7ubuntu8.8 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
libssl0.9.8 failed to preconfigure, with exit status 255
Can't exec "/tmp/samba-common.config.296593": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /tmp/samba-common.config.296593 configure 2:3.4.7~dfsg-1ubuntu3.8 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
samba-common failed to preconfigure, with exit status 255

```

Any clue what is going on?

Thanks

---

### Post by Paddy Landau on 2012-04-24
How were you trying to update Samba? What version of Ubuntu do you have?

---

### Post by JackTheKnife on 2012-04-24
Ubuntu 10.04 and using Update Manager

PS.

I looks like common update issue. Now I have problem with MySQL update:

```

Preconfiguring packages ...
Can't exec "/tmp/mysql-server-5.1.config.24401": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /tmp/mysql-server-5.1.config.24401 configure 5.1.61-0ubuntu0.10.04.1 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
mysql-server-5.1 failed to preconfigure, with exit status 255

```

---

### Post by Paddy Landau on 2012-04-25
Are you using Ubuntu or one of the derivatives, such as Xubuntu?
Are you using WUBI or a native installation?

Please open a terminal (Accessories > Terminal if I remember correctly, or Ctrl-Alt-T), and enter the following commands. Please post the results here.
```
sudo apt-get update
sudo apt-get upgrade
```

---

