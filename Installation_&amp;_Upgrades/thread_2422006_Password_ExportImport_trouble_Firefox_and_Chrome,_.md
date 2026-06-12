---
title: "Password Export/Import trouble Firefox and Chrome, to new Ubuntu Install"
date: 2019-06-30
forum: Installation &amp; Upgrades
---

### Post by adambond on 2019-06-30
New Comp Ubuntu 18.04.2 64bit, Firefox 65 

Old Comp Ubuntu 12.04 32bit, Firefox 52.0.2 


I have a new computer with fresh Ubuntu and firefox on it. 

Heres the issue. 

I need to export my old firefox data to the new firefox on the new computer. 

I managed to succefully create the "Old Firefox Data" folder using the "Refresh Firefox" method. 

I then tried copy/pasting that whole folder it into the new firefox directory.  It literally does  nothing. I go to check to see if the logins/passwords transferred over,  and its still empty. 

I can manage to copy/paste a bookmark file over  and get the bookmarks to  show up. But absolutely cannot get the logins/passwords to copy over. 

I tried pasting the "Old Firefox Data" file into the new firefox's  Local directory, AND even the root directory. With no luck for the  logins/passwords. :sad:

Any thoughts on how I can get this data transfered over?

---

### Post by uRock on 2019-06-30
I usually copy the whole .mozilla folder from the old to the new machine. Hit Ctrl+H to view hidden folders. The .mozilla folder can be found in your Home.

---

### Post by adambond on 2019-06-30
Ok. Will give that a try. Thank :D

---

### Post by adambond on 2019-06-30
> **uRock said:**
> I usually copy the whole .mozilla folder from the old to the new machine. Hit Ctrl+H to view hidden folders. The .mozilla folder can be found in your Home.

Before I try this, what should I do with the existing .mozilla folder currently on the new up to date computer (the one im trying to import passwords to)?

---

### Post by uRock on 2019-06-30
I renamed mine to .mozilla_old

---

### Post by CatKiller on 2019-06-30
> **uRock said:**
> I usually copy the whole .mozilla folder from the old to the new machine. Hit Ctrl+H to view hidden folders. The .mozilla folder can be found in your Home.

> **uRock said:**
> I renamed mine to .mozilla_old

This is exactly what I have done in the past, too, and it both works well and is easy to revert should you need to. Don't have Firefox running when you do it, though.

The equivalent also works for Chrome.

---

### Post by oldfred on 2019-06-30
I always copy entire profile for both Firefox & Thunderbird. They use same structures.
The profile for Firefox is in /home and .mozilla/firefox. The profile is xxxxx.default and uses profile.ini to know which profile is default. If new install of Firefox, you need to start it once to create a profile which then you can copy in old profile & edit profile.ini with old profile.

More details:
       thunderbird:
[https://support.mozilla.org/en-US/products/thunderbird](https://support.mozilla.org/en-US/products/thunderbird)
[https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer](https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer)
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate) 
   Firefox
[https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)
Firefox files:
[https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile](https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile)
[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles)

---

### Post by adambond on 2019-06-30
> **CatKiller said:**
> This is exactly what I have done in the past, too, and it both works well and is easy to revert should you need to. Don't have Firefox running when you do it, though.

The equivalent also works for Chrome.

WOW! Such a simple fix after hrs of trying to do it the other way.  
Copied .mozilla, 
 renamed the one im replaced with .mozilla_old
Opened firefox, 
It did not like how out of date it now was, so I downloaded its 'recommendation'. (.tar.bz file)
Restarted firefox, and BINGO all data transfered. 
Thank you. 

Now to try it with Chrome. I'll report back if I can or cant figure that one out.

---

