---
title: "Evolution-to-Postfix pop3 authentication fails"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by nimy on 2010-07-01
I just upgraded my Ubuntu 8.04 server to 10.04 and now I cannot receive mail on my Ubuntu 10.04 Evolution client, although I can send mail. No errors appear in auth.log or mail.log when I attempt to log in from my Evolution client, in fact mail.log shows 'pop3d-ssl: connection' from my laptop IP, followed by 'pop3d: Disconnected' when the log-in attempts fail.

I'm able to ssh into the server using the same log-on and password as before the upgrade, however I haven't changed the public or private keys in my .ssh directory. I updated the ssl keys in /etc/postfix/ssl but wasn't able to receive mail before or after the update.

The error in the client reads: 'Unable to connect to POP server mail.mydomain.com, error sending username'

I ran this test and the output appears to be related:

$ telnet mail.mydomain.com 110
Connected to server1.mydomain.com.
Escape character is '^]'.
+OK Hello there.
USER
-ERR TLS required to log in. 

Is the pop3 server not running TLS? /etc/postfix/main.cf says it should, and I get no errors restarting / reloading postfix. 

I am receiving messages in /home/user/Maildir, but I cannot download them.
I checked for supported authentication types in my Evolution client - 'Password' is the only one supported, as was true before. The client is  not using any certificates.

The output of openssl s_client -tls1 -connect 127.0.0.1:995 shows 'certificate has expired' on the 'Verify return code' entry, not sure if that's significant.

What's different about incoming versus outgoing mail authentication??

---

### Post by nimy on 2010-07-20
ok I fixed this a while back - sorry for the delay in posting my answers: 
- different ssh keys can be used to encrypt postfix, apache, ssh and other  connections/apps. I didn't update my user (/home) or system (/etc) ssh keys,  hence the error that my certificate had expired. 
- However I did update the ssh keys that postfix uses to encrypt connections to deliver mail to pop3 clients, per the sourceforge directions at [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p5](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p5), a quasi-biblical reference for ubuntu upgrades.
- My Evolution client on 8.4 was using plain text authentication but in 10.4, it was necessary to try each of the account 'receive' authentication/encryption options to see which one would work; I think it was the TLS option that worked - I could see that when the client requested a certificate.
- the telnet test showed the TLS error because telnet doesn't use TLS (but postfix requires it)
- there were no pop3 errors on the server because (I think) the error was on the client side, since the client was rejecting the connection; although I couldn't find any error output in the client syslog either (the error in Evolution was not specific)
- outgoing mail authentication doesn't require TLS - lower encryption  standards apply, although I couldn't find any documentation on this

---

