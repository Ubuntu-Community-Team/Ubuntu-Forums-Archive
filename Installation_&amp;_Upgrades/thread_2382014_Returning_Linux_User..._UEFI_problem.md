---
title: "Returning Linux User... UEFI problem?"
date: 2018-01-08
forum: Installation &amp; Upgrades
---

### Post by capitanpingaloca on 2018-01-08
Greetings!

So I've been looking for some answers for an hour and I can't find anything specifically clear.

Like myself, there might be people who once had Linux and stopped using it for years. This might be of use for them...
In my case, my laptop was getting old, was using it less and less, was instead using my wife's Windows pc more, and speaking of wife, yeah, I got married, and got distracted for a while. That and work. Just threw me off the Linux paradigm.

When I installed Linux in my laptop I wiped the hard drive clean using DBAN. Installed Mandriva, then a year after that was Ubuntu, and used these distros for at least three years with no major problems. I want to know how much things have changed regarding installation.

Right before my hiatus, I actually wanted to turn my wife's pc into a Linux machine, but the issue at that moment was that UEFI was making it hard or impossible to install Linux distros in new machines... I can't remember exactly.
That issue prevented from carrying on, and I got used to Windows.

The questions:

Does this issue still persist?
Was it resolved?

DBAN still liable? Something better?

Should I just get a hard drive wiping software(recommendations?) and carry on with the install?

FYI I'm about to buy a laptop, possibly has Windows 10 on it.
The plan is to wipe everything clean and install Ubuntu.

Thanks

---

### Post by oldfred on 2018-01-08
If not a knowledgeable Linux user, I still suggest dual booting. And at least do a full backup of Windows.
We get many requests on how to reinstall Windows as users must have one game or application that only runs in Windows.
One user, who must regular get a new system, buys a good system, but with HDD. Then removes that HDD and puts in SSD and Ubuntu. Then later sells system with HDD &  "brand" new unused Windows.

UEFI is a bit more complicated as it also supports the now 35 year old BIOS with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I used to have to change a couple of settings in BIOS, now many systems need multiple settings changed in UEFI.
Some brands (HP, Sony & others) also do not fully support UEFI. UEFI spec says not to use Description as part of boot. And of course only valid description is "Windows Boot Manager". We now have many work arounds.
Some others (Acer) have unique extra settings in UEFI to enable Ubuntu entry.
Some just work and users have no issues.

Lots of UEFI install info in link in my signature.

---

