---
title: "Spamassassin Not Scanning?"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by mattbytes on 2011-02-16
I set up spamassassin using [THIS]("https://help.ubuntu.com/community/PostfixAmavisNew") guide.  I'm not receiving any errors, but I don't see spamassassin adding its email headers.

All I see is this: X-Virus-Scanned: Debian amavisd-new 

Do I need to feed mails through spamc using procmail?  Or should my emails be automatically scanned??

Matt

---

### Post by lisati on 2011-02-16
Perhaps Spamassassin hasn't recognised any spam yet......

---

### Post by mattbytes on 2011-02-16
No, even if it's not labeled spam (having a score of 5.0 or greater), spamassassin should still add its headers.

Here's an example from another system:
X-Spam-Checker-Version: SpamAssassin 3.2.4 (2008-01-01)
X-Spam-Level:
X-Spam-Status: No, score=-9.5 required=5.0 tests=BAYES_00,FH_DATE_PAST_20XX
        autolearn=no version=3.2.4

---

