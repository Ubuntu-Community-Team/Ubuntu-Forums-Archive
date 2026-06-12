---
title: "No &quot;Answer Call&quot; for SIP and &quot;Accept request&quot; in XMPP in Empathy"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 321sebo123 on 2009-10-02
Hi, 

I have following issue with Empathy on the newest Karmic:
- when somebody is adding me to a contact list on XMPP I see an osd notification but I have no UI to accept the request
- when somebody is calling me on SIP I see an osd notification but I have no UI to answer the call
- when I minimize Empathy there is no icon to show it back (I have to click in the main menu).

3rd issue is not so annoying, but first two are just blockers for me.

Does anybody know if these issues are already reported (actually I haven't seen them in launchpad).

/S

---

### Post by xens on 2009-10-02
Same here :]

---

### Post by novafluxx on 2009-10-02
As far as I can tell, this is how Empathy is, and how it will stay for now, and until after Karmic is released, again, as far as I know.

If you want you can use the PPA, and no, I don't have the link.

---

### Post by 321sebo123 on 2009-10-02
Filled out bug for this:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/440865](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/440865)

I think that there should be panel at the top of Empathy with buttons, like shown when eg. protocol configured with wrong password.

---

### Post by tgpraveen on 2009-10-03
> **321sebo123 said:**
> Hi, 

I have following issue with Empathy on the newest Karmic:
- when somebody is adding me to a contact list on XMPP I see an osd notification but I have no UI to accept the request
- when somebody is calling me on SIP I see an osd notification but I have no UI to answer the call
- when I minimize Empathy there is no icon to show it back (I have to click in the main menu).

3rd issue is not so annoying, but first two are just blockers for me.

Does anybody know if these issues are already reported (actually I haven't seen them in launchpad).

/S

on the bug report pls everyone select affects me too

---

### Post by rdoolen on 2009-10-04
Go to preferences. On the 'Notifications' tab, de-select 'Use message indicators.' This should give you back the panel icon. When you get a SIP call, you can double click it to get the answer/reject dialog.

---

### Post by 321sebo123 on 2009-10-05
Wow - it is working now. It is not the best UI I have seen but at least I'm able to answer calls. 

Thanks!

/S

---

