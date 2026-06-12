---
title: "MS Echange"
date: 2019-11-04
forum: Installation &amp; Upgrades
---

### Post by mikelhayes on 2019-11-04
Howdy,
I'd like to dump Exchange and move away.
Does anyone have first hand knowledge of migrating to a Linux based email server ??
 That also works with Outlook/calendars/etc.

Thank you

---

### Post by TheFu on 2019-11-05
Zimbra.  It does much more than Exchange, but only the paid version has the thing called "push" ... whatever that is.  Zimbra supports all the standard IMAP, SMTP, CardDAV, CalDAV, et al protocols and Outlook does too.  I have zimbra hooked up to Thunderbird+Lightning and to Nextcloud modules for email, addresses, calendaring.

I didn't move off Exchange. We started with Zimbra to avoid Exchange ... in 2008.  Upgrades have been 'fun' over the last decade.  Avoid using a custom LDAP schema is my main advice.  Actually, it is probably best to use an external LDAP provider - external to Zimbra.   My last upgrade attempts failed, so I ended up dumping all the data for each userid, doing a fresh Zimbra install, then importing each user's data into the new install.  Thankfully, I'm above average at scripting.

For security reasons, we don't let Zimbra onto the internet directly. Instead we have an email gateway that handles all in/out SMTP traffic and end users have to use our VPN to gain network access to the IMAP and other Zimbra services.  This is a best practice anyway.  Initially the CxOs pushed back, until I showed them the logs of all the foreign IMAP login attempts from about 5 countries - mostly aimed at THEIR accounts.  If you aren't google, don't leave an imap email server on the internet directly, please.

---

### Post by tux-peng on 2019-11-07
I use fatmail, good carddav/caldav support

---

