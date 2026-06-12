---
title: "Flash installer - does it work with Chrome?"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ELD on 2010-04-02
I have done a fresh install of 9.10 on my desktop and had to do some copy and pasting jobby to get google chrome to have flash.

So a quick question, does the flash installer in software centre work with google chrome in lucid as it doesn't support it in karmic?

---

### Post by cheapsaket on 2010-04-02
Its going to come bundled with chrome.
see this: [http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html](http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html)

---

### Post by ELD on 2010-04-02
To quote that page though "There is no bundled Adobe Flash Player plug-in for 64-bit Linux." so still solves nothing for now.

---

### Post by cheapsaket on 2010-04-02
Well, I myself have used the how-to on this link to install it: [http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/](http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/)

Though it mentions firefox/xulrunner, you will find that flash will start working in chrome as well.

HTH

---

### Post by castrojo on 2010-04-02
I just did a new install today and just installed chrome and ubuntu-restricted-extras and flash just worked without any symlinking or anything special.

---

### Post by brimondyl on 2010-04-02
Just go to any site that needs flash, it will ask you if you want to install flash if you don't have it.

---

### Post by ELD on 2010-04-02
> **whiprush said:**
> I just did a new install today and just installed chrome and ubuntu-restricted-extras and flash just worked without any symlinking or anything special.

I haven't install that package yet.

---

### Post by utUtu on 2010-04-02
> **ELD said:**
> I have done a fresh install of 9.10 on my desktop and had to do some copy and pasting jobby to get google chrome to have flash.

So a quick question, does the flash installer in software centre work with google chrome in lucid as it doesn't support it in karmic?

For 64-bit flash, all you need is un-tar the Adobe labs 64-bit plugin into /usr/lib/mozilla/plugins.  Chrome, Firefox and Konqueror and possibly others find and take care of the rest.

---

### Post by zenarcher on 2010-04-02
I have had the same experience as whiprush.  I just installed restricted-extras, then installed Chrome and everything just works.

Cheers,
zenarcher

---

### Post by davehoz on 2010-04-04
> **zenarcher said:**
> I have had the same experience as whiprush.  I just installed restricted-extras, then installed Chrome and everything just works.

Cheers,
zenarcher

works for me 2.

---

### Post by ELD on 2010-04-04
Probably does work but i installed chrome first. I'm on 10.04 now with firefox anyway.

---

