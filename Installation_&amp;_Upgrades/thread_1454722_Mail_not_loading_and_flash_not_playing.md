---
title: "Mail not loading and flash not playing"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by srikris on 2010-04-15
Dear members,
Iam new to linux environment. I have recently loaded ubuntu 9.10 with windows XP dual boot. But iam facing these problems.
 
1. Iam able open all web sites except gmail, yahoomail which iam able to open in XP. Do i need to install anything else?
 
2. Iam unable to open you tube videos, it says needs to install additional plugins but finally says unable to get plugins. Going thru forum, i have installed gnash mozilla from synaptic package manager. But still its not working...
 
Could some one help me in getting out of these issues.
Thanks in advance...
 
Sri

---

### Post by tommcd on 2010-04-15
> **srikris said:**
> 
1. Iam able open all web sites except gmail, yahoomail which iam able to open in XP. Do i need to install anything else?
For the mail problem, do you mean you can not go to those mail sites in firefox? Or are you talking about accessing them from a mail client like Evolution or Thunderbird? Can you go to: mail.yahoo.com in firefox?
For what it's worth, I have found that Thunderbird works better for email than Evolution. You can get Thunderbird in the Ubuntu repos.
 > **srikris said:**
> 
2. Iam unable to open you tube videos, it says needs to install additional plugins but finally says unable to get plugins. Going thru forum, i have installed gnash mozilla from synaptic package manager.
I would recommend removing gnash from synaptic. Then just install the **flashplugin-nonfree** (the flash from adobe.com) from synaptic or apt-get. That gnash plugin (while free as in freedom) does not seem to quite up to par with the proprietary flash from Adobe. 

And welcome to the Ubuntu forums!

---

### Post by srikris on 2010-04-16
Thanx for the reply Tommcd,

Flash player problem got resolved. ...

Regarding mail, firefox is not loading gmail and yahoomail pages.
i.e when i give [www.yahoomail.com](www.yahoomail.com) or [www.gmail.com](www.gmail.com), it says connection has timed out.

Sri.

---

### Post by tommcd on 2010-04-16
> **srikris said:**
> .
Regarding mail, firefox is not loading gmail and yahoomail pages.
i.e when i give [www.yahoomail.com](www.yahoomail.com) or [www.gmail.com](www.gmail.com), it says connection has timed out.

Glad you got the flash problem solved!
I can access those email pages you linked to very quickly without a problem. 
For yahoo mail, try using [http://mail.yahoo.com](http://mail.yahoo.com).
I think that you should first look into a possible DNS problem, or a problem with your ISP.
To rule out a DNS problem, try using Open DNS:
[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by srikris on 2010-04-17
I tried giving  [http://mail.yahoo.com]("http://mail.yahoo.com/") but still the same response not opening.

If the problem is with ISP then i shudnt be able to open in Windows XP as well right. (If my thinking is correct). But in XP i dont have any problem...
Do i need to chk something else
Sri

---

### Post by srikris on 2010-04-17
Hey ...
It got resolved. It was problem with the proxy settings which i manged to find out.
Thanks a lot for ur help.

Sri

---

