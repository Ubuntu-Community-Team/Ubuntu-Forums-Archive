---
title: "Help, newbie for server installation"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Jorel on 2012-07-04
Hi guys, sorry for the bother, but im interested in building a headless file-server (at least) but is there any TUT here that is not for any VMware or VMBox? appreciated any help in advance,, ):P

---

### Post by matt_symes on 2012-07-04
Hi

Welcome to the forums jorel.

This link below is the standard Ubuntu help on servers. Take a read through and if you have any questions then post back.

There are many people here that can help you with setting up different servers.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

Kind regards

---

### Post by Jorel on 2012-07-04
Hi matt_symes

thanks for the help, i will dig on this... and hope my headless server will run in no time... :p


Thanks,,,

---

### Post by OM55 on 2012-07-04
Hello jorel,

If you intend to use it just as a file server, you can also simply use the regular desktop edition of Ubuntu, basic install would do (meaning, just as is out of the box).

Assuming you want both Linux and Windows client machines to use this as a file server, the second step would be to install install Samba. This is a file, print, and login server that can create shared folders for both Linux and Windows clients. You can install the Samba server by Either search for 'Samba' at the Software Center and selection the app called:
"SMB/CIFS file, print, and login server for Unix" or, open a terminal and type:

sudo apt-get install samba

After installation, you can launch the samba server application by simply typing 'samba'. If you are using the Gnome 3 (or Gnome session-fall-back) desktop,  you will find the Samba server icon under the Application -> Internet menu.

The Samba server is pretty self explanatory (you select a folder, assign users and user names, and access permissions). 

Just make sure that the Samba server will start automatically at boot. You can do that by adding 'samba' to the 'Startup Applications'.
If you are not sure how to get to the 'Startup Applications', just open terminal and type:

gnome-session-properties

Last - to access the file server from a Windows machine, connect to the IP of the file server computer and look for the shared names. From a Linux machine just use the 'Connect to Server...' program with the 'Windows Share' option.

That's basically all you need to get started. The rest is just tweaks for efficiency and performance. You can find all that you need at O'Reilly's "Using Samba" ISBN 1-56592-449-5 or ISBN-10: 0-596-00769-8 or ISBN-13: 978-0-596-00769-0 or any newer version. There are copies of those books on the net as well.

Hope that helps you get started!

---

### Post by Jorel on 2012-07-05
Hi OM55,

thanks for the advice, but it think the process that you are telling me is more like a NFS Server (as what i have read in [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and correct me if i'm wrong).

but thanks anyway, i will also take a look on that process as well.. :p

Thanks guys..

---

### Post by mastablasta on 2012-07-05
there are also versions based on ubuntu that are designed for easy use of server (with nice GUI frontends) like for example "Zentyal"
 
if you plan to have file storage server then debian based "Open media vault" is nice (if you want to stay on linux)

---

### Post by Jorel on 2012-07-05
Hi mastablasta,

yeah, im planning to set up a file storage server for now, and upgrade it in the near future (if i can), i like GUI's but its more fun using the black-en-white text only (its just my idea :lolflag:) i tried using Debian netinst 6.0.5 but i have no luck and im stuck on setting up my network and i cant get the nearest mirror for an archive... thats why i shift to Ubuntu server,,,

anyway, thanks for the advice...

---

