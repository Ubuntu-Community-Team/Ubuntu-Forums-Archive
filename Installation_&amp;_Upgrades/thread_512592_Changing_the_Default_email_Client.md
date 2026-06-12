---
title: "Changing the Default email Client"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by Luft on 2007-07-29
I am trying to set my default email client to mozilla-thunderbird from the Kubuntu desktop.  (I installed Ubuntu and then the Kubuntu-desktop on top of it.)

But even after setting it in: K-Menu | System Settings | Default Applications | Use Different email Client

Evolution insists in coming up when I click on an email link from Firefox.

---

### Post by TBerben on 2007-07-30
1. Open Firefox
2. In the address bar type "about:config" (minus the quotes)
3. Check that the boolean "network.protocol-handler.external.mailto" is set to true
4. Right-click somewhere and choose New -> String
5. As name enter: network.protocol-handler.app.mailto
6. As value enter: kmail (or whatever mail client you wish to use)

That should do it

---

