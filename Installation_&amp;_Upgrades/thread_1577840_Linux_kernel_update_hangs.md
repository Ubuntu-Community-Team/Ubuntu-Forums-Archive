---
title: "Linux kernel update hangs"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by LG_Auction on 2010-09-19
Yesterday the 10.04 update manager showed a kernel update. It downloaded and is hung at the unpacking statement. It's been there for hours.

What happens if I shut down?
What do I try next?

Thanks in advance.

---

### Post by LG_Auction on 2010-09-20
I tried Ctrl-C to end the update. Nothing happened.
I tried to shut down. Nothing happened.
I used the trusty hold the power button shut off and that worked.
Cold boot.
Update manager says that and update did not complete. "No kidding"
Continued the update.

The "thing" is stuck at unpacking the kernel AGAIN.

What would anyone suggest as the next try (I know a large hammer is what I would recommend. "If it jams, force it. If it breaks, you needed a new one anyway.")

---

### Post by llawwehttam on 2010-09-20
Try running the following:

```
sudo apt-get autoclean ; sudo apt-get autoremove ; sudo apt-get clean ; sudo apt-get update ; sudo apt-get upgrade

```

If it still hangs please post any errors that come up or post what the output is.

---

### Post by LG_Auction on 2010-09-20
Thank you!

The only error message was: 

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

After I ran that, I ran the apt-get commands that you provided and all was well.

Have a great day.

---

