---
title: "Intrepid: gnome-keyring-daemon gconf error"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cbkm on 2008-10-27
Hi,

To work around an existing issue in hardy ([gnome-keyring-daemon not honoring constrained ssh identities](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/209447)) I've set the ssh component of gnome-keyring-daemon in gconf to be disabled so I can use the standard ssh-agent which supports constrained ssh identities. 

I've just upgraded to Intrepid RC and I noticed that the gnome-keyring-daemon was still starting its ssh component even though it is configured not to. 

Running it on the commandline turns up the following and searching Google yielded nothing. :-(

```

$ gnome-keyring-daemon
gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Not running within active session)
gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Not running within active session)
** Message: another SSH agent is running at: /tmp/ssh-kWxdNx8484/agent.8484
gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Not running within active session)
GNOME_KEYRING_SOCKET=/tmp/keyring-vAeFOz/socket
SSH_AUTH_SOCK=/tmp/keyring-vAeFOz/ssh
GNOME_KEYRING_PID=9608

```

Anyone have any ideas? (It's clear to me that it's defaulting to running the ssh component because it's unable to lookup the config value.)

---

### Post by Sef on 2008-10-27
moved to ibex.

---

### Post by cbkm on 2008-10-27
Hmm, ignore the errors in my previous thread - they're a red herring since I was testing gnome-keyring-daemon from a ssh-session into the box, ofcourse there was no active session.... :-/

It's still running the ssh component though, for some reason...

Edit:-

Ok, thinking out loud here... I'm wondering if it's some sort of race condition or something... My home directory is encrypted so it needs to be mounted from pammount during logon, but, if gnome-keyring-daemon runs before that my gconf settings won't be available at that time and it'd default to running the ssh component in lieu of any user config.

---

