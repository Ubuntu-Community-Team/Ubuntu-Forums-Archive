---
title: "when battery runs out while upgrading the system .... ?"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by milensinan on 2010-10-01
so, I was just upgrading to the new release of Ubuntu and didn`t notice that laptop was running on battery, then it was switched off.

Now I can open Ubuntu system, can`t reach to login page.
the other two systems are ok, XP and Pardus.

how do you think I can recover ubuntu?

thanks

---

### Post by sikander3786 on 2010-10-01
Select Recovery from Grub menu. Drop to root prompt and try

```

sudo dpkg --configure -a

```

You can also try to enable internet while in the root shell prompt and use apt-get install -f or apt-get update && apt-get upgrade.

[http://ubuntuforums.org/showthread.php?t=486409](http://ubuntuforums.org/showthread.php?t=486409)

---

### Post by milensinan on 2010-10-04
when doing recovery, trying to repair broken packages, it finishes and I continue to normal boot and it stalls on the screen saying:

Enabling Laptop Mode...  [OK]

-----------

when I enter to root and write:

sudo dpkg --configure -a

it just doesnt seem doing anything, coming back again my root name without any other thing, just 1 second after.

---------------

and I established internet connection through that link you gave, updated - upgraded and than said `continue to normal boot`, it stays again at that point.

-----------

is there maybe any other code that I can use to fix the whole system completely, with the advantage of internet connection on root?

thanks for the answer btw.

---

### Post by milensinan on 2010-10-10
I can login but nothing more, a very strange colored screen is there which is just flashing and changing colours. but I can`t use the system.

so what should I do to recover my system ?
or maybe uninstalling..

thanks

---

### Post by sikander3786 on 2010-10-10
> **milensinan said:**
> I can login but nothing more, a very strange colored screen is there which is just flashing and changing colours. but I can`t use the system.

so what should I do to recover my system ?
or maybe uninstalling..

thanks
I think it'll be better to save all your data to some external source like USB Drive or CD/DVD and then reinstall Ubuntu.

You can boot into a live CD and then mount your '/' or /home partition, whichever contains data and copy them to a safe location.

---

