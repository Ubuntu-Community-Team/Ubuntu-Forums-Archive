---
title: "Sudo does not work graphically"
date: 2017-05-24
forum: Installation &amp; Upgrades
---

### Post by GoldWing on 2017-05-24
Hi,


After we install all our  laptops with ubuntu 16.04 and brought them into the domain, it seems when the user logs in with his domain account, when doing admin tasks, it asks for our admin account 'ict' which we created in terms of emergency.
User is added to a file in /etc/sudoers.d/ with this:

x011sqdfqs ALL=(ALL) ALL

Actually we update these files (with puppet) when giving a user access to a system:

- /etc/sshd/sshd_config (in the **AllowUsers** section
- /etc/sssd/sssd.conf (in the **simple_allow_users** section
- /etc/sudoers.d/10_sudo_users_groups

The workaround now is to launch **sudo unity-control-cente**r via the terminal

Probably we need to update another file, but we have no clue which.

Thanks,


O.

---

### Post by Y^2om&amp;#7sgP on 2017-05-24
I think you need to install gksu

---

### Post by GoldWing on 2017-05-24
solution is to add this user to the sudo group as well, so he becomes administrator

---

### Post by GoldWing on 2017-05-24
question is: all users that are in the sudo group have sudo access from the CLI & the GUI, but the ones in a file under /etc/sudoers.d does only have sudo access in the CLI. 
Is this normal behaviour ?
A bug ?

---

### Post by mastablasta on 2017-05-25
sudo is not to be used for GUI applications.

current recomedend method is 
sudo -H

---

