---
title: "Postgrey regex"
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by cle-ziskind on 2015-12-29
I'm told Postgrey uses standard regexes; more's the pity for me, as I can't get my brain in gear to figure them out.

How do I spec *.domain.com as a regex?

Thanks!

---

### Post by SeijiSensei on 2015-12-29
\.domain\.com$ will match anything ending in "domain.com".  The dollar sign represents the end of the string.  If "domain.com" appears within a longer text string, omit the dollar sign.

The backslash character "escapes" the special meaning the period has in a regex.  Usually a period is a wildcard for any single character, but "\." will treat the period as the actual character itself.

There are a lot of regex guides and tutorials on the Internet.  Give Google a try.

---

### Post by cle-ziskind on 2015-12-30
> **SeijiSensei said:**
> \.domain\.com$ will match anything ending in "domain.com".  The dollar sign represents the end of the string.  If "domain.com" appears within a longer text string, omit the dollar sign.

The backslash character "escapes" the special meaning the period has in a regex.  Usually a period is a wildcard for any single character, but "\." will treat the period as the actual character itself.

There are a lot of regex guides and tutorials on the Internet.  Give Google a try.

Thanks for the explanation. I *did* try Google, then my brain exploded. "Cleanup on Aisle Three!"
This is the kind of thing I would pay money (ok, a micropayment) for. Anyone know of such a site?

---

