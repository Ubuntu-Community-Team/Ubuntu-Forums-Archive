---
title: "Ubuntu 6.06 LAMP install"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by StianH on 2006-06-15
I just installed a LAMP server with the Ubuntu 6.06 server install CD, and I've got everything set up like I like it, and I've used nothing but the default packages. I've been working on a php script, where users recieve an email when registering (or when then need to reset their passwords). This worked very well before on my Fedora workstation, however moving things over to this freshly installed Ubuntu server all works fine except for having the mail sendt out.

The "mail" command is not installed either. If there is any other information you wish me to post that can aid in solving this please let me know.

---

### Post by fluffington on 2006-06-15
Ubuntu doesn't install an MTA by default. I recommend installing postfix (it's what I use), but there are also exim4-daemon-light and exim4-daemon-heavy in main and several others in universe.

---

### Post by StianH on 2006-06-15
Okay, I installed postfix, and also mailx so I could send e-mails from the shell. I used mail to send to my own user on the server, which worked as expected. However when trying to send to my gmail account, and a mailaccount at a webhost, the mails don't get through.

This is what mailq reports a few entries like this, where sending has timed out:
```

1688E2A8085      478 Fri Jun 16 03:49:11  [email]www-data@b0x.konspirasjon.net[/email]
         (connect to gsmtp163.google.com[64.233.163.27]: Connection timed out)
                                         [email]stian.hole@gmail.com[/email]

```

I have of course restarted apache and postfix just for good measure, and still no go.

I should also add that the server is not behind a firewall, it is behind a router, but all external requests are directed to this server (dmz).

---

### Post by StianH on 2006-06-15
Turns out my ISP blocks port 25 outbound, so I've just relayed postfix through their smtp server and everything works fine now :)

---

