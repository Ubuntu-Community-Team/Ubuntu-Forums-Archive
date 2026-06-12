---
title: "ubuntu 9.10 not showing upgrade option in update manager"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by kumarat9pm on 2010-04-30
Hi all,

      I am using Ubuntu  9.10, as i want to upgrade to 10.04. I followed the Ubuntu steps mention in Ubuntu.com but my update manager is not showing upgrade option..
i tried below command that too did not show any output about the available updates..

#do-release-upgrade
Checking for a new Ubuntu release
No new release found

Please help to resolve this issue.. I am egar to see how things are in Lucid..

---

### Post by apurbapaul0 on 2010-04-30
I am also not getting the upgrade option in the update manager of 9.10 to upgrade it to 10.04. Then I have downloaded the alternate cd from the site [http://mirror.ovh.net/ubuntu-releases/10.04/](http://mirror.ovh.net/ubuntu-releases/10.04/) now follow the steps given on the ubuntu site but it showing that "An upgrade from 'helena' to 'lucid' is not supported with this tool." 
Please help to solve the problem.

---

### Post by arpanaut on 2010-04-30
"An upgrade from **'helena'** to 'lucid' is not supported with this tool."

Isn't Helena the code name of the Linux Mint 9.10 release...
If you have Mint installed that could be the reason the Ubuntu iso is not working.

---

### Post by apurbapaul0 on 2010-04-30
> **arpanaut said:**
> "An upgrade from **'helena'** to 'lucid' is not supported with this tool."

Isn't Helena the code name of the Linux Mint 9.10 release...
If you have Mint installed that could be the reason the Ubuntu iso is not working.
I had installed the mint menu. Now I have unistalled all the package that I had installed to install the mint menu. But it till not showing the upgrade option and the same error massage when I am using the alternate cd. 
Please help me to solve the problem.

---

### Post by kumarat9pm on 2010-05-03
any updates on this? how to troubleshoot this issue?
still not able to see upgrade option :(

---

### Post by kumarat9pm on 2010-05-03
update-manager -d
warning: could not initiate dbus
Error setting launch_time:  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 107, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 204, in __init__
    self.restore_state()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 706, in restore_state
    expanded = self.gconfclient.get_bool("/apps/update-manager/show_details")
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)



This is the error i am getting when installing ubuntu 10.04..

---

### Post by chaeron on 2010-06-03
I managed to upgrade my laptop from Karmic to Lucid using the Alternative ISO.  But now when I run update manager (gksudo update-manager) and then tell it to update packages, I get the same error messages as Kumar:

> **kumarat9pm said:**
> 
warning: could not initiate dbus
...
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)


However, if I do a sudo su - and then start update-manager, it will download and install packages just fine.

Very strange.  Any ideas on how to fix this?

---

### Post by system60 on 2011-03-18
sorry to bump an old topic but did anyone figure this out? I'm on 9.10 and it doesn't show any upgrades available in update manager. This is just on a netbook that doesn't have much on it so i'll probably just d/l 10.10 and install off usb drive if no one has figured this out.

---

