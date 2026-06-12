---
title: "Firefox redirecting random pages"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by synd7 on 2009-10-05
I recently installed a fresh Alpha 6 which is now fully up to date.

When browsing using firefox certain webpages are redirected, usually to google (my homepage), a mozilla page about firefox or to an blank apache page ("Great Success ! Apache is working on your cPanel® and WHM™ Server") and occasionally one that just says "It works!"

Its pretty inconsistent, if i close firefox and re-open it a few times it will go away, but it will come back soon after.

facebook is the major one that gets redirected, facebook.com is always redirected. facebook.com/home.php is redirected about half the time.

some that are redirected (say domain.com/example/index.html) only get the domain redirected (firefox tries to load google.com/example/index.html)


Is this a known issue? any ideas on what might be causing it?

---

### Post by synd7 on 2009-10-12
Nobody else is experiencing this?

If its a problem with my machine, does anyone have any idea what might be causing it?

---

### Post by emarkay on 2009-10-12
If it was windows I'd say VIRUS!

Create a new profile and see if that happens still, if not, it's prob an add-on or plug-in issue.  Do you have any installed.  If NOT, I suggest NoScript and see what it's catching.

Have you done any "tweaks" to FF?

Also I'd seriously recommend going to the Beta version at this point.

---

### Post by synd7 on 2009-10-12
No tweaks, no plugins installed, just the "ubuntu firefox modifications" one. Disabling that make no difference.
Noscript didnt find anything unusual.

Do you mean a firefox beta or karmic beta?
My karmic is up to date, might try doing a fresh install from the beta or RC. Hell, i'll probably end up doing a fresh install when karmic is officially released anyway.

---

### Post by emarkay on 2009-10-12
Generally once you have a fresh install of a Beta it gets updated as normal, through  RC and then to release standards, but I would suggest maybe FWIW doing a fresh install if possible of each milestone for testing purposes.

I have no idea on the redirect issue - I have not seen it - maybe  something yout ISP is doing - some have "speedup" caches that get AFU at times..  Also are you using Open DNS?  I am .
[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by seeker5528 on 2009-10-12
DNS redirection seems to be pretty popular these days, Comcast does it (other ISPs too), OpenDNS does it (but I believe OpenDNS gives you a way to disable the redirections). This type of redirection should be pretty obvious who is doing it (always the same type of page, not random) and normally should only happen for the 404 errors, but may also happen if a site takes to long to respond.

But this:

> **synd7 said:**
> When browsing using firefox certain webpages are redirected, usually to google (my homepage), a mozilla page about firefox or to an blank apache page ("Great Success ! Apache is working on your cPanel® and WHM&#8482; Server") and occasionally one that just says "It works!"

sounds a bit hinky. 

The "It works!" message is default page for Apache when it's newly installed.

The cPanel thing appears to be:

[http://en.wikipedia.org/wiki/CPanel](http://en.wikipedia.org/wiki/CPanel)

And the google and about firefox redirections are even odder still.

If you have a router that does DNS forwarding instead of passing you directly through to an external DNS server and you use DHCP, there could be some weird interaction there. If you can find an option for that in your router configuration, it might be worth turning it off there, or you might try to specify the DNS instead of picking it up through DHCP.

You might also look at the proxy settings in firefox.

Looking at the extensions that are insalled (and possibly plugins) and disabling them seems like a good step too 'tools --> add-ons'.

Don't know what to suggest other than that.

Later, Seeker

---

### Post by synd7 on 2009-10-19
Just an update, the problem completely went away by disabling ipv6.

I did this by adding "ipv6.disable=1" to the line containing "GRUB_CMDLINE_LINUX_DEFAULT=" in /etc/default/grub

---

