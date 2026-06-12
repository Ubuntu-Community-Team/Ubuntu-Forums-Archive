---
title: "Empathy and gchat/gtalk"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-09-09
In jaunty I could add a google account in empathy and then use it to chat and talk with other people. In karmic, I don't see an option to add a gtalk account. Has it been renamed or am I missing something?

---

### Post by 243kof on 2009-09-10
Yes, you should just select "Jabber" as account type.

---

### Post by dholbert on 2009-09-14
Yeah, the Google Talk pre-set configuration seems to have disappeared in Karmic.

You want to just select "Jabber", with these settings (copied from my Ubuntu Jaunty configuration, with different checkbox settings for more security)

****
Login ID: [email]johndoe@gmail.com[/email]
Password: [gmail password]

ADVANCED
Encryption Required: CHECKED
Ignore SSL errors: UNCHECKED
Resource: Telepathy
Priority: 0
Server: talk.google.com
Port: 5222  [This should get filled in automatically]
Use Old SSL: UNCHECKED
****

---

### Post by Longinus00 on 2009-09-14
Thanks for the fix. Too bad it's so unintuitive for people who don't know the protocol gchat is using.

---

### Post by Tibuda on 2009-09-14
> **Longinus00 said:**
> Thanks for the fix. Too bad it's so unintuitive for people who don't know the protocol gchat is using.

I agree. The protocol name should be "XMPP/Jabber/Google Chat", so it covers the protocol name (XMPP) and the two main providers (Jabber and Google).

---

### Post by psyke83 on 2009-09-14
Are you folks up-to-date? I see the Google Talk account type listed in Empathy's Accounts window.

---

### Post by Longinus00 on 2009-09-14
> **psyke83 said:**
> Are you folks up-to-date? I see the Google Talk account type listed in Empathy's Accounts window.

I just checked and it has indeed been added back to the accounts list. I wonder why it was ever missing in the first place?

---

