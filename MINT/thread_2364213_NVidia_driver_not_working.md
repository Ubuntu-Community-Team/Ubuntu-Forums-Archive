---
title: "NVidia driver not working"
date: 2017-06-20
forum: MINT
---

### Post by Diskdoc on 2017-06-20
First off, I'm running Mint 18.1 (based on Ubuntu 16.04). I think it's legal asking about this here, because additional driver handling is the same I think. If I'm in the wrong forum today, I apologize and will be happy to write about this somewhere else.

Problem:

1) Choose NVidia driver, driver installs

2) Reboot

3) Still using Nouveau

Looking in X.org.log I see a line that says:

*Failed to load module "nvidia" (module does not exist, 0)*

I've tried doing

*sudo apt-get purge nvidia**

and trying to install the driver again but the problem remains.

Can anyone advise?

Screenshot: [https://drive.google.com/file/d/0B1A22hz9RUM-dzJ2empENGJCZnM/view?usp=sharing]("https://drive.google.com/file/d/0B1A22hz9RUM-dzJ2empENGJCZnM/view?usp=sharing")

---

### Post by howefield on 2017-06-20
Thread moved to the "*MINT*" forum.

---

### Post by Diskdoc on 2017-06-20
Thanks for putting the thread in the right place, I'll be sure to post here about questions for systems running Mint from now on.

Anyway, I found the problem. The solution was running:

*sudo update-alternatives --config x86_64-linux-gnu_gl_conf*

and selecting auto (0).

I needed to also do the aforementioned apt-get purge nvidia* before installing the 340-driver.

---

