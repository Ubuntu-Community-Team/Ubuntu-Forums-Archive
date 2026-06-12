---
title: "postfix, SSL and AT&amp;T"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by jeffrey1681 on 2007-06-29
I'm having some problems while setting up postfix.  I need to relay all of my outgoing mail through my ISP (AT&T) and had it working fine, except that recently AT&T changed and now requirs all SMTP authentication to use SSL on port 465.  After looking around the web I thought I had set it up correctly, but whenever I try to send an e-mail I get a message like the following in my mail log and the mail isn't sent:
> 
relay=smtp.att.yahoo.com[68.142.198.11]:465, delay=42137, delays=42117/0.04/20/0, dsn=4.4.2, status=deferred (lost connection with smtp.att.yahoo.com[68.142.198.11] while receiving the initial server greeting)


Here is the part of my main.cf that I think applies:
> 
relayhost = smtp.att.yahoo.com:465
smtp_tls_policy_maps = hash:/etc/postfix/tls_policy
smtp_sasl_password_maps = hash:/etc/postfix/saslpw
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,rejec
t_unauth_destination


with tls_policy consisting of:
> 
smtp.att.yahoo.com:465   encrypt


and saslpw having:
> 
smtp.att.yahoo.com:465  <email address>:<password>


I have run postmap on both files.  Is there something I'm missing in the main.cf file or anywhere else that would fix this problem?  This is running on 7.04 server.  Thanks for your help.

---

### Post by orozcovision on 2007-06-29
Hello Jeffrey,

I originally ran into the same problem when setting up a production Mail Server on Feisty 7.04.  Hope the following helps:

//---Main.cf-------------------------------------------------
**relayhost = [smtp.sbcglobal.yahoo.com]**
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
**smtpd_sasl_password_maps = hash:/etc/postfix/sasl_passwd**
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
------------------------------------------------------------//

Then created file: sasl_passwd

//---sasl_passwd-------------------------------------------------
[smtp.sbcglobal.yahoo.com] *myusername*@sbcglobal.net:*mypassword*
-------------------------------------------------------------------//

Afterwards, run the following:

sudo /etc/init.d/postfix reload
sudo /etc/init.d/postfix restart

NOTE: You can replace "sbcglobal" with your service provider (att). In my case, its 'Sbcglobal', so that worked for me. If it does not work for you, refer to AT&T's smtp guidelines to find out what address you should be pointing to.

Hope this info helps you out.

Best,
OrozcoVision

---

### Post by jeffrey1681 on 2007-06-29
That's actually what I had until about a week ago when I had to reinstall my server (hard drive died).  I figured this was a good chance to setup secure authentication for the SMTP server, since AT&T now says is required.  

[http://helpme.att.net/article.php?item=287](http://helpme.att.net/article.php?item=287)

With your method I get the error "authentication required - for help go to http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html" in my mail log.  Thanks for the attempt, I actually was sbcglobal initially as well until att bought them.

---

### Post by orozcovision on 2007-06-29
> "authentication required - for help go to http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html"


I recall receiving this error when NOT using the "[ ]" brackets in both, relayhost (main.cf), and in the sasl_passwd file.

Check to ensure you are using the brackets.  Again, this is what got my Mail server working.

Best,
OrozcoVision

---

### Post by jeffrey1681 on 2007-06-29
Unfortunately, no luck (same error).  My guess is that the old sbcglobal servers don't require the SSL authentication and the new att ones do.

---

### Post by orozcovision on 2007-06-29
The reason they changed it for Dynamic IP based customers, was due to their alternate solution to closing port 25.  This smtp auth. gives them more control in reducing spam, and helps diminish the control of un-protected servers.

You mentioned that you were once an Sbcglobal customer. If your member ID ends with @sbcglobal.net, then you should be using "smtp.sbcglobal.yahoo.com" and NOT "smtp.att.yahoo.com"

Alternately, you should check to see if TLS is configured correctly.  Telnet into your server (i.g telnet my.server.com 25)>Type "ehlo my.server.com", and you should see the following code:

250-STARTTLS

If you see that code, then your TLS is configured correctly.

NOTE: 
Not sure if I mentioned this in my previous posts, but after creating the "sasl_passwd", and entering :
//---------------
[smtp.sbcglobal.yahoo.com] [email]username@sbcglobal.net[/email]:mypassword
---------------//

**into that file, change the permission so others can't read it:**

//------------------------
chmod 600 /etc/postfix/sasl_passwd
----------------------------//

**Next, postmap it so Postfix can read it**

//----------------------------
postmap /etc/postfix/sasl_passwd
------------------------------//
[B]
Finally, Reload/Restart Postfix.[/B]

--
OrozcoVision

---

### Post by jeffrey1681 on 2007-06-30
> **orozcovision said:**
> You mentioned that you were once an Sbcglobal customer. If your member ID ends with @sbcglobal.net, then you should be using "smtp.sbcglobal.yahoo.com" and NOT "smtp.att.yahoo.com"


This is actually not true anymore.  Look at the link I have in my second post.  ALL users (whatever their initial service) are supposed to switch to the att server.  I could probably get the sbcglobal server working, but I don't think it's going to be active for too much longer.  

> 
Alternately, you should check to see if TLS is configured correctly.  Telnet into your server (i.g telnet my.server.com 25)>Type "ehlo my.server.com", and you should see the following code:


I tried this, TLS is configured correctly according to that.  

I've already run postmap on the saslpw file, no luck.  Thanks for the help, any other ideas?

---

### Post by jeffrey1681 on 2007-07-03
I've had no luck getting AT&T's server to work, but by following the tutorial here:

[http://prantran.blogspot.com/search/label/relayhost](http://prantran.blogspot.com/search/label/relayhost)
[http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)

I was able to get mail sending to work through gmail's server.  That should work for now.  Thanks for your help. :)

---

### Post by mterlouw on 2007-08-19
I was able to get it to work.  Here are the relevant settings:

main.cf:
```
relayhost = [smtp.att.yahoo.com]:587
smtp_sasl_auth_enable = yes
smtp_tls_security_level = may
smtp_sasl_password_maps = hash:/etc/postfix/saslpass
smtp_sasl_mechanism_filter = plain, login
smtp_sasl_security_options = noanonymous
```

saslpass:
```
[smtp.att.yahoo.com]:587        username@att.net:password
```

Then don't forget to run:
```
$ postmap saslpass
```

---

### Post by jeffrey1681 on 2007-08-20
Hm, it appears that the problem was with the port I was using.  AT&T says to use port 465, but when I switched to using 587 it all worked.  Thanks!

---

### Post by tieum on 2007-11-07
Hello,

I also have trouble setting this up.

Here is what I have in main.cf:

> relayhost = [smtp.att.yahoo.com]:465
smtpd_sasl_auth_enable = yes
smtp_tls_security_level = may
broken_sasl_auth_clients = yes
smtpd_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_mechanism_filter = plain, login
smtpd_sasl_security_options = noanonymous

I then got the following error:

> Nov  7 08:32:25 hostname postfix/smtp[4382]: 1172C2F4BF: to=<recipient@domain.com>, relay=smtp.att.yahoo.com[66.196.96.87]:465, delay=20, delays=0.15/0.02/20/0, dsn=4.4.2, status=deferred (lost connection with smtp.att.yahoo.com[66.196.96.87] while receiving the initial server greeting)


If I switch to port 587, I got:

> Nov  7 08:50:17 hostname postfix/smtp[5099]: 1172C2F4BF: to=<recipient@domain.com>, relay=smtp.att.yahoo.com[66.196.96.87]:587, delay=1093, delays=1092/0.11/0.35/0.11, dsn=5.0.0, status=bounced (host smtp.att.yahoo.com[66.196.96.87] said: 530 authentication required - for help go to [http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html](http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html) (in reply to MAIL FROM command))




Any ideas?

Thanks in advance,

   Tieum

---

### Post by tieum on 2007-11-07
Got it. I was missing the port number in the password file:

> [smtp.att.yahoo.com]**:587**        username@att.net : password

---

### Post by pmgeahan on 2007-11-10
I seem to be having the same problem.  I've tried making the changes you folks have mentioned, and upon sending an email, I get the following error message:

```
Nov 10 13:07:55 server postfix/smtp[15928]: B8E7474078: to=<pmgeahan@gmail.com>, relay=smtp.att.yahoo.com[68.142.229.41]:587, delay=0.29, delays=0.03/0.01/0.23/0.03, dsn=5.0.0, status=bounced (host smtp.att.yahoo.com[68.142.229.41] said: 530 authentication required - for help go to http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html (in reply to MAIL FROM command))
```

...which seems to be similiar to what everyone else is getting.  I have followed the other's directions, but still can't seem to connect.  

My main.cf:

```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server.thepatcave.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.thepatcave.org, server.thepatcave.org, thepatcave.org, localhost
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
#mailbox_command = /usr/bin/procmail
mailbox_command = /usr/bin/procmail -f- -a "$USER" 

relayhost = [smtp.att.yahoo.com]:587
smtpd_sasl_auth_enable = yes
smtp_tls_security_level = may
broken_sasl_auth_clients = yes
smtpd_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_mechanism_filter = plain, login
smtpd_sasl_security_options = noanonymous

```

My sasl_passwd(properly sanitized):

```
[smtp.att.yahoo.com]:587        user@sbcglobal.net:passwd
```

My tls_policy:

```
[smtp.att.yahoo.com]:587        encrypt
```

I have verified that postmap has been run since the files were updated:

```
-rw-------   1  655 root    56 2007-11-10 12:59 sasl_passwd
-rwxr-xr-x   1  655 root 12288 2007-11-10 13:05 sasl_passwd.db*
-rw-r--r--   1 root root    33 2007-11-10 13:07 tls_policy
-rw-r--r--   1 root root 12288 2007-11-10 13:07 tls_policy.db
```

...so I'm at a loss as to why I'm still getting the error.  I am using the username/password I set up with SBC for the DSL.

Anyone have any ideas?

---

### Post by pmgeahan on 2007-11-10
> **pmgeahan said:**
> I seem to be having the same problem.  I've tried making the changes you folks have mentioned, and upon sending an email, I get the following error message:

Yeah, I figured it out.  Seems in my main.cf, I had accidentally replaced some of the 'smtp's(like in, says, smtp_sasl_auth_enable) with smtpds.  Replaced back, fixed fine.

---

### Post by johngoebel on 2007-11-15
Thanks to the advice on this forum I am finally able to get my Postfix to talk to ATT's smtp server. 

Does anyone know why port 587 is needed although ATT says 465?

Just curious...

---

### Post by zazuge on 2008-03-02
> **johngoebel said:**
> Thanks to the advice on this forum I am finally able to get my Postfix to talk to ATT's smtp server. 

Does anyone know why port 587 is needed although ATT says 465?

Just curious...

sorry for the late reply, but I have to, so can others benefit from this thread.

well to put it simply the yahoo smtp server have 3 open ports for relaying smtp

there is the standard 25 port 
this one can be used by clients but it is intended for other smtp servers

the submit port 587 used for clients that want to submit their mails

and the 465 port used  for secure SSL authentification

using postfix with 
"smtpd_sasl_security_options = noanonymous"
arguments mean that potfix will use plain text passwords
so thers is no sense in trying to submit mail on the 465 with this argument and
"smtpd_use_tls=yes" SSL activated

so when to use 
smtpd_sasl_security_options = noanonymous
by default postfix will reply with " NO AUTHENFICATION MECHANISME" message
when you try to send mail throught port 25 or port 587
so to make plain text smtp auth works you use that "noanonymous" argument
because postfix use the "noplaintext" by default.

but if you want to send mail via the secure port 465 then you have to comment it
and to setup the SSL authentification mechanisme properly 

hope that will solve this kind of problem.

---

