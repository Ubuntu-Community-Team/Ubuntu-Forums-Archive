---
title: "Making TOmcat to run at port 80"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by yeoheric on 2007-04-17
Hi all,

Due to a requirement from my boss I had to download the tomcat 5.0x tarball from the apache.org site nad extracted it to run on Ubuntu Server 6.06-1.

I have created a user (User A, which cannot sudo) to own some of the application folders and its content. User A also has full access to the Tomcat binaries (I extracted thme to /opt/tomcat). Recently due to a request from a customer, they want to run Tomcat on port 80.

As I understand it as a normal user, User A cannot start a service to run below 1024. 

Is there a way I can make User A to start the Tomcat service with Port 80 but not having the ability to sudo?

We only allow the programmers and content uploaders to access the server using User A. So it is best not to allow them any other rights.

Please assist.

Thanks

Eric

---

### Post by thelinuxguy on 2007-04-17
> **yeoheric said:**
> 
Is there a way I can make User A to start the Tomcat service with Port 80 but not having the ability to sudo?


Are you looking for SUID?
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)
[http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)

**Security implications need to be evaluated carefully.**

---

### Post by yeoheric on 2007-04-20
Hi,

Thanks for the reply, was down for a couple of days due to fever. I shall look at your provided URLs.

Regards,
Eric

---

