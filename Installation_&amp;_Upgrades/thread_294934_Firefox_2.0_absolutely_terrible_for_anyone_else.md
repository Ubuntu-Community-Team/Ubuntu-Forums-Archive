---
title: "Firefox 2.0 absolutely terrible for anyone else?"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by CheeseEatingBulldog on 2006-11-07
Ever since I upgraded to edgy I have been annoyed at the terrible stability and general use of the new firefox, and just wanted to know if any one else has had these problems.

Firefox randomly just 'vanishes', each time I start it it asks me to restore the last session (eventhough I closed it normally), it is unbelievably slow (even with fasterfox) and I can't get it to open new links in tabs OUT of focus.

Aside from that I think the close tab option on each tab is very annoying and am seriously thinking of downgrading to FF 1.5, if not just for speed/load times which were half what they are now.

Any other people with this mindset/problems?

---

### Post by CallsignBaron on 2006-11-07
I am not exactly thrilled with Firefox 2.0 either I find that [Swiftfox]("http://getswiftfox.com/") or even [Opera]("http://www.opera.com/") to be a better and faster alternative. As for opening links in tabs out of focus just middle click the link and it should open in a new tab behind the others.

---

### Post by Suzan on 2006-11-07
Firefox 2 works like a charm for me.

Have you tried it with a clean Firefox-Profile?

---

### Post by CheeseEatingBulldog on 2006-11-07
*Have you tried it with a clean Firefox-Profile?*

Yeah great, then I lose two years of links, customisations setup. No thanks.

---

### Post by itchanddino on 2006-11-07
Your problem sounds like the known flash problem with firefox 2.0. 
[http://ubuntuforums.org/showpost.php?p=1673725&postcount=23]("http://ubuntuforums.org/showpost.php?p=1673725&postcount=23")
This solution should work, it did for me.

---

### Post by CheeseEatingBulldog on 2006-11-07
Thanks for that, but that still doesn't account for the slow speed. Will see what happens, otherwise I will just downgrade.

---

### Post by OffHand on 2006-11-07
It flies here and never crashes.

---

### Post by Cool Surfer on 2006-11-07
Just noticed this release has firefox2 inbuilt. It didnt work for me
initially. But then someone had suggested me to do this
in address bad type
about:config
ipv
set value from false to true (double click)
and then close browser n try a new window. Firefox was never faster:)

---

### Post by billylh on 2006-11-07
ive noticed that firefox runs great on my edgy machine at home and even windows xp(both 32) but it runs terrible on my win pro x64.  it actually causes all the same problems, the auto quit,always asks to restore sessions or start new, freezing the system, constant flash install dialogs, and sometimes it even opens multiple instances of firefox without actually showing the browser. could be a 64bit thing?

---

### Post by ronmarley1 on 2006-11-07
> **CheeseEatingBulldog said:**
> 
Aside from that I think the close tab option on each tab is very annoying and am seriously thinking of downgrading to FF 1.5, if not just for speed/load times which were half what they are now.
Here's a tweak for this issue.  I didn't try it because I like the "Close" button on each tab.  Hope it works:
Found this using "firefox 2.0 tweaks" at Google.
Type about:config in the address bar and follow below.  
Another tab interface change in Firefox 2 is the addition of a close button on each individual tab. I happen to love this, but some hate it, saying it causes them to accidentally close a tab when just trying to switch to it. If you're a hater, revert to the Firefox 1.5 behavior by changing the browser.tabs.closeButtons value to 3. This will not display close tabs on individual tabs, and turn on a single close tab button at the right end of the tab bar.

    * Key: browser.tabs.closeButtons
    * Modified Value: 3 (revert to Firefox 1.5 behavior)
    * Alternate Modified Value: 2 (don't display any close tab buttons)
    * Default: 1 (display close buttons on all tabs)

---

### Post by CheeseEatingBulldog on 2006-11-08
Thanks **Ronmarley**! That is frikkin awesome!

---

### Post by ronmarley1 on 2006-11-08
> **CheeseEatingBulldog said:**
> Thanks **Ronmarley**! That is frikkin awesome!
Glad I could help.  Hope things improve...  I've had a couple of issues with FF 2.0 also.

---

