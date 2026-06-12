---
title: "Recovering my admin password"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by sani786 on 2012-10-13
Hy guys,

I m forgot my admin password on ubuntu please tell me any way to recover my password .

waiting for your swift reply.



sani.

---

### Post by darkod on 2012-10-13
What do you mean by "admin" password? There is no such user in ubuntu.

The first user created during the installation has admin rights. So, did you forgot your password?

To reset a user password in ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sani786 on 2012-10-14
> **darkod said:**
> What do you mean by "admin" password? There is no such user in ubuntu.

The first user created during the installation has admin rights. So, did you forgot your password?

To reset a user password in ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
.

Thanks buddy for replying but one thing is confusing me when i use all process in the below link is it disturb my save application i.e oracle ,my documents and more like that .
i will try and then tell you the results.


sani

---

### Post by darkod on 2012-10-14
No, it just creates new password for the user. All applications and data are still there untouched.

---

### Post by sani786 on 2012-10-17
> **sani786 said:**
> .

Thanks buddy for replying but one thing is confusing me when i use all process in the below link is it disturb my save application i.e oracle ,my documents and more like that .
i will try and then tell you the results.


sani

HY Buddy ,

I try your given link but when i reach at recovery menue (2nd snap ) in give link it required root password what is the way to recover root password.

sani

---

### Post by darkod on 2012-10-17
> **sani786 said:**
> HY Buddy ,

I try your given link but when i reach at recovery menue (2nd snap ) in give link it required root password what is the way to recover root password.

sani

No, it doesn't ask for any password. When does it ask you for root password? You simply select Drop to root shell from the recovery menu, and the shell opens (command line).

After that you continue with the instructions.

---

### Post by Mark Phelps on 2012-10-17
You can not "recover" a password, period.  What you can do is "reset" a password, as in, assign a new one.  There is no software available that will let you "recover" passwords.

---

### Post by sani786 on 2012-10-18
> **Mark Phelps said:**
> You can not "recover" a password, period.  What you can do is "reset" a password, as in, assign a new one.  There is no software available that will let you "recover" passwords.


Thanks for guide but can you tell me the way of resetting password.

---

### Post by sani786 on 2012-10-18
> **darkod said:**
> No, it doesn't ask for any password. When does it ask you for root password? You simply select Drop to root shell from the recovery menu, and the shell opens (command line).

After that you continue with the instructions.

thanks buddy, 
 but it require password at command line.

i also share some snapshot for your information.


sani

---

### Post by sani786 on 2012-12-07
> **sani786 said:**
> thanks buddy, 
 but it require password at command line.

i also share some snapshot for your information.


sani


Hi frndz,

here is picture i highlight where it requires for root pass..

---

### Post by sani786 on 2012-12-07
> **sani786 said:**
> Hi frndz,

here is picture i highlight where it requires for root pass..

sani

---

### Post by darkod on 2012-12-07
It doesn't require the root password. It is asking you to enter the new password for the user susan (twice). And you can clearly see the message where it says password updated. That means the new password for susan now it the password you entered.

Now, if susan was the first user created on the system, it should have sudo permissions. So you should be able to use the susan user and the new password, for sudo commands.

On the other hand, if the only user that has sudo permissions is carol, then you need to use that user for running sudo commands.

After changing the password for susan, does it allow you to login with it or not?

---

### Post by spnkybnky on 2013-01-12
I just simply went to a terminal window and typed "passwd" and followed the instructions ......    

Simple as that   

Ubuntu 12.10lts

---

