---
title: "Post Edgy-Update: Courier Can No Longer Auth?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by SecurityMonkey on 2006-10-28
I've been working on this for two days now, I'm stumped.

I recently updated my mail server to Edgy, and everything is working just fine EXCEPT that courier (imap|pop|imap-ssl|pop-ssl) will no longer authenticate with MySQL.

I built the server using this guide:

[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

and it worked flawlessly under Dapper.  Not one problem.

Here is what I'm up against:

```

telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* BYE imaplogin expected exactly two arguments.
Connection closed by foreign host.

```

I get the same for the other logins.

For whatever reason, there is nothing helpful in /var/log/*.log.

I'm not sure if this is a problem with courier, courier-authlib-mysql, courier-authdaemon, or what.

Anyone?  ](*,)

---

### Post by rmar on 2007-05-21
Hi,

Could you solve it?

I was using the 6.06 version, and unfortunately yesterday, i update my system to Feisty fawn version, and some small trouble appear, and i was fixing them, but my Courier IMAP and POP3 server are not working, and always are giving me the following errors, when i telnet them:

telnet localhost imap
Trying 127.0.1.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* BYE imaplogin expected exactly two arguments.
Connection closed by foreign host.

 telnet localhost pop3
Trying 127.0.1.1...
Connected to localhost.localdomain.
Escape character is '^]'.
-ERR pop3login requires exactly two arguments.
Connection closed by foreign host.


The same as you!!

Anyone knows the way to fix it??

Thanks,

Rui

---

### Post by SecurityMonkey on 2007-05-21
> **rmar said:**
> Hi,

Could you solve it?

I was using the 6.06 version, and unfortunately yesterday, i update my system to Feisty fawn version, and some small trouble appear, and i was fixing them, but my Courier IMAP and POP3 server are not working, and always are giving me the following errors, when i telnet them:

telnet localhost imap
Trying 127.0.1.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* BYE imaplogin expected exactly two arguments.
Connection closed by foreign host.

 telnet localhost pop3
Trying 127.0.1.1...
Connected to localhost.localdomain.
Escape character is '^]'.
-ERR pop3login requires exactly two arguments.
Connection closed by foreign host.

Rui

Unfortunately, I ran out of time to troubleshoot this - I ended up wiping the server, going back to 6.06, and then restoring my data.  The server has been up ever since (201 days and counting) with zero problems.

---

### Post by bineshan on 2007-05-30
In the name of God

I opplogize for my english
in .....courier-imap/etc/imapd :
if MAILDIRPATH is null (MAILDIRPATH= ) change it to MAILDIRPATH= / (for example) 
because courier-imap starter script calls imapdrc script that it run imaplogin ${exec-prefix}/bin/imapd ${MAILDIRPATH} and when MAILDIRPATH is null it does not send 2nd argument to imaplogin and it exit with ERROR : " [COLOR="Red"]BYE imaplogin expected exactly two arguments[/COLOR]
when you set the MAILDIRPATH to a path (i.e / or /var/vmail etc....) it works.
I had a same problem in my mandriva box and i solved it by this manner

---

