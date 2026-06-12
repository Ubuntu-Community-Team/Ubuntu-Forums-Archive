---
title: "Moving e-mail from /var/spool/mail/$user to /home/$user/Maildir"
date: 2014-10-16
forum: Installation &amp; Upgrades
---

### Post by anthony40 on 2014-10-16
Hi,

After two days of upgrading from 9.10 to 10.04, then to 12.04 and finally 14.04.1. I have now managed to get my system up and running with the expected services,  also managed to exchange Squirrelmail to Roundcube which was nice. It all went rather well, mailboxes and user accounts intact etc.

I had some problem with the upgrade scripts which I eventually managed to solve. Then a lot of malware code on the box which I had to weed out, and then changing all passwords, regenerating keys etc.... all that crap,  but nothing which had managed to compromise root.

As an overall experience, I must say that I think Ubuntu, and the linux software suite has evolved a lot since the late 90:ties in terms of usability compared when I started to run linux servers.

Now to my problem. 

[B]Background:
[/B]Since the system was infected by some malware, I wanted to make sure to delete all configuration files of running services and start from default configuration to avoid any unsafe config.  Also, since the system had 3 years old software I realized that best practice might have been changed and also layout of configurations.

Hence, I replaced the postfix config files in /etc/postfix.

**Problem:**
Now, The system uses system users with /home/$user/Maildir configuration to store e-mail. The e-mails are delivered by Postfix SMTP server. 

Since I was reconfiguring the postfix config from scratch, I managed to make a mistake while reconfiguring /etc/postfix/main.cf where I inserted the following line:

mailbox_command = procmail -a "$EXTENSION" 

This made all incoming mail being delivered to postfix which gladly accepted them and then stored the mails in /var/spool/mail/$user.

It took me a few hours before I realized this **** up, and fixed it.  Which ment a few hours worth of mail  are now stuck in /var/spool/mail/$user.

I have googled around a bit regarding how to move the mails from /var/spool/mail/$user to /home/$user/Maildir  but I only seem to find guides on how to convert from one type to the others.  I am very afraid of doing this. I would like to merge from /var/spool/mail to maildir not only convert.  I have of course backed up all home folders before doing the upgrade, but I am really not keen on getting some Maildir corrupt errors.

So my question is,  is there some elegant way of merging in mails form /var/spool/mail  to maildir. Making sure that the mails are only added to the existing structure,  and not replacing files with meta data or whatever.

Any advice would be welcome.

Thanks,

---

### Post by SeijiSensei on 2014-10-16
This would be a cinch if you used mbox format.  You could just append the contents of the files in /var/spool/mail to the bottom of /home/user/mail/inbox.  

Files in mbox format use a blank line to delimit messages.  If you only have a few users, you could manually cut up the contents of /var/spool/mail/username into separate files and add them to the person's Maildir.  If you have a lot of users, you will probably need to write a script to do this.  You should stop accepting inbound mail during this process and let it queue up on your backup MX.

---

