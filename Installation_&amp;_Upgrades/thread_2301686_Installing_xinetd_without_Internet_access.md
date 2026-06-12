---
title: "Installing xinetd without Internet access"
date: 2015-11-04
forum: Installation &amp; Upgrades
---

### Post by rob151 on 2015-11-04
I am logged into a server via PuTTY. I am trying to install xinetd on a server that does not have Internet access. Thus, this command doesn't work.

sudo apt-get install xinetd

I'm trying to find a manual way around this. I **am** able to transfer files to this server using SCP.

Looking for guidance. Much appreciated.

Rob
[ATTACH=CONFIG]265360[/ATTACH]

---

### Post by SeijiSensei on 2015-11-04
You can download the appropriate package from here: [http://packages.ubuntu.com/trusty/xinetd](http://packages.ubuntu.com/trusty/xinetd)

This is for 14.04LTS which is the current release with long-term support.  For other versions, you'll need to navigate to the relevant page from the link above.  Once you have the .deb file, you can copy it to the server, then use "sudo dpkg -i package_name.deb" to install it.

Trying to work on an Ubuntu server without Internet access is like having your arms and legs chopped off.  Is there some reason this machine cannot be connected to the Internet?  If you were using an Ubuntu client rather than Windows (I assume since you're using Putty), you could set up an SSH tunnel on the server back through the client for Internet connectivity.

You could also put the distribution's CD in the machine's optical drive and install from that.  Here's the relevant page for Ubuntu Server 14.04LTS: [http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/current/).  If it doesn't have an optical drive, you can copy the entire ISO image onto the machine and mount it like this:
```
sudo mount -o loop /path/to/somedistro.iso /mnt
```
That makes all the directories and files on the ISO available at /mnt.

---

