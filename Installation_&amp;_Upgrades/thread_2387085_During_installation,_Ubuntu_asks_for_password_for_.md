---
title: "During installation, Ubuntu asks for password for downloading third-party software"
date: 2018-03-14
forum: Installation &amp; Upgrades
---

### Post by scribner on 2018-03-14
Hi, this is my first post in Ubuntu Forums.

Yesterday, when I was installing Ubuntu 16.04.4 LTS, it asked me to create a password underneath the checkbox for "Install third-party software." It said this password would be used after restarting Ubuntu. But Ubuntu never asked for this password again. Can anyone tell me what is going on?

---

### Post by strixtux on 2018-03-14
The installation is done.

---

### Post by strixtux on 2018-03-14
You'll be asked for that password every time the software must be updated.

---

### Post by deadflowr on 2018-03-14
> **strixtux said:**
> You'll be asked for that password every time the software must be updated.

Depends.
If updating using the command line, then yes.
If updating using he update-manager (Software Updater) then it will only ask for a password if new software needs to be installed.
(new software includes, but is not limited to, new kernel versions, as an example)
Otherwise the Software Updater will install updates to existing software without the need to input a password.

Also, Ubuntu has another update program in the Ubuntu Software store.
I am not sure how the Ubuntu Software's update feature handles updates.
If you choose to use that update method.

---

### Post by scribner on 2018-03-22
Thanks for the replies. It is now my understanding that the password was created for the Ubuntu Software application.

---

