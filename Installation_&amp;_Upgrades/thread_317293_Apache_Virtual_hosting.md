---
title: "Apache Virtual hosting"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by rpr on 2006-12-12
Hi,

I am looking for a way to create virtual hosting by using a mysql database but with _quota or bandwith limit_
Something like this [http://www.howtoforge.com/pureftpd_mysql_virtual_hosting]("http://www.howtoforge.com/pureftpd_mysql_virtual_hosting") but for apache or other webserver.

---

### Post by rpr on 2006-12-13
No one?

---

### Post by MJN on 2006-12-13
Try the **Server** forum - you'll probably get a better/bigger response.
 
Or indeed try a Google search - I came across all sorts of useful stuff when considering doing this some time back (I didn't require it in the end).
 
Mathew

---

### Post by rpr on 2006-12-14
> **MJN said:**
> Try the **Server** forum - you'll probably get a better/bigger response.
 
Or indeed try a Google search - I came across all sorts of useful stuff when considering doing this some time back (I didn't require it in the end).
 
Mathew

I tried google.
All what I find is this:
Virtual users in MYSQL but without quota support!

For the quota support I find a plugin to allow virtual hosting to have quota but it requires some text in the virtual user config file.

That is why I post this on the forum. I can't find anything like that and I just can't believe it.
All virtual users from Postfix to proftpd has got support for quota but a webserver like apache don't?

---

### Post by MJN on 2006-12-14
The reason I suggested the 'Server' sub-forum is that this isn't an 'Installation & Upgrades' issue.
 
With regards to Google what did you search for? I did a search for **'apache quota bandwidth'** ([http://www.google.co.uk/search?hl=en&q=apache+quota+bandwidth&meta=](http://www.google.co.uk/search?hl=en&q=apache+quota+bandwidth&meta=)) and came up with the following as result number 1:
 
[http://cband.linux.pl/](http://cband.linux.pl/)
 
'mod_cband is an [COLOR=black]Apache 2[/COLOR] module provided to solve the problem of limiting users' and virtualhosts' bandwidth usage. The current versions can set virtualhosts' and users' bandwidth quotas, maximal download speed (like in mod_bandwidth), requests-per-second speed and the maximal number of simultanous IP connections (like in mod_limitipconn).'
 
Result number 2 is the following, a Debian HowTo on mod_cband:
 
[http://www.howtoforge.com/mod_cband_apache2_bandwidth_quota_throttling](http://www.howtoforge.com/mod_cband_apache2_bandwidth_quota_throttling)
 
Aren't both of these _exactly_ what you're looking for or have I misunderstood your question? :confused: 
 
Mathew

---

### Post by rpr on 2006-12-14
> **MJN said:**
> The reason I suggested the 'Server' sub-forum is that this isn't an 'Installation & Upgrades' issue.
 
With regards to Google what did you search for? I did a search for **'apache quota bandwidth'** ([http://www.google.co.uk/search?hl=en&q=apache+quota+bandwidth&meta=](http://www.google.co.uk/search?hl=en&q=apache+quota+bandwidth&meta=)) and came up with the following as result number 1:
 
[http://cband.linux.pl/](http://cband.linux.pl/)
 
'mod_cband is an [COLOR=black]Apache 2[/COLOR] module provided to solve the problem of limiting users' and virtualhosts' bandwidth usage. The current versions can set virtualhosts' and users' bandwidth quotas, maximal download speed (like in mod_bandwidth), requests-per-second speed and the maximal number of simultanous IP connections (like in mod_limitipconn).'
 
Result number 2 is the following, a Debian HowTo on mod_cband:
 
[http://www.howtoforge.com/mod_cband_apache2_bandwidth_quota_throttling](http://www.howtoforge.com/mod_cband_apache2_bandwidth_quota_throttling)
 
Aren't both of these _exactly_ what you're looking for or have I misunderstood your question? :confused: 
 
Mathew

Yeah I found that one too.
But the virtual host users are in mysql. The quota plugin require virtual hosts in a file.

I appreciate the input.

---

