---
title: "Installing Ubuntu from Windows XP PXE"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by WildFoxMedia on 2008-12-01
Hi everyone, I found a couple tutorials on installing Ubuntu with PXE via a local FTP server.

My situation is slightly different in that the only networking that the new comp will have is Wireless and that is provided via a USB adapter.

I got the initial PXE setup and Ubuntu boots from it, but when it comes time to download the installer/packages it cant connect to the internet. Since I cant get the USB adapter to work during the install (or just dont know how) I am connecting the new comp to my laptop with an ethernet cable (My laptop has internet Wirelessly from the router).

Internet Connection Sharing gets me to the point where the FTP server is recognized and the PXE works, but will ICS also connect through my Wireless to the outside world? I tried doing a network bridge but you can only bridge 2 connections that dont use ICS.

Is this possible?

---

### Post by mic159 on 2008-12-02
You dont need to get on the internet to install with PXE, you can mirror the install CD on your local PC (get the files from the ISO) and set the mirror to the PC that is hosting the files. The only way i know is to have them on a HTTP server (eg use apache or [HFS]("http://www.rejetto.com/hfs/") to serve the files over the network to the target machine)

I have not been able to do this with 8.10 (I tried the server version) yet because it seems to be missing some files on the CD... -.-
but i have done this with all previous versions.

---

