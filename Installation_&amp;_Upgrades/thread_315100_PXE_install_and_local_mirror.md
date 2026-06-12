---
title: "PXE install and local mirror"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by dummkauf1980 on 2006-12-08
I am trying to install ubuntu on a laptop over the network.  I can get the laptop to boot via the PXE server, but I want to set up a local mirror on my network from an Ubuntu DVD that I have.  I Have copied the necessary directories over to my server and have tried serving them out via HTTP (apache) and VIA ftp, but every time I point the install at the HTTP or FTP site it says it is not a valid mirror.  Is there some kind of a configuration file that needs to be placed on the server for the installation to recognize it and pull files from it?? or am I missing something else here as well?


*Note*
I do not want to run a full mirror downloading every package for every version of Ubuntu.  I only want to be able to install Hoary along with the packages that came on the DVD.

---

### Post by unfaigui on 2006-12-16
I am trying what exactly that you do too. I have the same problem. The client can boot of the pxe but it has never to see my ftp at all. May I ask you about the files that you put on the ftp server? I don't know exactly what files i need on my ftp. I just put all the files that on the Ubuntu-alternative-Dapper CD. Is this correct files that I need on my ftp?  If all the files from the CD are not correct, please tell me what files that i need to upload to my ftp.

Maybe i upload the wrong files on the ftp so the client  are looking some files on the ftp to start and continue install.

I hope there is someone has done this before.

unfaigui

---

