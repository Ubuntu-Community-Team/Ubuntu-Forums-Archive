---
title: "[SOLVED] Reconfigure Courier-IMAP//Courier-POP SSL key"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by iceportal on 2008-02-21
I've installed an Ubuntu 6.06 server as per [This Tutorial (The Perfect Setup)](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5) about six times now, and every time, I come up with a problem when trying to read mail from my server.

What happens is that when I connect, it says the security certificate seems invalid, and then after I accept, it says that the certificate is for "localhost" while the server is located at "mail.z3row3b.com." I couldn't figure out why this was for the longest time, but I believe I know now...

At the part of the install where we install courier, they execute the following command:

```
apt-get install courier-authdaemon courier-base courier-imap courier-imap-ssl courier-pop courier-pop-ssl courier-ssl gamin libgamin0 libglib2.0-0
```

Part of the results returned (during installation) include this line:

```
subject= /C=US/ST=NY/L=New York/O=Courier Mail Server/OU=Automatically-generated IMAP SSL key/CN=localhost/emailAddress=postmaster@example.com
```

If you notice, it's a default, generic SSL certificate generated.

This is where I think my problem lies... But I don't know how to reconfigure that SSL cert! I want my server to have the proper information, not some default-installation generic SSL info.

So my question is this: How do I make a new SSL certificate for my courier IMAP and POP installation?

---

### Post by iceportal on 2008-02-22
Is there a different place this post should be, where it might get answered quicker?

---

### Post by whazooo on 2008-02-22
open /etc/courier/imapd.cnf
enter your info
Make sure you use your qualified dns name for your common name. CN

rename the original pem file in /usr/lib/courier


run
/usr/lib/courier/mkimapdcert

and then do the same for /etc/courier/pop3d.cnf

rename the original pem file in /usr/lib/courier

Then run;
/usrlib/courier/mkpop3dcert

that should do ya

---

### Post by iceportal on 2008-02-22
Bloody hell... I was trying to "rm imapd.pem" and accidentally did "rm imapd" instead.

Could you maybe output the /usr/lib/courier/imapd script here?

EDIT: nevermind. I just aptitude reinstall'd it.

---

### Post by whazooo on 2008-02-22
Yeah, On my local machine I rename and delete through the file browser so if I do fudge it up
I can get it back from the trashcan #-o

---

### Post by iceportal on 2008-02-22
I'm doing everything from SSH. There is no GUI on the machine, it's a standalone server.

I could probably put fluxbox or something on the system then RDP it...

---

### Post by whazooo on 2008-02-22
I hear ya.......

If the above took care of the problem,
Could you please mark this thread as Solved

Thanks....

---

### Post by iceportal on 2008-02-22
My problem with the install is still not completely fixed, but you did show me how to change the SSL certification, so I'll mark it solved.

Thanks so much for your help!

---

### Post by whazooo on 2008-02-23
IcePortal,

Sorry, I wasn't trying to rush you... Theres no bounty on solved posts :)
take off the solved and lets see if the community can get it sorted out..
Or start a new thread with the problems your having..

---

### Post by iceportal on 2008-02-23
It's no  trouble! You answered the question I asked. I'll probably start a new post with the next step, or a more general inquiry. 

Thanks!

---

