---
title: "Mail Server: Cannot Receive From Outside LAN"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by Mhaddy on 2005-11-17
Hi guys,

I just finished the *very* exhaustive [How to set up a mail server on a GNU / Linux system](http://ubuntuforums.org/showthread.php?t=40047) and almost everything went off without a hitch.  I can now send emails and I can receive them locally (i.e. telnet in and send through postfix or emailing myself through SquirrelMail), but I cannot receive emails from people outside my Lan.

I know that my ISP blocks my port 25, so I have invested in [DynDNS.org](http://www.dyndns.org)'s MailHop Relay service where all mail sent to port 25 will be redirected to port 587 (or another one that I can choose).  However, no where in the aforementioned tutorial did I read / figure out how to change my SMTP port from 25 to 587.  This is the email that gets bounced back when you try to email a user on my server:
> This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [email]mhaddy@maddogstudios.net[/email]

------ This is a copy of the message, including all the headers. ------

Return-path: <sitekore@sitekore.com>
Received: from mxin1.mailhop.org ([63.208.196.175])
	by mxout3.mailhop.org with esmtp (Exim 4.51)
	id 1Ecq9s-0009ev-58
	for [email]mhaddy@maddogstudios.net[/email]; Thu, 17 Nov 2005 15:15:00 -0500
Received: from ns1.futurepoint.com ([67.15.58.21] helo=srv01.futurepoint.com)
	by mxin1.mailhop.org with esmtp (Exim 4.51)
	id 1Ecq9r-0002Z9-SO
	for [email]mhaddy@maddogstudios.net[/email]; Thu, 17 Nov 2005 15:15:00 -0500
Received: from [192.168.1.101] (d36-163-122.home1.cgocable.net [24.36.163.122])
	(authenticated bits=0)
	by srv01.futurepoint.com (8.12.11/8.12.11) with ESMTP id jAHKDukC021278
	for <mhaddy@maddogstudios.net>; Thu, 17 Nov 2005 15:13:56 -0500
Message-ID: <437CE4C7.1040702@sitekore.com>
Date: Thu, 17 Nov 2005 15:15:03 -0500
From: Ryan Matthews <sitekore@sitekore.com>
User-Agent: Mozilla Thunderbird 1.0.7 (Macintosh/20050923)
X-Accept-Language: en-us, en
MIME-Version: 1.0
To: [email]mhaddy@maddogstudios.net[/email]
Subject: testasdfasdfsadfasdf
Content-Type: text/plain; charset=ISO-8859-1; format=flowed
Content-Transfer-Encoding: 7bit
X-Mail-Handler: MailHop by DynDNS
X-Spam-Score: -2.6 (--)


Is this possible and if so, can someone lend me a helping hand?  Thanks in advance! :)

---

