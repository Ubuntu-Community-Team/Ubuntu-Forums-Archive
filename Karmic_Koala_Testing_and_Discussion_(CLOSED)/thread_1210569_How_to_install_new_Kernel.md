---
title: "How to install new Kernel?"
date: 2009-07-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-07-11
I finally was able to obtain and install the Alpha 2 release for a fresh start. While upgrading I accidentally allowed the updated to bypass the new kernel leaving me with the old. How do I obtain and install the latest kernel?

---

### Post by budluva04 on 2009-07-11
run update manager again? or sudo apt-get update && sudo apt-get upgrade in a terminal

---

### Post by tjeremiah on 2009-07-11
> **budluva04 said:**
> run update manager again? or sudo apt-get update && sudo apt-get upgrade in a terminal

it isnt there.

---

### Post by Craigy90 on 2009-07-11
Well, to check if you have it installed, do

```
dpkg --list | grep linux-image

```

and look for the latest kernel (2.6.31-2). If you have it, and want to add grub2 entries, run

```
sudo update-grub2
```

---

### Post by tjeremiah on 2009-07-11
> **Craigy90 said:**
> Well, to check if you have it installed, do

```
dpkg --list | grep linux-image

```

and look for the latest kernel (2.6.31-2). If you have it, and want to add grub2 entries, run

```
sudo update-grub2
```
That seems to do it, it just wasnt appearing, thanks! :)

---

