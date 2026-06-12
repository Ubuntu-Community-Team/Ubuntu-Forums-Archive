---
title: "Synaptic Package Manager: An error occured"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by silverfish1978 on 2010-04-06
An error message appeared when starting Synaptic Package Manager:
An error occurred
The following details are provided:
E: Type '--2010-04-01' is not known on line 1 in source list /etc/apt/sources.list.d/qutim.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 
I tryed to remove Qutim in the root directory by command:
aptitude remove qutim

But it failed:
E: Type '--2010-04-01' is not known on line 1 in source list /etc/apt/sources.list.d/qutim.list
E: Type '--2010-04-01' is not known on line 1 in source list /etc/apt/sources.list.d/qutim.list
E: The list of sources could not be read.
E: Type '--2010-04-01' is not known on line 1 in source list /etc/apt/sources.list.d/qutim.list
E: The list of sources could not be read.

Can anybody help me out in this? I want to remove qitum.

Thanks, Villy

---

### Post by phillw on 2010-04-06
Hi Villy,

I'm going to have to use a sudo rm for a proposed answer, so please do check the spellings.

To copy direct from the code tables below, triple click on the command, then use CTRL+C to copy it to your clipboard. Then use SHIFT+CTRL+V to paste it into the Terminal.

```

cd /etc/apt/sources.list.d
ls qutim*

```

You should see reported back ```
qutim.list
``` and possibly also ```
qutim.list.save
```

Assuming that is what you see, issue ```
sudo rm qutim*
```

If you do not see the listing from the ls command, please do NOT issue the sudo rm command. The sudo command will require you enter your password.

Regards,

Phill.

---

### Post by silverfish1978 on 2010-04-07
:guitar:  THanks a lot,dear Phill! It works now:)

Villy

---

