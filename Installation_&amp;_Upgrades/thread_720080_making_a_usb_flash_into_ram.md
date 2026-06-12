---
title: "making a usb flash into ram?"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by little cazy on 2008-03-09
I was wandering. If i can use flash flash drives as RAM. I want 2 put WoW:BC on and it sayz not enough ram (528mb, not enough). So, how? if possible.

---

### Post by prshah on 2008-03-10
> **little cazy said:**
> I was wandering. If i can use flash flash drives as RAM. I want 2 put WoW:BC on and it sayz not enough ram (528mb, not enough). So, how? if possible.

Nope, this cant be done in Ubuntu; what you are thinking of is Vista's ReadyBoost.

You can create a swap file on your USB flash drive, but it wont help you any, since the swap file is used only when your main system memory is full.

Normally, what free memory you have in your system is used by the cache; as and when programs need more memory, the cache is freed up.

If still more memory is required, dormant programs are moved to swap memory to free up more system memory for current running programs.

You can check your memory status by typing the command "free -m" in a Terminal.

Cheers,
PRShah

---

