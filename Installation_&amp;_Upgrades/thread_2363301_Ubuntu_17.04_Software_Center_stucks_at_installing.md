---
title: "Ubuntu 17.04 Software Center stucks at installing"
date: 2017-06-08
forum: Installation &amp; Upgrades
---

### Post by docdoc2 on 2017-06-08
Hi ho, did a fresh installation on an empty partition of Ubuntu 17.04 and the software center doesn't really install much. Wine stops at 50%, chromium at 74%. When i click cancel, the cancel button just turns gray and the installation still keeps being stuck, Can't install anything else until i kill the process. The only thing i did with the new Ubuntu was to install some libraries and change from open java to oracle java.

---

### Post by LastDino on 2017-06-08
open terminal and try to install from there, then we will get idea as to what the actual error is

```

sudo apt install wine
```

Assuming wine is in official repositories, copy paste output here from command line

---

### Post by Autodave on 2017-06-08
The software center is an issue for most people on 17.04. I used *synaptic* long before the software center came into existence. Much easier.

sudo apt install synaptic

---

### Post by LastDino on 2017-06-08
+ 1 to Synaptic

Makes life much much easier. Also, terminal is quite handy (and gives that geeky feeling)

---

