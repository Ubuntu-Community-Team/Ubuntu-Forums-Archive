---
title: "New Ubuntu version not shown in the update manager"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Arrgoss on 2010-05-30
I want to update to the Lucid Lynx version (I'm now running Jaunt Jackalope) but the update manager doesn't show me any new release.

In the Software Sources --> Updates --> Release Upgrades I have activated Show normal releases, and the funny thing is that a couple of days ago I did have the warning in the Update manager about the new release, but now that I have time to update it I don't know how to start it.

Any idea why the warning about the new release is not there anymore?

Thanks a lot.

---

### Post by davidmohammed on 2010-05-30
it its recommended that if you are not on a LTS i.e. 8.04, you need to upgrade through each next release - i.e. from 9.04 you need to upgrade to 9.10 before you upgrade to 10.04.

The alternative is just to wipe your installation and reinstall 10.04 from scratch.

---

### Post by Jakiejake on 2010-05-30
> **davidmohammed said:**
> it its recommended that if you are not on a LTS i.e. 8.04, you need to upgrade through each next release - i.e. from 9.04 you need to upgrade to 9.10 before you upgrade to 10.04.

The alternative is just to wipe your installation and reinstall 10.04 from scratch.

I recommend Wiping and starting again
It will be worth it
It takes around 30 mins to do a fresh install if not that!
:)

---

### Post by Arrgoss on 2010-05-30
I thought that upgrading from a version two steps away was supported by the update manager... Anyway, what's the best way then to upgrade step by step?

---

### Post by Arrgoss on 2010-05-30
> **Jakiejake said:**
> I recommend Wiping and starting again
It will be worth it
It takes around 30 mins to do a fresh install if not that!
:)

Uhm... I'm always afraid of wiping. Is it really so much advised?

---

### Post by Arrgoss on 2010-05-30
No hints on how to upgrade from 9.04 to 9.10? I'm blocked here...

---

### Post by Jakiejake on 2010-05-30
> **Arrgoss said:**
> Uhm... I'm always afraid of wiping. Is it really so much advised?

Well If you back-up everything it will be worth it!

---

### Post by Jakiejake on 2010-05-30
> **Arrgoss said:**
> Uhm... I'm always afraid of wiping. Is it really so much advised?

AND!!!
It will free up space and make your PC faster

---

### Post by Arrgoss on 2010-05-30
> **Jakiejake said:**
> AND!!!
It will free up space and make your PC faster

All advantages! :)
I will do that, but I need some time I don't have now to back up everything properly and don't screw up.
In the meantime I'll upgrade step by step, if someone can advise me on how to go from 9.04 to 9.10.

---

### Post by Jakiejake on 2010-05-30
> **Arrgoss said:**
> All advantages! :)
I will do that, but I need some time I don't have now to back up everything properly and don't screw up.
In the meantime I'll upgrade step by step, if someone can advise me on how to go from 9.04 to 9.10.

Didn't you want 10.04
If you are going to wait until you install 10.04 just stay on 9.04 it is not worth upgrading to 9.10 if you will then install 10.04
How to install 10.04:
Download GParted and burn to CD
Download Ubuntu 10.04 Lucid Lynx And Burn to CD
Wipe everything using the GParted Live CD (Google Is your friend ;))
Then install Ubuntu 10.04 using the Ubuntu 10.04 CD you burned earlier
Ta-Da
Enjoy! :)

---

### Post by wojox on 2010-05-30
> **Arrgoss said:**
> All advantages! :)
I will do that, but I need some time I don't have now to back up everything properly and don't screw up.
In the meantime I'll upgrade step by step, if someone can advise me on how to go from 9.04 to 9.10.

Try:

```
sudo apt-get update
```

```
gksudo update-manager -d
```

---

### Post by Arrgoss on 2010-05-30
> **Jakiejake said:**
> Didn't you want 10.04
If you are going to wait until you install 10.04 just stay on 9.04 it is not worth upgrading to 9.10 if you will then install 10.04
How to install 10.04:
Download GParted and burn to CD
Download Ubuntu 10.04 Lucid Lynx And Burn to CD
Wipe everything using the GParted Live CD (Google Is your friend ;))
Then install Ubuntu 10.04 using the Ubuntu 10.04 CD you burned earlier
Ta-Da
Enjoy! :)

Jakiejake, you're a stubborn one! But I'm stubborner :)
I totally agree that a new installation from the scratch might be beneficial for the performance of my computer, but--and there's always a but--you have to understand that some people prefer to do an upgrade and keep the configurations and changes that we've been doing along the months or years and want to stay away of the burden of finding them all, saving them and re-reconfigure them again.
This said I've upgraded from 9.04 to 9.10 and I'm going to move forward from 9.10 to 10.04. Still, my upgrade manager doesn't tells me that there's a new distribution (although I'm now running 9.10 and have checked to show all new distribution releases). That's not a big problem, I can always download the alternate 10.4 CD, but I'd like to know why is that. Any suggestion?

---

### Post by Arrgoss on 2010-05-30
> **wojox said:**
> Try:

```
sudo apt-get update
```

```
gksudo update-manager -d
```
Thanks wojox, that worked!
I'm somewhat embarrassed I couldn't find it out by myself.
Any idea why it needed to be done by the terminal?

---

### Post by ssam on 2010-05-30
> **wojox said:**
> Try:

```
sudo apt-get update
```

```
gksudo update-manager -d
```

not -d. you should -c. -d will show development versions, so you may antecedently install the pre-alpha 10.10.

from 'man update-manager'
```

       -c, --check-dist-upgrades
              Check if a new distribution release is available

       -d, --devel-release
              Check if upgrading to the latest devel release is possible

```

---

