---
title: "List guest session in GDM face browser"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by orlox on 2009-10-02
I'm trying to do this and I can't find how. I'm trying to see how to list the guest session (the one that can be accessed with the session indicator applet) on the GDM face browser, so users can login without a password there.

---

### Post by Amaranth on 2009-10-02
This is intentionally not allowed for security reasons. A currently logged in user has to give permission for someone to use the guest account by choosing the option from indication-session-applet.

---

### Post by orlox on 2009-10-02
> **Amaranth said:**
> This is intentionally not allowed for security reasons. A currently logged in user has to give permission for someone to use the guest account by choosing the option from indication-session-applet.

Awwww bummer...I just needed this cause in the computer I'm configuring there's a regular session that has a screensaver lock. People accessing the computer are supossed to be able to press on the "change user" option from the dialog to unlock the screen, and access the guest account through GDM.

Is this absolutely, hard-coded disabled?? Does anyone have a recommendation on how to handle this??

I thought about creating a guest user, but I want a true guest session so the files used by it are not persistent.

---

