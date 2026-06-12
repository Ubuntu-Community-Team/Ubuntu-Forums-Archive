---
title: "livepatchd error: The platform Ubuntu 22.10 is not supported."
date: 2024-05-27
forum: Installation &amp; Upgrades
---

### Post by rjgoverna on 2024-05-27
Upgraded successfully from Mantic to Noble via standard upgrade method (no -d or other trickery used).

Enrolled Ubuntu Pro but seeing errors, namely "livepatchd error: The platform Ubuntu 22.10 is not supported."

I am obviously not running 22.10 so something is not quite right. How to correct it? Many thanks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293816&stc=1[/IMG]

EDIT: forced reinstall of ubuntu-pro-client, didn't fix it.

---

### Post by corradoventu on 2024-05-27
ubuntu-pro is only for LTS version. what version are you using? upgrade completed or?

---

### Post by rjgoverna on 2024-05-27
> **corradoventu said:**
> ubuntu-pro is only for LTS version. what version are you using? upgrade completed or?

Yep. It's all there, I'm running 24.04 LTS, aka Noble:
> [COLOR=#000000]_Upgraded successfully_ from Mantic to **Noble** via s_tandard upgrade method_ (no -d or other trickery used).[/COLOR]

You can see I've successfully enrolled Pro. As per the screenshot, *esm-apps* and *esm-infra* are fine but *livepatch* seems to think I'm running 22.10. :-k

Reinstalling ubuntu-pro-client didn't help either.

EDIT: reinstalling [FONT=var(--ff-mono)]ubuntu-advantage-tools also doesn't fix it.[/FONT]

---

### Post by MAFoElffen on 2024-05-27
> **rjgoverna said:**
> Yep. It's all there, I'm running 22.04 LTS, aka Noble:

You can see I've successfully enrolled Pro. As per the screenshot, *esm-apps* and *esm-infra* are fine but *livepatch* seems to think I'm running 22.10. :-k

Reinstalling ubuntu-pro-client didn't help either.

EDIT: reinstalling [FONT=var(--ff-mono)]ubuntu-advantage-tools also doesn't fix it.[/FONT]
Well no. You said you went from Mantic, which is 23.10, to Noble, which is 24.04. That is where you enrolled into Ubuntu Pro. ( It had nothing to do with 22.04. )

I asked the Canonical Ubuntu Pro Team where to refer people for support for Ubuntu Pro, when I was testing it for Ubuntu Members. Below is the instructions.

Regardless... Go to [https://ubuntu.com/pricing/pro](https://ubuntu.com/pricing/pro)... In the lower right of that page is a contact dialog. It will say "Leave a Message", or "Chat"... When it says "Chat", talk with a person from their support team, and ask them. Explain it just like I did above, then tell them the errors you are getting.

---

### Post by rjgoverna on 2024-05-27
oh I see, typo on my second reply. Now amended. First post accurate.

 In short, on this machine: Jammy (22.04 LTS, first enrollment) > Mantic (23.10, unenrolled) > Noble (24.04 LTS, re-enrolled).
Not sure what's up with the "Ubuntu 22.10 is not supported" error. 

Cheers, I'll give that a shot.

---

### Post by MAFoElffen on 2024-05-27
I'm thinking the code is still wet on that. Updates for "Released Noble" just started rolling out recently. They are still working things out with Ubuntu Pro ESM as it relates to Noble. I wouldn't expect their to be much updates through Ubuntu Pro ESM yet... It's only less than a month since it's release. 

But LivePatch being broken for Noble... That is definitely a Bug that they need to be made aware of. They (there) all work for Canonical they can make things happen.

We here are just volunteers who are Users sharing our experience with other Users.

---

### Post by rjgoverna on 2024-05-27
Yep, I expect it all to be ironed out by the time 24.04.1 comes out. All in all the upgrade went smoothly and this is a very minor issue for my use case.

> **MAFoElffen said:**
> But LivePatch being broken for Noble... That is definitely a Bug that they need to be made aware of.

My thoughts exactly. The sort of feedback I expect will be useful to the folks at Canonical.

---

### Post by deadflowr on 2024-05-27
It's probably basing it on what kernel is running.
Look a what kernel version is current in use
```
uname -a
```

It's possible, albeit odd, to still have the 22.10 kernel installed and by some odder chance it being the kernel in use.
That kernel series for 22.10 was automatically installed to 22.04 as an upgraded HWE kernel.

---

### Post by rjgoverna on 2024-05-27
> **deadflowr said:**
> It's probably basing it on what kernel is running.
Look a what kernel version is current in use

Good point. Double checked, all looks normal.

[I]Linux E6420 **6.8.0-31-generic** #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
[/I]

---

### Post by rjgoverna on 2024-05-27
Good news, fixed it by reinstalling the livepatch snap.

*sudo snap remove --purge canonical-livepatch*
*sudo snap install canonical-livepatch*
*sudo pro enable livepatch*

It's now up and running.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293817&stc=1[/IMG]

Only niggle left to fix is the following error:

*Successfully processed your pro configuration.*
*Successfully refreshed your subscription.*
***/usr/lib/python3/dist-packages/uaclient/apt_news.py:160: Warning: W: Download is performed unsandboxed as root as file '/run/ubuntu-advantage//aptnews.json' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)***
***  acq.run()***
*Successfully updated Ubuntu Pro related APT and MOTD messages.*

---

### Post by rjgoverna on 2024-05-27
> **rjgoverna said:**
> Only niggle left to fix is the following error:

*Successfully processed your pro configuration.*
*Successfully refreshed your subscription.*
***/usr/lib/python3/dist-packages/uaclient/apt_news.py:160: Warning: W: Download is performed unsandboxed as root as file '/run/ubuntu-advantage//aptnews.json' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)***
***  acq.run()***
*Successfully updated Ubuntu Pro related APT and MOTD messages.*

Not a fix per se but made the error go away so I'm ok with it:

[I]sudo pro config set apt_news=false

[/I]Marking the thread as SOLVED. Cheers everyone.

---

