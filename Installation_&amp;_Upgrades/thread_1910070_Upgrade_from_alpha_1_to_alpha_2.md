---
title: "Upgrade from alpha 1 to alpha 2"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by sonicsackboyver.25.04 on 2012-01-16
if i get the 12.04 alpha how can i upgrade from alpha 1 to alpha 2 when it comes out?

---

### Post by snowpine on 2012-01-16
You can use the Update manager, or if you prefer the Terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you stay current with updates then your system should seamlessly roll over to Alpha 2, Beta, RC, and Final. :)

---

### Post by sonicsackboyver.25.04 on 2012-01-16
thanks ill probably use the update manager cause im not good with the terminal but how can i upgrade my 11.10 system to 12.04 alpha 1

---

### Post by Mark Phelps on 2012-01-16
> **sonicsackboyver.25.04 said:**
> thanks ill probably use the update manager cause im not good with the terminal but how can i upgrade my 11.10 system to 12.04 alpha 1

Unless you want to spend your time debugging problems -- DON'T!

Alphas are very early versions, always buggy, and sometimes incomplete.  They are intended to be used only by experienced Ubuntu users, as they often fail and require considerable hand-fixing.

Also, there is no simple roll-back capability to Ubuntu.  So, if you upgrade to 12.04 and have problems, there is no simple way to get your currently working 11.10 version back.

---

### Post by IPEX-731BA5DD06 on 2012-01-16
If you really want to try it out, options are;

1) Install alongside 11.10 and dual boot into either system as you wish.

2) Use the live cd/ USB (capitals for better option) and play with it.

3) Install as a stand alone system, as per previous poster, ONLY if you are an experienced user. You like fixing bugs, editing your system to stop hangs, bugs, enjoy being frustrated.
(hey, I like to play about, but Alpha's don't play nice at all)

Note : No great groundbreaking alterations/additions. Its a LTS Copy, so they are just polishing up the release. 11.10 seems fairly much the same, but MUCH MORE STABLE.

---

