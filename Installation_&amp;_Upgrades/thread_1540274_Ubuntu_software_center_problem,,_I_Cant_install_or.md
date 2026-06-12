---
title: "Ubuntu software center problem,, I Cant install or remove anything"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by DarkEnergy.0 on 2010-07-27
Whenever i try to install something or remove software it says that, "the previous installation didn't finish downloading and installing or was canceled in an unfriendly way. "You will have to fix this problem before installing or removing any software"

I already looked every where.

Does this have be fixed with terminal?
Is there someway to reinstall Ubuntu software center?

Please help.

I'm new to Ubuntu so go soft on me

---

### Post by AshRice on 2010-07-27
I'd hit up the terminal next. Try:

```
sudo apt-get update && sudo apt-get upgrade
```

if it still doesn't work, post the results here.

---

