---
title: "The action would require the installation of packages from not authenticated sources."
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2012-02-07
Hello everyone :)

I have just installed the ppa for the Wine.
I try to update my machine from the new ppa, but I get the error :

"The action would require the installation of packages from not authenticated sources."

I looked over the internet and I found that all I need to do is go to the update manager > Settings > Ubuntu Software and check the Source code checkbox.

It then asks me to [Authenticate] which I do, but then it DOES NOT check the check box.. So when I try to update it produces the same error.

Does anyone know if there is a way around it?
or a way to fix this?

Thank you all in advance.

---

### Post by RedSingularity on 2012-02-07
You can do an apt-get update to get around it for now.  Its a known issue. 

[Look Here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/707392")

---

### Post by Ifaistos on 2012-02-07
Thank you for your answer !!

I did an update as you say, and rerun the Update manager.
It is now in the process of downloading and installing...


Thank you :-)
Issue is solved...

---

### Post by RedSingularity on 2012-02-07
No problem.  You could also have run:

sudo apt-get update && sudo apt-get upgrade

---

