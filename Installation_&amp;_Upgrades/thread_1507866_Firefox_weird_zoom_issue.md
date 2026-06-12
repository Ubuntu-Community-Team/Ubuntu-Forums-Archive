---
title: "Firefox weird zoom issue"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by danbaark on 2010-06-12
I'm running Firefox Namoroka 3.6.3 (As Namoroka as I have the smooth scaling ppa installed).

It was working fine but weirdly all of a sudden the zoom settings seem very inconsistent. Some pages, like the ubuntu google start page load fine. Many others like google searches or timesonline.co.uk for example, load completely zoomed out. Using ctrl + or the zoom menu I can zoom in but navigating within the page immediately resets it to being zoomed out. 

I don't have any zoom related add-ons installed. Also the error console throws out a whole load of errors mostly 'unknown property declaration dropped errors'.

Anyone know what's going on here?

Thanks very much

---

### Post by khelben1979 on 2010-06-12
You say you don't have any zoom addons installed, but what about other addons? I know that some addons can cause bugs in the web browser because they don't work well together. Have you checked that?

[http://kb.mozillazine.org/Problematic_extensions]("http://kb.mozillazine.org/Problematic_extensions")

---

### Post by danbaark on 2010-06-12
Hi Khelben,

I've got a couple of add-ons installed but the only one that is actually enabled is the Ubuntu modifications pack (I assume there's no problem with that?)

All other add-ons are disabled but were working before this bug appeared so I don't think they are the problem really.

Thanks

---

### Post by danbaark on 2010-06-13
I'm pretty sure it must be something set in my profile as I've noticed this occurs in firefox on my windows partition too (Dual-boot shared profile)

Anyone know what's going on?

Thanks very much

---

### Post by khelben1979 on 2010-06-13
> **danbaark said:**
> (Dual-boot shared profile)

I think that's the source of your problem. Try with using 2 profiles instead.

---

### Post by danbaark on 2010-06-13
Why would sharing the profile cause this problem in itself? I have had firefox working fine previously using a shared profile like this so I think it should be able to work.

Would like to keep it this way if possible so I can keep bookmarks etc synced easily.

Is there any profile setting or anything like that I could have changed?

---

### Post by khelben1979 on 2010-06-13
> **danbaark said:**
> Why would sharing the profile cause this problem in itself? I have had firefox working fine previously using a shared profile like this so I think it should be able to work.

Bug in the browser version maybe? Hmm.. have you tried downgrading the web browser? Also, helping the developers sending a bug report might be a good idea if you can be certain it's because of this specific version of the browser you're using.

---

### Post by danbaark on 2010-06-13
I've tried to change to the branded version of 3.6.3 and the 3.6.4 beta and had the same problem in all 3.

thanks for the help, I'm really stumped here

---

### Post by danbaark on 2010-06-18
Bump?

---

### Post by danbaark on 2010-06-20
I've noticed that the issue disappears when I use the In Private browsing mode - does that help identify the problem at all?

Thanks very much

---

### Post by khelben1979 on 2010-06-20
> **danbaark said:**
> I've noticed that the issue disappears when I use the In Private browsing mode - does that help identify the problem at all?

Thanks very much

If the issue disappears when doing so, then this problem would be solved now, wouldn't it?

Also, you can try experimenting with different [firefox zoom addons]("https://addons.mozilla.org/en-US/firefox/search/?q=zoom&cat=all&lver=any&atype=0&sort=&pid=1&pp=20&lup=&advanced=") if you feel like doing so.

---

### Post by danbaark on 2010-06-20
Well no, as it still doesn't work correctly in normal mode, would quite like to understand what's going on here. It seems like it should just be an obvious about:config setting or something, but I can't seem to find anything.

Thanks for the help

---

### Post by danbaark on 2010-06-21
I've also tried to restore the profile to one that I know works (from another computer) and this hasn't helped.

Would really love to get this sorted so I can go back to using firefox.

---

### Post by danbaark on 2010-06-23
When I set firefox to use text-only zooming, it loads the pages normal size but with all the text zoomed right out to the minimum. It seems to somehow be set to automatically zoom right out of every page on load. Is there any way I could have set something like this?

---

### Post by danbaark on 2010-06-24
I've also found that going into about:config and toggling browser.zoom.siteSpecific value to false enables all pages to load normally with zoom reset (however leaving this set as false obviously means that firefox doesn't remember any sites I've zoomed in on)

Toggling it back to true immediately causes sites to zoom right out again.

---

