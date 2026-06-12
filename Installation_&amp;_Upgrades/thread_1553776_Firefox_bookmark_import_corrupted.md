---
title: "Firefox bookmark import corrupted"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by lisa374 on 2010-08-15
When importing bookmarks, created by Windows XP, Firefox V 3.6.8, into Ubuntu 10.04 Firefox V 3.6.8 they are not complete:o
My 3 levels of bookmarks are correct in Win XP SP3 but when imported, either via HTML or JSOC files, no bm's show up except first and second level folders. The bm's contained within are not displayed. I've removed and reinstalled Firefox, used both methods of importing bookmarks and tried several iterations of the above. Nothing seems to work:(
What should I try next?

---

### Post by lovinglinux on 2010-08-15
You could simply copy the file *places.sqlite* from your Windows machine Firefox profile into the Ubuntu Firefox profile, assuming you still have access to the Window system and don't need to merge bookmarks.

If you need to merge the bookmarks, then install  [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/") extension in the Windows machine and sync your bookmarks with the server. Then install the extension on Firefox Ubuntu and sync again.

---

### Post by lisa374 on 2010-09-03
Thanks for the info.
That did the trick.:D

---

### Post by lovinglinux on 2010-09-03
> **lisa374 said:**
> Thanks for the info.
That did the trick.:D

You are welcome.

---

