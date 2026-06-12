---
title: "Change default e-mail client system wide"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by disasm on 2007-10-18
Hey all,

I have about 50 machines running ubuntu. I thought I had my setup script correct to change the default mail client system wide to thunderbird, but it isn't working.

This is the current command, I'm running as root
gconftool-2 --set /desktop/gnome/url-handlers/mailto/command --type="string" "mozilla-thunderbird %s"

Any ideas?

Sam

---

### Post by cornelis1 on 2007-10-18
try "thunderbird" instead of "mozilla-thunderbird"; I think they've changed the command

---

### Post by disasm on 2007-10-18
> **cornelis1 said:**
> try "thunderbird" instead of "mozilla-thunderbird"; I think they've changed the command

That's not it. I just did a which thunderbird on one of the machines, and no matches, both for feisty and edgy. It works fine if the individual user runs that command, but I can't seem to switch the default setting using that command.

Thankyou,

Sam

---

