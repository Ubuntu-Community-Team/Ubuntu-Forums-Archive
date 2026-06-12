---
title: "samba, sharing directories with windows"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by JvA on 2005-06-06
I want to be able to share directories or files with windows on a network.
First thing I tried was just System>Administration>Shared folders, but it tells it needs Samba or NFS and that neither is installed.. So I look in Synaptic, and it looks like Samba is installed (can't find NFS anywhere)..

I'm almost completely new to linux, but I did use Samba once on another computer, so figuring it's probably not set up correctly, I take a look at:
[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba)
Which says something like you will need the 'General' tab in 'Network Settings' (Networking) and then 'Windows Networking'.. Makes sense.. but.. there is no 'Windows Networking' in my 'General' tab, only 'Host Settings'..

Can somebody tell me what I should do, or maybe, if the wiki page is just outdated, where else I can find what I should do??

BTW, I did find the configuration file of samba, but thought it'd probably be better to ask around before trying editing anything myself..

---

### Post by jiyuu0 on 2005-06-06
you might want to check [www.ubuntuguide.org](www.ubuntuguide.org)
there's a section on samba

---

### Post by JvA on 2005-06-06
Thanks, well, it says you should install samba with 'sudo apt-get install samba,' but 'samba has no installation candidate,' but I'll give the rest of it a try since samba seems to be installed already..

---

### Post by JvA on 2005-06-06
Well... the whole apt-get samba part doesn't work, but it gives me the option of installing two other packages (samba-common and smbclient), but when I try to install them it says the newest versions of both packages are already installed...?

I'm still getting the message that samba isn't installed when I try to access the Shared folders dialog..

---

### Post by JvA on 2005-06-06
Okay.. this may sound very silly, but could it help if I install a gui for samba (different from Shared folders dialog) or will this also not work if the Shared folders thing doesn't recognise any samba installation?

---

### Post by JvA on 2005-06-06
Never mind, I used Places>Network Servers and did what I wanted to do, thanks.

---

