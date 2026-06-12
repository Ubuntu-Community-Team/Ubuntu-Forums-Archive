---
title: "Confused about p/word for install on user account"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Ozdemon on 2008-06-21
I can't find the answer to what I think is a basic question.  I have installed ubuntu (current) on 2 machines, so I have sudo rights.  I then setup a user account for each machine (for my 2 daughters). 

Now, if while one of them is logged on and using the machine, and they want me to install some software, I am prompted for a password.  If I enter their password, no go.  If I enter my password, no go.  If I open terminal and type sudo apt-get install (whatever) no go.

So my question is do I have to logout of the user account and login to my admin account to do any install?

---

### Post by avtolle on 2008-06-21
Unless you want to give your daughters administrative rights, AFAIK, you will need to log out of her account and in to your account to do this.

---

### Post by Ozdemon on 2008-06-21
> **avtolle said:**
> Unless you want to give your daughters administrative rights, AFAIK, you will need to log out of her account and in to your account to do this.

Thanks, I thought I must have missed something. I still don't know why it would ask me for a password if no matter what password I put in, it would be rejected because that account did not have admin rights.  :confused:

---

### Post by avtolle on 2008-06-22
Hazarding a guess here, that is how the application(s) are programmed, that is, to ask for a password always notwithstanding the fact that the current user doesn't have the authority to take the requested action.

---

