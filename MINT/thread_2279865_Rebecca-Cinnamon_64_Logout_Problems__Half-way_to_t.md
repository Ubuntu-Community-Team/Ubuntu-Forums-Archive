---
title: "Rebecca-Cinnamon 64: Logout Problems / Half-way to the solution"
date: 2015-05-26
forum: MINT
---

### Post by MikeMecanic on 2015-05-26
There seems to be 2 sessions running in Linux Mint 17.1 when I logout.  A message tells me that I'm already login and I must choose the second name that appears in the pop up message.  Those 2 names are related to the installer names that I choose and are the terminal names.  When this occurs I'm in loop hard to get out.  

When in the settings and disable Automatic login and Enable Timed Login.  The second session is not shown no more.  But, this morning I was ask to enter my password on boot up with the same lougout screen?   During the installation I choose automatic login so that I don't have to enter a password each time I boot.


**Is there a way to remove the second session** like in Ubuntu that offers the possibility to remove guess session using this terminal command: ```
sudo sh -c 'printf "[SeatDefaults]\nallow-guest=false\n" >/usr/share/lightdm/lightdm.conf.d/50-no-guest.conf'

```

Thanks in advance,

---

### Post by MikeMecanic on 2015-06-02
Houston! We have an unknown intruder unable to kill?  We don't know where he is, we don't know is privileges, we were not able to kill I'm using Mint 16 method, we don't know if he acts like a second user or a second session or even if there's a third one?  Sooner or later, we will be force to delete related partitions.   [I] 
Be prepare for exit code, it appears that Linux Mint Programmers have problems[/I].   


**We did it (Mint 16 Method) but he comes back on ****boot-up**
[http://unix.stackexchange.com/questions/45573/how-to-disable-auto-login-in-linux-mint](http://unix.stackexchange.com/questions/45573/how-to-disable-auto-login-in-linux-mint)
**We succeed doing so**
[http://forums.linuxmint.com/viewtopic.php?f=208&t=154554http://](http://forums.linuxmint.com/viewtopic.php?f=208&t=154554http://)
**Waiting for 2.0 but we succeed doing it under 1.8.3**
[http://segfault.linuxmint.com/2015/03/better-session-detection-in-mdm-2-0/](http://segfault.linuxmint.com/2015/03/better-session-detection-in-mdm-2-0/)
```
$  apt policy mdm
mdm:
  Installed: 1.8.3+rebecca
  Candidate: 1.8.3+rebecca
  Version table:
 *** 1.8.3+rebecca 0
        700 http://packages.linuxmint.com/ rebecca/main amd64 Packages
        100 /var/lib/dpkg/status
     0.1.3-2.1 0
        500 http://ubuntu.mirror.iweb.ca/ trusty/universe amd64 Packages
```

---

### Post by MikeMecanic on 2015-06-14
Recap
On first installation the terminal names were $ ibm@IBM with 963 password.  The Sudo User was IBM and I was in loop with no end on Logout: was ask to change user session in a **** up manner. On second installation, the terminal names were $ mac@mac with the same password.  I thought that by using the same names I would disable the second session that appears to be *Session Cinnamon* and the Sudo one is *Cinnamon Session*.  Both I kept the same password and the Sudo user was IBM.  Under Mint, we are able to change the computer name, so I change it to mac.
On third installation, I choose nec@NEC and I change the password (knowing that when you keep the same password many things occur) for 3 other numbers.  Didn't fix nothing,

So I when in deep settings:  First link of post # 2 fix the boot up issue but I enable automatic login: no password to enter on boot up.  The second link create a fatal error (the one when you try to logout under 10 seconds).   The third link ended in a black screen on boot up:  **the first time in 2 weeks**.  So I did a third installation and switch to Rebecca Romeo:  Settings are redefine and more friendly user, a lot to do with Windows ones.  **I delete the Users and Groups privileges and this folder is not shown anymore**.  But I login under the same name, I'm not ask YOU ARE ALREADY LOGIN no more.  I kill the process under System Monitor (Task Manager) Cinnamon Session but it responded normally: Logout as usual.

So I'm at two-third of the solution now.  This problem last since Mint 12 at least and no one seems to be able to fix it.  I'm discussing security issue and I don't believe that an OS can come out _with a gap like that one_.  Still working on it and except for the folder that disappear it's quite and stable.
```
nec@NEC ~ $ cinnamon --version
Cinnamon 2.6.7

```

---

