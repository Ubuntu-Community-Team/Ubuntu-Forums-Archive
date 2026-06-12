---
title: "no windows xp in Grub"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by jj97403 on 2010-11-01
After I installed lubuntu Windows XP is not showing up as an option in GRUB (boot menu).  Only lubuntu and memory test.

Windows partition is there and untouched, because when I run G Parted I see it, and it is the same size as before, and still flagged as 'boot'

I tried running my XP-OS-CD in repair and the repair CD sees and identifies the Windows OS, and I can gain admin rights, but I don't know the commands (within CD) to repair the boot menu so windows XP is an option when booting up.

---

### Post by garvinrick4 on 2010-11-01
LOOK in post #4 please.
Boot into linux and run this in a terminal:
```
sudo update-grub
```Will probe for other installs and put them in grub menu at boot.

---

### Post by ubudog on 2010-11-01
> **garvinrick4 said:**
> Boot into linux and run this in a terminal:
```
sudo update-grub
```
Will probe for other installs and put them in grub menu at boot.

If that doesn't work, try this:
```
sudo update-grub2
```

Don't really know if there is any difference, but it may be worth trying.

---

### Post by garvinrick4 on 2010-11-01
Looked into Lubuntu and it has to have the os-prober installed first:

```
sudo apt-get install os-prober
``````
sudo update-grub
```

---

### Post by ubudog on 2010-11-01
> **garvinrick4 said:**
> Looked into Lubuntu and it has to have the os-prober installed first:

```
sudo apt-get install os-prober
``````
sudo update-grub
```

Ah, never used Lubuntu before.  Got to try it out I guess. :)

Any progress, OP?

---

### Post by jj97403 on 2010-11-01
Worked like a charm.  Had to do the os-prober command, but worked perfectly.  Thanks a million!!!!!!!

---

### Post by ubudog on 2010-11-01
Cool!

---

