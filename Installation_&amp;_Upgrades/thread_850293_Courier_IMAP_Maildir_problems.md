---
title: "Courier IMAP Maildir problems"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by pittcaleb on 2008-07-05
Average SysAdmin experience here...  My Ubuntu (5.x) server, which had been running fine up and died - had been running postfix & sourier with POP3 mail.  I have numerous domains and users on those domains...

After failing to re-build this system, opted to use backups and build new system - 8.04 - followed the instructions on-line for ISPConfig built, installing POSTFIX and Courier for e-mail.

I don't recall selecting it, but Courier installed with IMAP rather than POP3.  I'll live with IMAP, may actually help me in the long run, so I'm cool with that.

I created my main domain and created my accounts and e-mail started being received - yeah!  On the old system, it was stored in /home/www/domain/users/username/Mail/ [cur|new] as individual files

On the new system, it's all stored for all domains, all users in /var/mail/username as a single file per username.

in /etc/passwd the root for these users is listed as /var/www/domain/user/username

From something I read while googling this issue, maildir should be under that directory, don't know if that pertained to me specifically or not.

When I log in, the error I get is:
chdir Maildir: No such file or directory

This is using SquirrelMail as Thunderbird isn't giving me any verbose errors.  The chdir error is from my system logs.

I am quite at the end of my rope right now.  Any specific help I can get will be greatly appreciated.  My skill set is good, not great and my experience with mail is definitely lacking, but I got it to work last time.  outgoing mail appears to be fine thankfully and it is receiving the mail, but i can not get to it.

thanks in advance,
PittCaleb

---

