---
title: "procps error upgrade"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by trovador on 2013-10-24
Hi, I've read [http://ubuntuforums.org/showthread.php?t=1505356](http://ubuntuforums.org/showthread.php?t=1505356) but it doesent help me.
I have ubuntu 12.04 and upgrading this error
```
lucio@lucio-N61PA-M2S:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti saranno aggiornati:
  procps
1 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
1 non completamente installati o rimossi.
È necessario scaricare 0 B/225 kB di archivi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Continuare [S/n]? s
Configurazione di procps (1:3.2.8-11ubuntu6.1)...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: errore nell'elaborare procps (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
Si sono verificati degli errori nell'elaborazione:
 procps
E: Sub-process /usr/bin/dpkg returned an error code (1)
lucio@lucio-N61PA-M2S:~$ 
```
With **cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -** I've this output
```
lucio@lucio-N61PA-M2S:~$ cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -
kernel.printk = 4 4 1 7
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.use_tempaddr = 2
kernel.kptr_restrict = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
kernel.yama.ptrace_scope = 1
vm.mmap_min_addr = 65536
fs.inotify.max_user_watches = 524288
error: "Invalid argument" setting key "fs.inotify.max_user_watches"
lucio@lucio-N61PA-M2S:~$ 
```
I do not what to do to solve it.
Can help ?  please
Thank you

---

### Post by Chris_Keller on 2013-10-26
try adding new line? ('see for example: [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1241376]("https://bugs.launchpad.net/ubuntu/+source/procps/+bug/1241376")'.
check files for procps in directory upstart for error. In my case just needed to add a new line in one of the .conf's).

---

