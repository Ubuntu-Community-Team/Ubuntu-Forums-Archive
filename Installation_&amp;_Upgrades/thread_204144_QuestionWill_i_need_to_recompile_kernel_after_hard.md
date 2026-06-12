---
title: "Question:Will i need to recompile kernel after hardw. upgrade from pIII to Athlon XP?"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by kakulacis on 2006-06-26
In my opinion i should not need to recompile, and everything should work (32 bit system with same 386 architecture), but i'v tried same procedure some time (probably some years) ago on Warthy and i'v got kernel panic :) I actually do not remember reason for kernel panic and it was closely my first linux experience :) So now i'm a little bit confused, as i am lazy i would not upgrade system if i would need to recmpile kernel. Hope you got ir :)
sorry for my bad English!

---

### Post by David Corrales on 2006-10-28
Just install the K7 kernel if you're using Dapper or the generic one (should be already installed) if you're using Edgy.

---

### Post by dcstar on 2006-10-28
> **kakulacis said:**
> In my opinion i should not need to recompile, and everything should work (32 bit system with same 386 architecture), but i'v tried same procedure some time (probably some years) ago on Warthy and i'v got kernel panic :) I actually do not remember reason for kernel panic and it was closely my first linux experience :) So now i'm a little bit confused, as i am lazy i would not upgrade system if i would need to recmpile kernel. Hope you got ir :)
sorry for my bad English!

Changing motherboard hardware usually requires a fresh installation - lots of configuration set during the initial install will (most probably) no longer be valid for the new hardware.

---

### Post by AlReece45 on 2006-10-28
Last year, I replaced a Celeron 733Mhz and its motherboard with a new PIII and linux ran flawlessly. I had to reinstall windows though. This was with CentOS 4 though, not Ubuntu. Might be different.

---

### Post by David Corrales on 2006-10-29
> **dcstar said:**
> Changing motherboard hardware usually requires a fresh installation - lots of configuration set during the initial install will (most probably) no longer be valid for the new hardware.

This holds true for Windows but not Linux. Linux has tons of drivers and will just autodetect the changes.

---

