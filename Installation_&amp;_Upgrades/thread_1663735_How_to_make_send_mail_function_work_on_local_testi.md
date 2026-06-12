---
title: "How to make send mail function work on local testing pc(without fixed IP, domain)"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by xirochanh on 2011-01-10
I have an ubuntu box (server edition 10.10) installed on a PC at my home, behind a NAT - i guess, so I don't have a public IP as well as valid domain mapped to it.

Can I test the mail function of PHP? I like to test sending mail to yahoo, gmail...
I tried sendmail package, then the script take very long time to finish and got some errors like "no qualified domain name" in the /var/log/mail.err file.
Then, I tried postfix, which is supposed to replace totally sendmail. In php.ini file, sendmail_path is still /usr/sbin/sendmail -t -i. The mail() function return true immediately but without any message received. If I change to sendmail_path to /usr/sbin/postfix -t -i, mail function return false. I don't know where to catch error log of postfix

Any suggestion for my situation is highly appreciated. I need to test all functions before putting my server into data center.

Thanks

---

### Post by mail2345 on 2011-01-10
Well, you could try to create a webmail account for the server and configure postfix to use that.

---

### Post by xirochanh on 2011-01-10
> **mail2345 said:**
> Well, you could try to create a webmail account for the server and configure postfix to use that.

Not really catch your idea clearly. You mean I should register some mail account like hotmail, gmail... then use smtp their service to send, right? could I do like I can do with smtp service on IIS? so that I can send email with "from address" can be whatever I want.

I don't have knowledge about mailing protocol, but I find it simple to send mail with IIS SMTP service

---

### Post by xirochanh on 2011-01-10
Can someone explain me basic concepts of sending mail or something help me have better understanding about my situation?

---

### Post by lykeion on 2011-01-10
I've only experience with sendmail and PHP, not Postfix. 
But you should look at the error log to see what errors you get, I think it's /var/log/mail.log
Maybe it's something easy like a missing required dir: [http://serverfault.com/questions/109201/php-mail-not-working-with-postfix-on-ubuntu](http://serverfault.com/questions/109201/php-mail-not-working-with-postfix-on-ubuntu)
Also the Ubuntu docs on Postfix is good to read: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by xirochanh on 2011-01-11
> **lykeion said:**
> I've only experience with sendmail and PHP, not Postfix. 
But you should look at the error log to see what errors you get, I think it's /var/log/mail.log
Maybe it's something easy like a missing required dir: [http://serverfault.com/questions/109201/php-mail-not-working-with-postfix-on-ubuntu](http://serverfault.com/questions/109201/php-mail-not-working-with-postfix-on-ubuntu)
Also the Ubuntu docs on Postfix is good to read: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

thanks, bro. I'll try

---

