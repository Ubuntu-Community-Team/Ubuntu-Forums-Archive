---
title: "Apache2 Web Config"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by CYHPT.net on 2005-12-06
Hi all,

I hope theres a response to my post coz I really need this to be fixed. Here goes:

I have a little problem with my apache2 configuration. First of all, IM using the 5.04 Ubuntu, probably be upgrading it to 5.10 breezy soon. I have configured pretty much on what web server needs to be done, but everytime when I enter [http://localhost](http://localhost), it will come up with 2 folders instead of directly to the web page. And I am pretty sure I changed my DocumentRoot to the directory I want, but it still comes up with 2 folders listed.

Can someone tell me or advise me in any way I can do this correctly? I really like Ubuntu, and hopefully someone wud tell me wat the problem is.

Thanks in advance.

---

### Post by djur on 2005-12-18
I'm not sure where you are...    You need to have your files in /var/www.  You should have a file named index.html, and this should be the main part of your page.  Apache2 will list whatever is in the directly unless it finds a suitable page to display.  I believe it specifically looks for index.html.  The name "index.html" may be something you can change in some configuration file, but I don't know where.

Good luck.

---

