---
title: "Upgrade 10.04-12.04 no response on imap port"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by brucehvn on 2012-09-03
I upgraded from 10.04 to 12.04 and most everything went smooth except for errors upgrading cyrus from 2.2 to 2.4.  There was an issue with converting the dbs, and several bugs have been filed on that problem.

I worked through that problem and got cyrus 2.4 up and running with no errors in the mail.log and mail is now being delivered to the mailboxes (as per the log).

My problem now, however, is that while cyrus is listening on port 143, any connection to that port are met with no response from the server.  I can telnet to it (even from localhost) and the connection gets established, but I get nothing from the imap server.  I try to issue a LOGIN command, but nothing.  So email clients end up timing out.  I have apache on that box and there's no problem connecting to the web server.  UFW is disabled.  Whenever I make a connection, I'm not seeing any indication in any logs (auth, mail.log, mail.err, syslog, etc.).

When I connect with telnet, I can see the established connection using netstat.

I'm really baffled here and I need to get my mail.  Any ideas?

---

### Post by brucehvn on 2012-09-03
Seems that for some reason, I did not have the cyrus-imapd package installed.  Having the base cyrus installation seems to be enough to have it listening on port 143, but nobody was home to pick up the phone.

---

