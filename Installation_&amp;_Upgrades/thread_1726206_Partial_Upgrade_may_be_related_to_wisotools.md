---
title: "Partial Upgrade may be related to wisotools"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by tombola on 2011-04-10
I'm wondering whether anyone has had Partial Upgrade issues recently on Ubuntu 10.04? I have and I suspect it is linked to wisotools, which has apparently become extraneous.

I've have had a week of saying no to messages from Update Manager asking would I like to do a Partial Upgrade. I'd been expecting that sooner or later this request would be replaced by the standard request to do an update. When this didn't happen I took the first step of a partial upgrade and ascertained that it would involve upgrading of 23 packages, and removal of one: wisotools. I cancelled the Partial Upgrade, as I'm wary of corrupting my installation, and then removed wisotools independently (using Ubuntu Software Centre). After that, I ran the Update Manager, and it was happy to proceed with a normal Update, not a Partial Upgrade. 

Was this the right way to resolve this issue? Should I try a similar course of action if this issue occurs again in the future?

---

### Post by Dutch70 on 2011-04-10
I've never had that problem, but I think you may find this interesting to say the least.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1479146[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1479146")

---

### Post by tombola on 2011-04-12
Thanks Dutch70 - I have come across that thread before ([[COLOR=RoyalBlue]http://ubuntuforums.org/showthread.php?t=1479146[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1479146")). It suggests that 

[LIST]
[*]users of LTS versions of Ubuntu (like me) wouldn't have to deal with inconsistencies in the dependencies, and therefore shouldn't get the "Partial Upgrade" question.
[*]and that even if they did, waiting a few hours before reactivating Update Manager would get rid of the "Partial Upgrade" question, and allow a normal update.
[/LIST]
It doesn't explain what's happened in my case, nor what should be done! I've found my workaround for now, so I'm not too fussed. I suspect there's an insight here for the developers/debuggers. Thanks for your response.

---

### Post by Dutch70 on 2011-04-12
No problem, sorry I couldn't be of more help.

---

