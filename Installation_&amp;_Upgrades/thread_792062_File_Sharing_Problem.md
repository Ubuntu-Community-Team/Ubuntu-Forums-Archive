---
title: "File Sharing Problem"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by CRISM on 2008-05-12
I installed the i386 version of Hardy, and the installation went well except for one problem. I tried to share a folder over the LAN, and was prompted to install Samba. I did that, set permissions on the folder for full access by user, group, and others. Then right-clicked on the folder to share and activated all options for sharing. But the folder never showed up for access on the network, even after a reboot to make sure all settings were in effect. I cannot get the right-click sharing options to work. However, I can manually edit the /etc/samba/smb.conf file and after making the appropriate entries for sharing, the folder does show up on the network.

It therefore appears that my right-click option for file sharing is not working. Is there another piece of software I need to download or another setting that needs to be made? I've never had this problem with previous versions of Ubuntu.

---

### Post by gkestrel on 2008-05-28
Have you by any chance got nautilus share installed as this can often cause the problem you describe, check by looking in synaptic if it is installed.  If it is then it needs to be configured before file sharing works correctly. 

To Setup and configure nautilus share
* A quick and easy way to have it running (must be done as root):
copy and paste the following lines in the terminal

export USERSHARES_DIR="/var/lib/samba/usershare"
export USERSHARES_GROUP="samba"

mkdir -p ${USERSHARES_DIR}
groupadd ${USERSHARES_GROUP}
chown root:${USERSHARES_GROUP} ${USERSHARES_DIR}
chmod 01770 ${USERSHARES_DIR}

* next edit /etc/samba/smb.conf:

;/etc/samba/smb.conf

[global]
workgroup = WORKGROUP ; you can change to your own workgroup
security = share

usershare path = /var/lib/samba/usershare
usershare max shares = 100
usershare allow guests = yes
usershare owner only = yes

* Add the samba group to your user (replace your_username by your login):

usermod -a -G ${USERSHARES_GROUP} your_username

* Logout and login again and nautilus share will then work

---

