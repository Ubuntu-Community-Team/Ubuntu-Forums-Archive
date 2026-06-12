---
title: "Google Chrome reports &quot;Your profile could not be opened correctly&quot; when opened"
date: 2014-11-20
forum: MINT
---

### Post by rewyllys on 2014-11-20
As a user of Linux Mint 17, I've repeatedly encountered -- during the last 2 or 3 days -- a problem when opening Google Chrome. (It's my impression that the problem is associated with the latest update to Chrome, #39...)  The problem is that upon opening, Google Chrome reports, "Your profile could not be opened correctly."

When I Googled the problem (in Firefox), the most potentially useful set of suggestions I found was this:
"1.        Quit Google Chrome.2.        Open a shell.
3.        Change directory (cd) to ~/.config/google-chrome/Default
4.        Delete the file named "Web Data": rm -rf Web\ Data;
5.        Start Google Chrome and the error should be gone."

But I tried these steps, more than once, without success.  In fact, after installing Chrome, I couldn't even succeed in opening it.

I finally used the Synaptic Package Manager to remove Chrome entirely.  Then I used the SPM to install Chromium.

Chromium is working satisfactorily -- so far, at least <fingers crossed>.

---

### Post by chris36 on 2014-11-21
Thumbs up for the workaround.

---

### Post by rewyllys on 2014-11-23
I'm sorry to have to report that Chromium is not a solution to this problem after all.  At least, my desktop's copy of it has started displaying the "Your profile could not be opened correctly" warning.

For me, the new workaround is to click repeatedly on the warning messages till they cease (after 6 or 7 times is my guess; I haven't actually counted).  Thereafter, I leave Chromium open all the time.

---

