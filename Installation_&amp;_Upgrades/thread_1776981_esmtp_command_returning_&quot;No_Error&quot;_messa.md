---
title: "esmtp command returning &quot;No Error&quot; message..how to solve it"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by priyaranjanmonu on 2011-06-07
Hi, I have installed esmtp and libEsmtp manually in my system (Ubntu). I  have configured the esmtprc file properly too, but I am not able to  send the mail. It returns No Error.

hostname=[smtp.gmail.com:587]("http://smtp.gmail.com:587/")
username=""
password=""
starttels=enabled
mda="/usr/bin/procmail -d %T"

I have installed the software in this way.

$ tar xvjf libesmtp-1.0.4.tar.bz2 $ cd libesmtp-1.0.4 $ ./configure --prefix=/usr/local $ make $ sudo make install $ cd .. $ tar xvjf esmtp-0.6.0.tar.bz2 $ cd esmtp-0.6.0 $ ./configure --prefix=/usr/local --with-libesmtp=/usr/local $ make $ sudo make install


When I was running the command esmtp to send a mail. It was returning "No Error"

$echo "Hello" | esmtp [EMAIL="priyaranjan@silvanlabs.com"]priyaranjan@silvanlabs.com[/EMAIL] -f [EMAIL="priyaranjan@silvanlabs.com"]priyaranjan@silvanlabs.com[/EMAIL]  -C /etc/esmtprc 

$No Error

Please send me any solution for this and how could I make it work properly.
[COLOR=#888888]
-- 
[COLOR=#888888][COLOR=#006600][FONT=comic sans ms]Thanks & Regards,
Priyaranjan
System Design Engineer
[/FONT][/COLOR][/COLOR][COLOR=#888888]
[/COLOR][/COLOR]

---

