---
title: "*Tip* Manage cookies in Firefox 3.5.3 (Ubuntu 9.10)"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ikisham on 2009-10-15
In Karmic Koala/Firefox 3.5.3 the Privacy tab in Edit>Preferences doesn't give any option to manage cookies besides deleting them. And the default settings are to _allow all cookies for the time the cookies themselves supply_.
So we must open a tab and type ```
about:config
``` in the address bar and click *ok* when asked for confirmation.
Then type *network* in the search box and look for the following strings:
[B]
network.cookie.cookieBehavior[/B]

Its option are:
0 - allow all cookies (default)
1 - allow for the originating site only
2 - block all cookies

**network.cookie.lifetimePolicy**

Its options are:
0 - last for as much as the cookie itself determines (default)
1 - ask the user
2 - last for the session only
3 - number of days specified


After any of these settings have been changed, the Privacy tab under Edit>Preferences will give the option to manage cookies again.


**How to whitelist cookies if default is set to *block***

When in a page from which we want to allow cookies, click on Tools>Page Info or just press Ctrl+I, go to the Permissions tab and set any preference for that site (this may be used to block cookies from a site when the default is set to *allow*).

*Reference:*
[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)
[http://support.mozilla.com/en-US/kb/Blocking+cookies](http://support.mozilla.com/en-US/kb/Blocking+cookies)

---

### Post by philinux on 2009-10-15
I always block all cookies and use a whitelist.

---

### Post by tekstr1der on 2009-10-15
> **ikisham said:**
> In Karmic Koala/Firefox 3.5.3 the Privacy tab in Edit>Preferences doesn't give any option to manage cookies besides deleting them. And the default settings are to _allow all cookies for the time the cookies themselves supply_.
So we must open a tab and type ```
about:config
``` in the address bar and click *ok* when asked for confirmation.
Then type *network* in the search box and look for the following strings:
[B]
network.cookie.cookieBehavior[/B]

Its option are:
0 - allow all cookies (default)
1 - allow for the originating site only
2 - block all cookies

**network.cookie.lifetimePolicy**

Its options are:
0 - last for as much as the cookie itself determines (default)
1 - ask the user
2 - last for the session only
3 - number of days specified


After any of these settings have been changed, the Privacy tab under Edit>Preferences will give the option to manage cookies again.


**How to whitelist cookies if default is set to *block***

When in a page from which we want to allow cookies, click on Tools>Page Info or just press Ctrl+I, go to the Permissions tab and set any preference for that site (this may be used to block cookies from a site when the default is set to *allow*).

*Reference:*
[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)
[http://support.mozilla.com/en-US/kb/Blocking+cookies](http://support.mozilla.com/en-US/kb/Blocking+cookies)

Umm... All these settings are exposed through the UI.
You need to select "Use custom settings for history" from the first dropdown on the privacy tab.

---

