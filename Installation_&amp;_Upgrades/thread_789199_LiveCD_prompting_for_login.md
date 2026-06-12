---
title: "LiveCD prompting for login"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by CSquared on 2008-05-10
I've successfully installed several versions of Ubuntu, but this problem (which is on a special case) is stumping me.

Setup is:

I've taken the HDD out of my laptop (since the laptop's having some serious troubles) and put it in a 2.5" - 3.5" converter.  The system picks up on it without fault, I know this due to formatting the main partition with GParted.

However, when I try to run the LiveCD of Gibbon (I know, Heron's out - but I had the disc, and I didn't want to download another .iso), it prompts me to log in every time.  I even tried the OEM Install option, in case that would bypass it.

There is another HDD in the system, which is running Ubuntu.  The login details for that system have no effect on the LiveCD, but is it possible that's what's causing the problem?

Otherwise, are there default passwords for root, or any other username?  I just need to get an OS on the laptop's HDD, and I can't do it through the laptop itself.  Anyone have any idea what's going on?

---

### Post by Pumalite on 2008-05-10
It might be a bad burn. Have you already installed in another computer or drive with that CD?

---

### Post by CSquared on 2008-05-10
Not that particular one, no.  I couldn't find the one I used before, so I burnt it again.

I should try another disc, then?

---

### Post by Pumalite on 2008-05-10
Burn a new one. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on good quality CD-R, check CD integrity before install.

---

### Post by CSquared on 2008-05-10
Tried that, same problem.  What's confusing is that I know it can't be the .iso, I've used it before.  Any other ideas?  I'm totally lost here.

---

### Post by Pumalite on 2008-05-10
How did the md5sum come out?

---

