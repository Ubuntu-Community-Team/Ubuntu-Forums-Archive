---
title: "Downgrading libstdc++6"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by karthik.V.M. on 2011-05-06
Hi All,

I use ubuntu lucid distribution. The libstdc++6 distributed in lucid is 4.4.3. But for some other work I installed libstdc++6 from natty whose version is 4.5.2. I did this by adding natty in the synaptic repositories. I would now want to go back to libstdc++6 4.4.3 but to do that the system says it needs to remove many packages of which essential packages are also a part. I cannot remove any essential package as the system may crash. Any idea on how to do that? :confused:

Thanks,
karthik

---

### Post by slooksterpsv on 2011-05-06
If you installed it via a adding a repository to Natty, just remove that repository and run:

sudo apt-get dist-upgrade

That should take it back to the current repository items, but if you have other natty stuff it'll remove those as well.

Otherwise how did you install it?

---

### Post by karthik.V.M. on 2011-05-06
Hi slooksterpsv,

Thanks for your quick answer. Also in the meantime, I actually downgraded the libstdc++6 with the following command.

sudo aptitude purge libstdc++6

It purged the libstdc++6 4.5.2 version(which is currently installed) and downgraded to the libstdc++6 4.4.3 version which is the default lucid version automatically. This tool is very intelligent. But synaptic complained a lot when I gave remove libstdc++6 that essential packages needs to be removed. Hope everything is fine now.

So does synaptic and aptitude are different tools?. I thought synaptic is a GUI version of aptitude.


Cheers :),
karthik.

---

### Post by slooksterpsv on 2011-05-06
To my understanding Synaptic and Aptitude are the same thing, ones a GUI and whats a CLI.
I could be wrong, but yeah.

---

