---
title: "samba problems in Dolphin and Konqueror"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aj237769 on 2008-10-21
After installing the latest package updates to Kubuntu 8.10 (II), I can no longer connect to any smb file shares on my LAN from Dolphin or Konqueror.  I know they are still configured correctly as I can boot any machine to Windows and connect, read, write...just about anything I want to do.  I'll also note that one of my machines hadn't been upgraded in about a week and before I went through the adept upgrades today, that machine seemed to be working.

Using smbclient -L <hostname> appears to give the correct results, subsequently connecting via a terminal using smbclient ALSO seems to work.

Dolphin > Network > Samba Shares >
I can see icons for the high-level shares but clicking one results in "File or Folder smb://<hostname> does not exist."

Konqueror > Entering 'smb://<hostname>' results in same error.

I've attached the smb.conf file from the samba server I have set up one one of my machines.  The overall architecture I have is as follows:

Sony Vaio - Kubuntu 8.10 (II) - Windows Vista - Samba Server Active
Dell DIM4600 - Kubuntu 8.10 (II) - Windows XP
Russound SMS3 Mediaserver (linux based but not sure abt details)

Has anyone else run into this after the latest round of upgrades?  If so any/all suggestions are appreciated.

--I just finished installing today's updates and rebooted, still no luck.  I'm attaching the results of smbtree too, not sure if there is something i'm missing.  Windows can still see and use all shares.

--Could this be an issue with kio_smb as opposed to samba server or smbclient?

---

