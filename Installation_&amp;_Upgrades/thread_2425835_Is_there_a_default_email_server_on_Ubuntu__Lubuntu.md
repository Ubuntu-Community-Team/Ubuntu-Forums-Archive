---
title: "Is there a default email server on Ubuntu / Lubuntu ?"
date: 2019-08-31
forum: Installation &amp; Upgrades
---

### Post by faubuntu on 2019-08-31
Hi, sorry for the naive question but I am out of my depth when it comes to mail config:

I have a couple of Lubuntu desktop installations: 18.04 alternate version and a 18.10.


I use them for testing various webserver configurations and I think I have realized that I have never been able to send emails out.
For example, in trying a forum registration, the emai log says

```
MyBB was unable to send the email using the PHP mail() function.
```


I had assumed that Ubuntu and derivatives come with a default email server but maybe I'm wrong.

I searched around here and in other forums and the common mail services I have come across seem to be **postfix **and **mailutils**, neither of which is installed by default on my images.

Please could you advise as to

[LIST]
[*]whether there is a basic email service pre-installed with the various Ubuntu flavors? 
[*]if not, which one is the most basic I could install (I just need it to enable mail send/receive for the webserver tests)? 
[/LIST]

Thank you

---

### Post by spjackson on 2019-08-31
postfix is what is normally used to send email from a webserver with php. It also receives email. exim would be the main alternative. mailutils doesn't do what you are looking for.

---

### Post by guiverc on 2019-08-31
Just a quick note:  Lubuntu 18.10 (along with all 18.10 releases) reached EOL last month; it was not a long-term-support release and you should have received notifications to upgrade to 19.04.  My chosen mirror still has files for it, but your should fully-upgrade it then `do-release-upgrade` move to 19.04 asap as I've seen help requests because mirrors have already dropped cosmic support.

[https://lubuntu.me/cosmic-etc-eol/](https://lubuntu.me/cosmic-etc-eol/)
[http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/](http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by faubuntu on 2019-08-31
> **spjackson said:**
> postfix is what is normally used to send email from a webserver with php. It also receives email. exim would be the main alternative. mailutils doesn't do what you are looking for.

Thanks spjackson - in the meantime I had tried to install mailutils which happened to automatically install postfix so I think you're right.


So, do I assume there is no default email server that comes pre-installed with Ubuntu and postfix is the default choice that should be installed?

---

### Post by faubuntu on 2019-08-31
> **guiverc said:**
> Just a quick note:  Lubuntu 18.10 (along with all 18.10 releases) reached EOL last month; it was not a long-term-support release and you should have received notifications to upgrade to 19.04.  My chosen mirror still has files for it, but your should fully-upgrade it then `do-release-upgrade` move to 19.04 asap as I've seen help requests because mirrors have already dropped cosmic support.

[https://lubuntu.me/cosmic-etc-eol/](https://lubuntu.me/cosmic-etc-eol/)
[http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/](http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Ok, thanks guiverc

---

### Post by TheFu on 2019-08-31
> **faubuntu said:**
> Thanks spjackson - in the meantime I had tried to install mailutils which happened to automatically install postfix so I think you're right.


So, do I assume there is no default email server that comes pre-installed with Ubuntu and postfix is the default choice that should be installed?

"default" is a strong term.  It is the normal MTA for many Unix systems.  Running an email server doesn't really happen enough that any MTA would claim to be the "default."  Choose the one you need.

If you only need to send email, not receive any, then I think there are better choices.  If you only need to send email to 1 external account, there are better choices.

I've been using postfix for almost 25 yrs now, so I know nothing about most of the the other options and nothing about php. Sorry.

As for troubleshooting - check the log files.

---

### Post by faubuntu on 2019-08-31
> **TheFu said:**
> "default" is a strong term.  It is the normal MTA for many Unix systems.  Running an email server doesn't really happen enough that any MTA would claim to be the "default."  Choose the one you need.

If you only need to send email, not receive any, then I think there are better choices.  If you only need to send email to 1 external account, there are better choices.

I've been using postfix for almost 25 yrs now, so I know nothing about most of the the other options and nothing about php. Sorry.

As for troubleshooting - check the log files.

Thank you TheFu.

---

### Post by SeijiSensei on 2019-08-31
Ordinary desktop users have no need for a mail server so it isn't part of the standard desktop distributions.

Did installing postfix fix your problem?  It should at least see mail sent using PHP's mail() command. Now whether that mail can be delivered is a whole other story.  If you're using a residential connection, chances are good your ISP has blocked outbound connections to port 25 on remote servers to thwart spambots.  Since you also installed mailutils, you can run some simple tests. If postfix is running ("ps ax | grep postfix" to check), then the command

```
echo test | mail -s test someone@example.com
```

should send a test message to [email]someone@example.com[/email].  After doing this, take a look at /var/log/mail.log and see what happened to the message.  

Another simple test is to run the command:

```
telnet gmail-smtp-in.l.google.com 25
```

and see whether you can connect.  You should see a banner like this:

```

Trying 172.217.197.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP m2si1696616qtq.310 - gsmtp

```

If you don't, you're being blocked.  (To end this session, hold down the Ctrl key and hit "]", then type "quit".)

---

### Post by faubuntu on 2019-09-03
> **SeijiSensei said:**
> Ordinary desktop users have no need for a mail server so it isn't part of the standard desktop distributions.

Did installing postfix fix your problem?  It should at least see mail sent using PHP's mail() command. Now whether that mail can be delivered is a whole other story.  If you're using a residential connection, chances are good your ISP has blocked outbound connections to port 25 on remote servers to thwart spambots.  Since you also installed mailutils, you can run some simple tests. If postfix is running ("ps ax | grep postfix" to check), then the command

```
echo test | mail -s test someone@example.com
```

should send a test message to [EMAIL="someone@example.com"]someone@example.com[/EMAIL].  After doing this, take a look at /var/log/mail.log and see what happened to the message.  

Another simple test is to run the command:

```
telnet gmail-smtp-in.l.google.com 25
```

and see whether you can connect.  You should see a banner like this:

```

Trying 172.217.197.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP m2si1696616qtq.310 - gsmtp

```

If you don't, you're being blocked.  (To end this session, hold down the Ctrl key and hit "]", then type "quit".)

Thank you very much SeijiSensei for your comprehensive reply.

Indeed, installing postfix did not solve my original issue (which was needing to see how notifications go out on certain webapps such as WordPress). I realized the more I tried the less I knew about SMTP.

You are right in that whatever I was trying was being sent out but was not being delivered (for example Google blocking me as I was not a recognized/approved sender). I can understand that given how pervasive spam is.

In the end, since I am testing WordPress, I just installed a WordPress SMTP module and I used credentials for an exisiting email account, which for now is sufficient. In retrospect I could probably have used the same credentials with postfix/mailutils achieving the same result.

---

