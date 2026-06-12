---
title: "Configuring Postix"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by musse1 on 2007-01-06
This is my /etc/postfix/main.cf file. What have I done wrong? I just want to be able to send mail. PHP mail() doesn't work. What is wrong with my settings?

smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
myhostname = smtprelay1.telia.com
inet_interfaces = all

#mydomain = xx.yy.se
#myorigin = $mydomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, localhost.$mydomain
relayhost = smtprelay1.telia.com
relay_domains = $mydestination
#local_reciptient_maps =
#smtpd_sender_restrictions = hash:/etc/postfix/access
#smtpd_client_restrictions = no
smtpd_helo_required = no
#smtpd_helo_restrictions = no
#mynetworks_style = subnet
mynetworks = 127.0.0.0/8, 10.0.0.0/8
#smtpd_recipient_restrictions = check_relay_domains

mailbox_size_limit = 0
message_size_limit = 10240000
recipient_delimiter = +
inet_protocols = all


php.ini:

[mail function]
; For Win32 only.
SMTP = smtprelay1.telia.com
smtp_port = 25

; For Win32 only.
;sendmail_from = [email]me@example.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail

---

### Post by kidders on 2007-01-06
Hi there,

What do you mean when you say "doesn't work"?

---

### Post by musse1 on 2007-01-06
it won't send any emails with mail();

---

### Post by kidders on 2007-01-06
Hey again,

See if you can pin the issue down a bit. For instance, you should check your postfix logs to see if PHP even tries to send the mail in the first place. That way, you'll have a much clearer idea of where to look for problems. Values returned by PHP's "mail" function might also give you some clues.

---

### Post by musse1 on 2007-01-06
where are the postfix logs?

---

### Post by kidders on 2007-01-06
/var/log/mail.log (for me, anyway).

**Edit:** Try doing a **tail -n 0 -f /var/log/mail.log** and sending a mail with PHP. If there's no output, I imagine PHP is the problem.

---

### Post by musse1 on 2007-01-06
This is the error:
Jan  6 20:41:23 ubuntu postfix/sendmail[3759]: fatal: Recipient addresses must be specified on the command line or via the -t option

---

### Post by musse1 on 2007-01-06
Now I get this error:

Jan  6 23:21:03 ubuntu postfix/smtp[3743]: 75BEC2DEC2: to=<my_email@hotmail.com>, relay=smtprelay1.telia.com[81.228.9.101]:25, delay=0.35, delays=0.12/0/0.2/0.03, dsn=5.0.0, status=bounced (host smtprelay1.telia.com[81.228.9.101] said: 504 <www-data@ubuntu>: Sender address rejected: need fully-qualified address (in reply to RCPT TO command))
Jan  6 23:21:03 ubuntu postfix/cleanup[3774]: BCED52DEC3: message-id=<20070106222103.BCED52DEC3@ubuntu>
Jan  6 23:21:03 ubuntu postfix/qmgr[3642]: BCED52DEC3: from=<>, size=2332, nrcpt=1 (queue active)
Jan  6 23:21:03 ubuntu postfix/bounce[3744]: 75BEC2DEC2: sender non-delivery notification: BCED52DEC3
Jan  6 23:21:03 ubuntu postfix/qmgr[3642]: 75BEC2DEC2: removed
Jan  6 23:21:03 ubuntu postfix/local[3745]: BCED52DEC3: to=<www-data@ubuntu>, relay=local, delay=0.05, delays=0.03/0/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Jan  6 23:21:03 ubuntu postfix/qmgr[3642]: BCED52DEC3: removed

---

### Post by kidders on 2007-01-07
> **musse1 said:**
> This is the error:
Jan  6 20:41:23 ubuntu postfix/sendmail[3759]: fatal: Recipient addresses must be specified on the command line or via the -t optionAs I think you've already seen, that can be fixed in php.ini.

> **musse1 said:**
> Now I get this error:

Jan  6 23:21:03 ubuntu postfix/smtp[3743]: 75BEC2DEC2: to=<my_email@hotmail.com>, relay=smtprelay1.telia.com[81.228.9.101]:25, delay=0.35, delays=0.12/0/0.2/0.03, dsn=5.0.0, status=bounced (host smtprelay1.telia.com[81.228.9.101] said: 504 <www-data@ubuntu>: Sender address rejected: need fully-qualified address (in reply to RCPT TO command))
Jan  6 23:21:03 ubuntu postfix/cleanup[3774]: BCED52DEC3: message-id=<20070106222103.BCED52DEC3@ubuntu>
Jan  6 23:21:03 ubuntu postfix/qmgr[3642]: BCED52DEC3: from=<>, size=2332, nrcpt=1 (queue active)
Jan  6 23:21:03 ubuntu postfix/bounce[3744]: 75BEC2DEC2: sender non-delivery notification: BCED52DEC3
Jan  6 23:21:03 ubuntu postfix/qmgr[3642]: 75BEC2DEC2: removed
Jan  6 23:21:03 ubuntu postfix/local[3745]: BCED52DEC3: to=<www-data@ubuntu>, relay=local, delay=0.05, delays=0.03/0/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Jan  6 23:21:03 ubuntu postfix/qmgr[3642]: BCED52DEC3: removedI would be inclined to fix that in php.ini too. You've presumably arranged your addressing requirements in postfix the way they are for a reason, so it's up to PHP to comply with them. Check out sendmail's man page for how to specify sender information on the command line.

Of course, depending on the contents of the mails you're sending (ie how much header info they have in them), your PHP scripts themselves might be the things that need tweaking ... but "www-data@ubuntu" looks like a default sender name to me, so you're probably not specifying it manually, I'd say.

**Edit:** I'm not sure if you're aware of this, but you probably have a little mail queue management to take care of after all that testing. You may have delivery failure notifications swimming around in the queue with nowhere to go.

---

### Post by musse1 on 2007-01-07
I actually found this and maybe this is something:
[http://www.ubuntuforums.org/showpost.php?p=1481089&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1481089&postcount=8)
He has the same problem but I don't know what to write in /etc/hosts if that's the problem. This is my etc/hosts:

127.0.0.1       localhost
192.168.0.161   ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by kidders on 2007-01-07
Yeah, I guess that would be one way of solving the problem. When postfix says "I want a fully qualified domain name", you could either just give it one, or fiddle with your name resolution config to distort your system's impression of your domain name.

If it were me, I would just have PHP use a sensible sender address, either by altering the sendmail parameters it uses, and/or by including appropriate headers in mails sent via PHP scripts. If you would prefer to doctor your domain name resoltion, I'm sure a little experimentation would find the right settings for you. I'm not completely certain about what side-effects that might have, though.

---

### Post by musse1 on 2007-01-07
So how should I solve this technically since I'm totaly green at Linux? I have bought this domain: [www.rugbymanager.eu](www.rugbymanager.eu) and this is my test-script:

<?php
	$subject = 'Test';
	$message = 'Test';
	$mail = 'email@hotmail.com';
	$name = 'Name';

	$headers  = "MIME-Version: 1.0\r\n";
	$headers .= "Content-type: text/html; charset=iso-8859-1\r\n";
	$headers .= "X-Priority: 3\r\n"; 
	$headers .= "X-MSMail-Priority: Normal\r\n"; 
	$headers .= "X-Mailer: php\r\n"; 
	$headers .= "To: $name < $mail > \r\n";
	$headers .= "Return-path: [email]support@rugbymanager.eu[/email] \r\n";
	$headers .= "Reply-to: [email]support@rugbymanager.eu[/email] \r\n";
	$headers .= "From: Rugby Manager <support@rugbymanager.eu>\r\n"; 

	mail($mail, $subject, $message, $headers);
?>

---

### Post by kidders on 2007-01-07
Sendmail's **-r** or **-f** options might sort you out ... at least that's what I was hoping.

It wouldn't surprise me if your SMTP server continued to reject mail from PHP though, since (from your postfix config) your local domain seems to be "telia.com" ... so I guess I'm assuming postfix will accept and deliver a mail from [email]support@rugbymanager.eu[/email] sent from your email app.

**Edit:** Incidentally, on closer inspection of your extract from your postfix logs, I notice that it's actually another SMTP server (ie not your own postfix) that rejects mail from PHP. Modifying your /etc/hosts will **not** help you in that case. Sorry I didn't spot that before.

---

### Post by musse1 on 2007-01-07
telia.com is not my localhost...maybe the postfix config is wrong after all. telia is my isp

---

### Post by kidders on 2007-01-07
Ohhh... In that case, you really should go over your postfix configuration with a fine tooth comb before moving on to PHP. If your SMTP server is going to be externally accessible, it is particularly important that you understand and consider the effect of every single line. If not, you can affort to be a little laxer though.

---

### Post by sav2005 on 2007-01-08
The PHP mail() doesn't seem to work from localhost. See the PHP documentation. Try your code on the live server.

---

### Post by musse1 on 2007-01-08
I changed mydomain and myorigin to my domain and now it works. Still a problem though. Mails that are sent goes directly to the junkmail. How do I solve that?

---

### Post by kidders on 2007-01-09
Are you referring to your mail client's junk mail filter, or have you installed spamassassin?

It's possible that your junk filter is a little overzealous, or that something about your mails isn't quite right ... can you make your spam filter explain what causes it to filter your mail? Often the problem is protocol-related -- if mails you send break the rules, they'll often get filtered.

One easy thing you can do is whitelist your own domain, however that won't stop other peoples' spam filters from junking mail you send :-(

---

### Post by musse1 on 2007-01-09
I have hotmail and hotmail are a little bit sensitive in this matter. I don't think I can make hotmail show why it's filtered. Probably there's a problem with Postfix since the same PHP-script could send emails before on my Windows 2003 server. Don't know how to solve this.

---

### Post by kidders on 2007-01-09
There are many, many possible reasons why an SP would consider mail from you to be junk. Provided postfix isn't configured to do something weird, it's unlikely to be the cause though. It could just be down to the IP address you're using.

Just in case there's something obvious going on, could you post the source of one of the junked messages?

---

