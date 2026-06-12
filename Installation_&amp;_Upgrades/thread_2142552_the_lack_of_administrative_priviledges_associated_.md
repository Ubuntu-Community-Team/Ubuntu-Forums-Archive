---
title: "the lack of administrative priviledges associated with your user account"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by arexsekerat on 2013-05-06
Hye guys i got this error when i  install and purge packages  .. also problem when i run command reboot or another command a terminal tell me run using /sbin/<packages> or /usr/sbin/<packages> .. anybody help me please .


1: error on terminal .. 

dpkg: warning: 'ldconfig' not found on PATH.
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: warning: 'update-rc.d' not found on PATH.
dpkg: 3 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

2: error on terminal ..

The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative priviledges associated with your user account.


Thank You .

---

### Post by lisati on 2013-05-06
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) should help you with the administative privileges that you might need for some tasks.

---

### Post by schragge on 2013-05-06
Wouldn't dpkg bail out even before trying to execute anything if not being run under sudo? In this case, I'd rather suspect a wrongly set *secure_path* in */etc/sudoers* or something like this.

---

### Post by arexsekerat on 2013-05-06
my /etc/sudoers 

Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

---

### Post by schragge on 2013-05-06
So, */etc/sudoers* looks okay. Let's try to find out where the wrong PATH comes from. Please post the output of following commands:
```
sudo sh -c 'echo $PATH'
```
```
echo 'echo $PATH'|sudo -s
```
```
pkexec sh -c 'echo $PATH'
```

---

