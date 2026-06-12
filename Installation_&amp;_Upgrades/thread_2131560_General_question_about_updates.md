---
title: "General question about updates"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by nicolamenicacci on 2013-04-02
Good morning everyone,
Just a general question: I am experiencing some problems with Ubuntu 12.10 64 bit version after the march 21st upgrade with the new Linux image, something went wrong.
Those who have that version, made that upgrade and have Wine are still using it properly? it may be that I did something wrong during the upgrade, so it would be better to format the pc and install it all over again.
Thanks everybody in advance for your reply,

Nicola

---

### Post by darkod on 2013-04-02
Not all people do the update the same day. If you have a question for a specific kernel it's best to specify the exact kernel number. Like 3.5.0-XX, it depends which is the kernel that you are currently using.

Also, in the grub boot menu there should be section Previous versions, you can load an older kernel from there, for example the previous one. See if the issue exists there or not.

---

### Post by nicolamenicacci on 2013-04-02
> **darkod said:**
> Not all people do the update the same day. If you have a question for a specific kernel it's best to specify the exact kernel number. Like 3.5.0-XX, it depends which is the kernel that you are currently using.

Also, in the grub boot menu there should be section Previous versions, you can load an older kernel from there, for example the previous one. See if the issue exists there or not.

Hi Darko, thanks for your reply
That is actually quite a good idea! I'll load the previous kernel ad see if the problem is still there or not. The Kernel I was referring to is Linux version 3.5.0-26-generic
Thanks again for your reply,

Nicola

---

### Post by grahammechanical on 2013-04-02
> [COLOR=#000000]Those who have that version, made that upgrade and have Wine are still using it properly?[/COLOR]

So, the problem is with Wine? Please describe the problem. You should not need to re-install Ubuntu. You may need to re-install Wine or the Windows applications that you use under Wine but I do not see any need for that. First tell us the actual problems that you are experiencing.

Regards.

---

### Post by nicolamenicacci on 2013-04-02
While doing an upgrade that was divided in two, at a certain point it was said that Wine would have been deleted. Unfortunately, I clicked on the advancing button without payint to much attention, and now Wine has disappeared and for a problem of dependencies cannot be installed. And althugh i can run some applications on Virtualbox, I cannot fully take advantage of Wine, which is really anoying to me.
That is why I thought about formatting again, alas. It's been more than 10 days and no dependencies resolved, there must be something rotten in my ubuntu, I suspect

---

### Post by nicolamenicacci on 2013-04-04
I solved the issue reinstalling Ubuntu 12.10. Despite the new Linux image and kernel, Wine installed without a problem.
So it probably was a bug coming out some unfortunate update.
Thanks everyone for your contribution and kind help.

---

