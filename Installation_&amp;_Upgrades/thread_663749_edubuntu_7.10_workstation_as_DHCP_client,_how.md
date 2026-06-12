---
title: "edubuntu 7.10 workstation as DHCP client, how?"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by dbc_too on 2008-01-10
Hello,
  This may be a FAQ, but searching here and googling isn't turning up what I need.

  My goal is to set up my daughter's computer as an Edubuntu 7.10 workstation configuration, dual booting with XP. While waiting for the .iso to download, I'm looking over the release notes.  The installation instructions for Edubuntu talk about how to configure a static IP, but not how to set up the workstation as a DHCP client.  Is there a howto someplace that I am not finding?  It also looks like Edubuntu wants to be the DHCP server -- I need to shut that off.

What I am trying to do:
Target machine will dual boot XP and Edubuntu 7.10 as DHCP client.
The network DHCP server is the home file server (Gentoo).
The edubuntu client will also need to have NFS access to the file server.

TIA
  Dave

---

### Post by maybeway36 on 2008-01-18
DHCP client (getting IP address automatically) is the default. It requires no setup. If you "install a workstation," no DHCP server wil be installed.

---

