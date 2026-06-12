---
title: "Firefox gets locked up"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by TallMatthew on 2008-04-10
Ever since an update pushed out a couple of weeks ago, Firefox has become more or less unusable.

It will get stuck, no longer connecting to any website.  The message bar reads "looking up <website>" and nothing happens.  Open a new tab and try to connect to another site ... it won't come up either.

Close firefox, then reopen it, the problem disappears.  But this has become a necessity a half-dozen times a day.

It's not a DNS issue.  I use my own BIND to resolve, and "host <website>" returns immediately.
It's not an IPV6 issue.  I disabled IPV6 and the problem recurs.
It's not an isolated issue.  I have three machines at home, and all are broken.
It's not a network issue.  No other network applications are affected.

I've switched to Swiftfox, which works fine.  But I wonder what the underlying issue could be.

---

### Post by BobbyIceCubes on 2008-04-10
Matt, If you are running the beta version of FF that comes with Hardy Heron as I am, you will see it lock up. I was informed by one of the guys on my Linux team here that they have some underlying bug fix about ready to be released. My issue was Flash related,  then an issue with PDFs opening, finally it was a Java related bug. In my case with the PDFs it hosed my machine for 10 minutes... I also went to SwiftFox, and all is good. (If it can be broken, I usually find it...)

---

