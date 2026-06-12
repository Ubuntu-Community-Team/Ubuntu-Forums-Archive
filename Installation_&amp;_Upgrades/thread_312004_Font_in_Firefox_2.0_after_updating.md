---
title: "Font in Firefox 2.0 after updating"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by cisoprogressivo on 2006-12-03
i've updated manually my firefox 2.0 (i have Ubuntu Dapper 6.06).
But after updating my firefox does not show pages with the Dejavu font (as in Firefox 1.5), but in another font.
Also if i change the font in the preferences the font of the page does not change.
So i have selected Dejavu, but nothing happen.
Someone can help me?
:confused: 
Thanks

---

### Post by mssever on 2006-12-03
> **cisoprogressivo said:**
> i've updated manually my firefox 2.0 (i have Ubuntu Dapper 6.06).
But after updating my firefox does not show pages with the Dejavu font (as in Firefox 1.5), but in another font.
Also if i change the font in the preferences the font of the page does not change.
So i have selected Dejavu, but nothing happen.
Someone can help me?
:confused: 
Thanks

Just a stab in the dark here, but what happens if you toggle the option to not allow pages to specify their own fonts? I'm just wondering if you're running into a CSS issue.

---

### Post by cisoprogressivo on 2006-12-04
> **mssever said:**
> Just a stab in the dark here, but what happens if you toggle the option to not allow pages to specify their own fonts? I'm just wondering if you're running into a CSS issue.
Hi mssever, thanks for interesting.
I've already tried to toggle the option, but nothing changes. ](*,)

---

### Post by mssever on 2006-12-04
> **cisoprogressivo said:**
> Hi mssever, thanks for interesting.
I've already tried to toggle the option, but nothing changes. ](*,)

Hmm... I really don't know, then. Have you looked through about:config (type that in the address bar)? There might be something there--or there might not... :-k

---

### Post by pumpapa on 2006-12-04
see also thread  	
Google Docs & Firefox 2.0 fonts mutually exclusive?

---

### Post by capital on 2007-02-19
The problem is with Firefox, not the system.  Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

