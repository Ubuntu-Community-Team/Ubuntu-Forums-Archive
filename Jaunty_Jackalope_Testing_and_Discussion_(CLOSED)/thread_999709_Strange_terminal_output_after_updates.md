---
title: "Strange terminal output after updates"
date: 2008-12-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-12-02
Did 48 updates this morning. Wondering what the posted output from terminal means and if it's some thing I need to fix or will it resolve itself.
Could some one please explain what it all means to me?
Thanks
```
Setting up powernowd (1.00-1ubuntu3) ...
Installing new version of config file /etc/init.d/powernowd ...
update-rc.d: warning: /etc/init.d/powernowd.early missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Starting powernowd...                                                                                                                    * CPU frequency scaling not supported...                                                                                           [ OK ] 

Setting up samba-common (2:3.2.5-1ubuntu1) ...
Replacing config file /etc/samba/smb.conf with new version

Setting up smbclient (2:3.2.5-1ubuntu1) ...
Setting up winbind (2:3.2.5-1ubuntu1) ...
 * Starting the Winbind daemon winbind                                                                                              [ OK ] 

Setting up transmission-common (1.40-0ubuntu1) ...
Setting up transmission-gtk (1.40-0ubuntu1) ...

Setting up tsclient (0.150-1ubuntu4) ...

Setting up xterm (237-1ubuntu1) ...

Setting up accerciser (1.5.2-0ubuntu1) ...

Setting up firefox-3.1-branding (3.1~b2+build1+nobinonly-0ubuntu1) ...
Setting up kdelibs-bin (4:4.1.80-0ubuntu1) ...
Setting up firefox-3.1 (3.1~b2+build1+nobinonly-0ubuntu1) ...
Please restart all running instances of firefox-3.1, or you will experience problems.

Setting up firefox-3.1-dev (3.1~b2+build1+nobinonly-0ubuntu1) ...
Setting up firefox-3.1-gnome-support (3.1~b2+build1+nobinonly-0ubuntu1) ...

Setting up kdelibs5 (4:4.1.80-0ubuntu1) ...

Setting up kdebase-runtime-bin-kde4 (4:4.1.80-0ubuntu1) ...
Setting up kdebase-runtime (4:4.1.80-0ubuntu1) ...

Setting up khelpcenter4 (4:4.1.80-0ubuntu1) ...
Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Compiling /var/lib/python-support/python2.5/orca/speechgenerator.py ...
  File "/var/lib/python-support/python2.5/orca/speechgenerator.py", line 179
    """Returns a list of utterances that describe
                                                
^
SyntaxError: EOF while scanning triple-quoted string

```

---

### Post by shirishagarwal on 2008-12-02
powernowd is basically to control the voltage of your cpu or cpu's (if its a multi-processor machine) from inside the OS. Also works for laptops. 

Orca on the other hand is to do with accessibility.
[http://live.gnome.org/Orca](http://live.gnome.org/Orca)

 You should report that error which you got.

---

### Post by DougieFresh4U on 2008-12-02
> **shirishagarwal said:**
> powernowd is basically to control the voltage of your cpu or cpu's (if its a multi-processor machine) from inside the OS. Alsow works for laptops. 

Orca on the other hand is to do with accessibility.
[http://live.gnome.org/Orca](http://live.gnome.org/Orca)

 You should report that error which you got.

May sound stupid but how would I report and would it be an 'orca' bug?

---

### Post by ronacc on 2008-12-02
first you need to register on launchpad    [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)   then you will be able to file bugs or comment on ones filed by others . It does look like orca would be the package to file it against but you also could just post the terminal output into your bug report and leave the package as unknown .

---

### Post by DougieFresh4U on 2008-12-02
> **ronacc said:**
> first you need to register on launchpad    [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)   then you will be able to file bugs or comment on ones filed by others . It does look like orca would be the package to file it against but you also could just post the terminal output into your bug report and leave the package as unknown .

Been a while since I used launchpad, but I dug out my info and reported.
Bug #304592

---

