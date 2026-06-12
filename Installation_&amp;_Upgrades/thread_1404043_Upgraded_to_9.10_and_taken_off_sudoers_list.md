---
title: "Upgraded to 9.10 and taken off sudoers list"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by b89.smith on 2010-02-11
I recently upgraded my computer from Ubuntu 8.04 to Ubuntu 9.10. After I finished the upgrade I tried to run a command in terminal as sudo. The terminal said that I was not on the sudoers list. I tried to ssh into the root account from my everyday account and the password to root had changed as well with the upgrade. How can I add my everyday account back to the sudoers list and also reset my root password?

Thanks.

---

### Post by zvacet on 2010-02-11
To reset password read [this.]("http://www.psychocats.net/ubuntu/resetpassword")

To be able to use sudo add user to admin group with command from recovery mode

```
adduser <username> admin
```

---

### Post by johnson.d on 2010-02-12
Can you post the process of upgradation from 8.04 to 9.10 i.e. using liveCD or internet

---

### Post by b89.smith on 2010-02-13
> **johnson.d said:**
> Can you post the process of upgradation from 8.04 to 9.10 i.e. using liveCD or internet

I upgraded over the internet. I used Update Manager. It prompted me with the update and agreed to it so it downloaded the necessary files on its own and a few hours later I had 9.10.

---

### Post by johnson.d on 2010-02-15
You can follow the below procedure to add your username to sudoers file:

1) Boot using the live CD.
2) Mount the partition from the hard-drive which contains the /etc/sudoers file.
3) Open the file using a utility available in the live CD.
4) Edit the file and add your username to it.
5) Now reboot the system from the hard-drive and login using your username.

Try booting the system and check by running any administrative task using sudo.

You can find details about sudoers file in the following link
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You can reset the password by using the following command:

$ sudo passwd root

---

