---
title: "Suggestions for alternative network boot methods"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by quentinsf on 2006-09-27
I have a machine - a remotely-hosted server - currently running Fedora.  I want to switch it to Ubuntu, but I don't have physical access to the machine.

I do, however, have a nice remote control panel which lets me see the console, boot from an uploaded floppy image, or boot from an ISO image on a Windows share. All very clever.

Can anyone offer suggestions about getting Ubuntu going on this machine?

My first thought was just to put the standard install CD image on a Samba share on one of my other machines.  But while I can mount the share locally on the server machine using smbclient, I haven't had any success mounting it from elsewhere - my guess is that many ISPs assume that allowing remote SMB access is a bad idea and so block the ports.  I've tried on two different servers without success; smbclient reports a failure to connect to port 445.  So if anybody has a Samba/Windows share I could connect to with a Dapper install disk on it, I'd be most grateful!

The other option I can think of is to try and create an etherboot floppy image, which will allow me to specify the local IP address and start a boot from a specified remote TFTP server.  Is that possible?  Sound good?

Any recommendations gratefully received before I plunge into this!

---

