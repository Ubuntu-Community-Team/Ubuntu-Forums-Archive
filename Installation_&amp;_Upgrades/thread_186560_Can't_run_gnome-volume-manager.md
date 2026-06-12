---
title: "Can't run gnome-volume-manager"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by dmalinovsky on 2006-06-02
After upgrading from Breezy to Dapper (it was RC version, today I upgraded to final release, but it didn't help my problem) I noticed my CD stopped automount—previously I've got CD icon on the Desktop after inserting, but now I just get nothing.

`lshal` shows correct results, after some digging I found out gnome-volume-manager is responsilble in Gnome for such things.  It should be run as daemon after my login, but it's not running!  I even tried to run it manually in foreground mode but it closes instantly.  I've generated `strace` output via:
strace gnome-volume-manager -n
it's attached to the post.  Maybe someone smarter can give me a hint what else should I try...

---

### Post by barna.kosa on 2006-06-02
The same thing happened to me after I upgraded Breezy to Dapper on two notebooks. Tracing with strace gives a is very similar output. I belive this is not an isolated  problem and somebody will find a solution.

---

### Post by dmalinovsky on 2006-06-05
Maybe it's significant---my user account is handled via LDAP, we're using LDAP server which stores user data for /etc/passwd etc.  I have libnss-ldap package installed to make it work on my side.
I also tried to remove hal, gnome-volume-manager and their dependencies (even purged them via `aptitude purge`) and installed them again with no success.

Does anyone know how to debug gnome-volume-manager better?

---

### Post by dmalinovsky on 2006-06-09
Eventually I fixed this problem&#8212;I completely removed (i.e. purged) all the packages related to gnome-volume-manager (`deborphan -an` is your friend! :) ) and installed ubuntu-desktop package again.  Now everything works ok.

---

### Post by daveg on 2006-06-28
[QUOTE=dmalinovsky]Eventually I fixed this problem—I completely removed (i.e. purged) all the packages related to gnome-volume-manager (`deborphan -an` is your friend! :) ) and installed ubuntu-desktop package again.  Now everything works ok.[/QUOTE]
Any chance of getting a more detailed explaination? I've removed g-v-m a few times now, ran wajig purge-orphans and reinstalled it.

No joy. This is sh*tting me... ](*,)

---

### Post by dmalinovsky on 2006-06-28
[QUOTE=daveg]Any chance of getting a more detailed explaination? I've removed g-v-m a few times now, ran wajig purge-orphans and reinstalled it.

No joy. This is sh*tting me... ](*,)[/QUOTE]
Sorry, but I was wrong.  After a reboot it happened to me again.  I [filed a bug]("https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/49666") into Ubuntu bug tracker, but haven't got any reply yet.

---

### Post by dakine_1111 on 2006-07-01
I solved the problem by adding

session optional pam_foreground.so

to the end of /etc/pam.d/common-session

maybe you have to create /var/run/console.

/etc/pam.d/common-session

session required pam_unix.so
session optional pam_foreground.so

---

