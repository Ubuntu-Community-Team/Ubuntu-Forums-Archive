---
title: "Ubuntu installation as a server"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-03-02
Hi! I am looking to install ubuntu as my home server.  But, i have a question. When I boot the cd from the drive, it gave me a choice of either a default system or a server, but it says its just a base system. did somebody tried to install as a server? what is the difference between the defult and as a server? 

Currently, I installed as default, and if its really need to install as a server, I can re-install everything. but before hand, I want to ask the difference. what i want to run as a services are apache, php, mysql, postfix, pop3d, wu-ftpd, samba.

Thanks

---

### Post by drfloob on 2006-03-02
the "server" install option just installs the base system ... it's sortof a misnomer.  It doesn't actually install any server software (that I know of).  I heard of an ubuntu-server spinoff, but I haven't really looked into it.  here's the [release info]("https://lists.ubuntu.com/archives/ubuntu-announce/2005-December/000047.html").

A quick google search landed me here: [ISP-Server Setup]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10"): a breezy-specific how-to install apache, dns, ftp, pop3 ... servers.  This how-to begins with a server (base) install, but so long as you have the room on your hard drive, I doubt you'll have a problem getting your servers up and running with the full ubuntu setup you have now.

good luck.

---

### Post by lazyleg on 2006-03-02
I just installed Ubuntu breezy badger as a server vs since i had a old pc running with very small space on the MBR (2gig). The server installation needs 500MB, while the desktop (default) needs about 1.8 - 2 GB on a clean install. Earlier i used xp, and installed apache, php and mysql from scratch, wich always was a bitch since everything needed to be configured before it worked (even after configuration things wouldnt always work right). Havent tested much on the server yet, but after installing apache everything was up and running. I was stunned over how easy the setup was from installing ubuntu to installing packages like apache2, vsftpd. no configuration is needed to get things up and running, the only thing you need to do is to edit the settings afterwards to suit your needs. I think its overkill to install the default vs if you only going to use the pc as a server. Instead install the server, and add the packages you need later.

---

