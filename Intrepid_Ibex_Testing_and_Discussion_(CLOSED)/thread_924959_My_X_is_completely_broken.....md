---
title: "My X is completely broken...."
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2008-09-20
After applying the latest Xorg updates, I can no longer get X to work. My laptop gets past the loading screen and ends up with an underscore ( _ ) flashing until I turn it off by holding the power button. There's even no command line...

I can get into recovery mode and to a CLI, which will probably be the only  way to fix things. Trying the "Xfix" option (to fix xorg) doesn't work. "startx" at the command line gets the same result as above.

I did install fglrx for some reason, which could be the cause. I'll remove those packages now and see if that makes a difference.

---

### Post by Sslaxx on 2008-09-20
There's issues with the latest Nvidia drivers.

AMD's ATI drivers are, I think, not all that much better off either.

---

### Post by bpl07 on 2008-09-20
I have your same hardware and my system is still working after the updates.  I agree, you should completely purge fglrx then reinstall the open-source drivers.

---

### Post by lichtgestalt on 2008-09-20
I had the same problem.

Here's the error report + solution:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/fglrx-installer/+bug/247376](https://bugs.launchpad.net/ubuntu/intrepid/+source/fglrx-installer/+bug/247376)

---

### Post by Mazza558 on 2008-09-20
Removed fglrx and it's working again (with compiz too!?)

---

### Post by lichtgestalt on 2008-09-20
I was astound, too. Compiz didn't work before but does now.
Performance might not be as good as it could be with my card, but it's enough for me.

---

