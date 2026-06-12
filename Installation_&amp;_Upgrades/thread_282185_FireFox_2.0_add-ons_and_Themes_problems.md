---
title: "FireFox 2.0 add-ons and Themes problems"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by bpalyshka on 2006-10-22
**hello**

HI im new to the forums; im sure you haven't heard that before.  

anyways I recently upgraded to xubuntu 6.10 and its working great i have no problems what so ever, except all the extensions and add-ons no longer work with the version of Firefox im using.  

Opera works great, its just Firefox 2.0.

Any suggestions?  I could use a theme like a fat kid needs cake.](*,) ](*,) 

thanks

Ben

---

### Post by pradeepadapa on 2006-10-22
hii,

          actually some themes still donot have the compatibility to work in firefox 2.0. to find out which themes work in firefox 2.0 u can see in the add-ons directory in firefox website, so dont worry the compatibility for those themes nd add-ons will be released in a few days, so be patient.

---

### Post by oliwally on 2006-11-03
After I upgraded to edgy (and Firefox 2) I can no longer access addons.mozilla.org, either through the browser or the Tools-Add-ons menu. Does anyone know what the problem may be? 

I kind of remember some similar problem some years ago with the version listing in about:config in Firefox and changing that to a different version then allowing access to the site.

Any ideas?

---

### Post by maprx on 2006-11-04
I am using 2.0 themes with firefox 2.0 and the themes to not change.  The theme windows indicates something is missing.  over at firefox, i got stupid replies like are you using 2.0 themes?


here is a screen shot of the error, what additional is needed.  click on any theme and they all come up with this

---

### Post by oliwally on 2006-11-09
> **oliwally said:**
> After I upgraded to edgy (and Firefox 2) I can no longer access addons.mozilla.org, either through the browser or the Tools-Add-ons menu. Does anyone know what the problem may be? 

I kind of remember some similar problem some years ago with the version listing in about:config in Firefox and changing that to a different version then allowing access to the site.

Any ideas?

I still need some help with this issue please. Does anyone have a solution?

---

### Post by Blur-king on 2006-11-10
Hi Was there a promt from firefox that "software installation is disabled". If there is then you have to enable it. Type **about:config** in the address bar. Then look for **xpinstall.enabled  **if the value is false, double-click it to change it to **true**   You can then restart firefox. hope this works.

         [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by oliwally on 2006-11-10
> **Blur-king said:**
> Hi Was there a promt from firefox that "software installation is disabled". If there is then you have to enable it. Type **about:config** in the address bar. Then look for **xpinstall.enabled  **if the value is false, double-click it to change it to **true**   You can then restart firefox. hope this works.


Thanks so much for helping out. No, there was no such prompt. I've checked the config and it's already on 'true' and I still can't get to the site.

Are there other suggestions please?

---

### Post by oliwally on 2006-11-10
I've done some more playing around and found that if I access addons.mozilla.org using Konqueror first, then Firefox will also be able to access the site after this (even if I then close Konqueror)

This lasts a few minutes, then I have to access the site in Konqueror again.

What's going on?

---

### Post by oliwally on 2006-11-11
> **oliwally said:**
> I've done some more playing around and found that if I access addons.mozilla.org using Konqueror first, then Firefox will also be able to access the site after this (even if I then close Konqueror)

This lasts a few minutes, then I have to access the site in Konqueror again.

What's going on?

Please, please help

---

### Post by Blur-king on 2006-11-11
[http://forums.mozillazine.org/viewtopic.php?t=106431&start=0&postdays=0&postorder=asc&highlight=&sid=8cdf479b6c71324d4aa08b7f13366533](http://forums.mozillazine.org/viewtopic.php?t=106431&start=0&postdays=0&postorder=asc&highlight=&sid=8cdf479b6c71324d4aa08b7f13366533)  Hi have you try the firefox FAQ or forum. They may be able to help.

---

### Post by oliwally on 2006-11-11
Thanks Blur-king,

I went to the site, more specifically to 

[http://kb.mozillazine.org/Error_loading_any_website](http://kb.mozillazine.org/Error_loading_any_website)

and there read to try to disable ipv6 
> 

The problem may be with IPv6 ("Internet Protocol version 6"). To disable IPv6, change the preference network.dns.disableIPv6 from "false" to "true" . Here are the steps:

   1. Type about:config in the address bar, press Enter.
   2. Find network.dns.disableIPv6 in the list.
   3. Right-click -> Toggle.
   4. Restart Firefox/Mozilla Suite and try again. 

If this doesn't work, re-enable IPv6 by resetting the preference to "false". 

So far it works

---

