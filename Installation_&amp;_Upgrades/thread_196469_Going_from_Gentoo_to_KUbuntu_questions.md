---
title: "Going from Gentoo to K/Ubuntu questions"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by jabster on 2006-06-14
Hi

I currently have a gentoo server setup as samba (domain controller), email server (courier-imap-ssl, fetchmail, proc, spamass, squirrelmail), mysql, local web server, and NFS server.

Basically, I am starting to get tired of waiting for things to compile, and then updating all sorts of config files after each update. So I want to install U/Kubuntu as a server there instead.

What sort of issues am I going to encounter during this upgrade? Specifically:
1. LVM: my main shares (music & web/pictures) are LVM. SInce I'll only be formatting the "/" partition, this shouldn't really be a big concern, correct? As long as I keep track of which partitions are LVM before upgrading, and then just proceed per the LVM How-to ([http://www.tldp.org/HOWTO/LVM-HOWTO/)?](http://www.tldp.org/HOWTO/LVM-HOWTO/)?)
2. No root. Anything in particular to watch out for here? Mainly regarding webmin, which I use for most of my LVM admin (as far as I can anyways).
3. Kubuntu or Ubuntu? I won't be installing X here at all. Does it matter which I use? Or are they truly the same thing except for KDE/Gnome?
4. Any other pitfalls to be aware of before I do this?

Thanks,
john

---

### Post by stlutz on 2006-06-15
Regarding #2, there is a root user--you just need to enable it.  See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

---

### Post by ubuntu27 on 2006-06-15
[Try Ubuntu Server](http://www.ubuntu.com/server) It dosn't install X at all. So no worries whatever you need Ubuntu, Kubuntu or Xubuntu.

The iso that you will need is "ubuntu-6.06-server-i386.iso: [I'm assuming your comp is x86] 

The download are here: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

And maybe this will be your help: [https://wiki.ubuntu.com/Servers](https://wiki.ubuntu.com/Servers)

---

