---
title: "[SOLVED] Distribution upgrade hangs"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by JackTheKnife on 2008-07-24
I'am trying to do distribution upgrade from 7.10 to 8.04 and I'am on Installing the upgrades stage (77% done) but upgrade seems to freeze on

```

Generating locale...
en_AU.UTF-8...

```

So what can I do to finish distro upgrade :confused: There is no skip or cancel button :mad: Thanks

---

### Post by Pumalite on 2008-07-24
Try changing Server.

---

### Post by JackTheKnife on 2008-07-24
How can I do this?

---

### Post by Pumalite on 2008-07-24
System>Administration>Software Sources>Change the Server
(in Ubuntu Hardy)

---

### Post by JackTheKnife on 2008-07-24
OK, but how can I resume distro upgrade after that?

---

### Post by Pumalite on 2008-07-24
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by JackTheKnife on 2008-07-24
After sudo dpkg --configure -a i have

dpkg: status database area is locked by another process

](*,)

---

### Post by Pumalite on 2008-07-24
Close Synaptic. or other process using apt-get.

---

### Post by JackTheKnife on 2008-07-24
It was closed...

---

### Post by Pumalite on 2008-07-24
Maybe you can just click on the updater to continue.

---

### Post by JackTheKnife on 2008-07-24
I can not do anything when I closed updater. When I open again I got message:

Another process is using the packaging system database. 

:twisted:

---

### Post by Pumalite on 2008-07-24
Reboot

---

### Post by JackTheKnife on 2008-07-24
Even I can not to kill dpkg process

---

### Post by JackTheKnife on 2008-07-24
When I will reboot it will not boot to the system because distro upgrade didn't installed to the end...

---

### Post by Pumalite on 2008-07-24
You might be right. Keep on looking where is the process.

---

### Post by JackTheKnife on 2008-07-24
I have Python tree with dpkg and locales.postins runing gzip, but I can not to kill any of them. It says "Insufficient permission to kill process". What is sudo command line to that?

---

### Post by gcee on 2008-07-24
found this...

run the dist-upgrade as recommended. If the process hangs at generating locales, taking more than 20min for the first one and still not continuing:

chmod 644 /usr/bin/localedef
killall locale-gen

now the process should continue, but throwing a bunch of errors (simply ignore those). If it still not continues, check whether locale-gen has really been killed (ps aux|grep locale-gen) and repeat "killall locale-gen" until it's gone.

When update-manager is done, don't forget to

chmod 755 /usr/bin/localedef

---

### Post by JackTheKnife on 2008-07-24
Thanks a lot! I hope it will works! \\:D/

---

### Post by gcee on 2008-07-24
worked for me

best of luck

---

### Post by tova on 2008-08-20
my computer does not allow me to kill the proccess. what do i do?

---

### Post by Coombabah on 2008-08-25
> **gcee said:**
> found this...

run the dist-upgrade as recommended. If the process hangs at generating locales, taking more than 20min for the first one and still not continuing:

chmod 644 /usr/bin/localedef
killall locale-gen

now the process should continue, but throwing a bunch of errors (simply ignore those). If it still not continues, check whether locale-gen has really been killed (ps aux|grep locale-gen) and repeat "killall locale-gen" until it's gone.

When update-manager is done, don't forget to

chmod 755 /usr/bin/localedef

Thanks. This has worked for me on a few upgrades Ubuntu 7.10 to 8.04.1

---

