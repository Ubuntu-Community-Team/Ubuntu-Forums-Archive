---
title: "New gdm/xsplash has disabled tty's?"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-08-11
with the new updates today i've lost all tty's. i'm thinking its related to the new xsplash work. just a warning. i thought the computer wasnt booting due to the blank black screen ( i tend not to use splash ) but actually its booting fine but the tty's are disabled somehow so theres no text flying by to reassure me :)

---

### Post by wayne_cat on 2009-08-11
hmm .. no problems with xsplash 0.3. I can still switch to tty0-tty6

```
root@macbook:~# apt-cache policy xsplash
xsplash:
  Installed: 0.3-0ubuntu1
  Candidate: 0.3-0ubuntu1
  Version table:
 *** 0.3-0ubuntu1 0
        100 /var/lib/dpkg/status
     0.2-0ubuntu1 0
        500 http://archive.ubuntu.com karmic/main Packages
root@macbook:~# 

```edit: forgot the gdm version

```
root@macbook:~# apt-cache policy gdm
gdm:
  Installed: 2.27.4-0ubuntu10
  Candidate: 2.27.4-0ubuntu10
  Version table:
 *** 2.27.4-0ubuntu10 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
root@macbook:~#
```

---

### Post by MacUntu on 2009-08-11
Everything's fine here too. Same versions as prairie_cat.

---

### Post by dinxter on 2009-08-11
hmm, i'll install a test on a spare partition tomorrow and check if i haven't bodged up something somewhere

---

### Post by dinxter on 2009-08-11
ah, no need, the grub installed to the mbr was muddled, i should have expected that one after the messing about ive done with it. i'm guessing it might have been easier to see the wood for the trees a little earlier in the day :) all fixed, thanks folks

---

### Post by Starks on 2009-08-11
xsplash is functional beyond that test image?

---

### Post by wayne_cat on 2009-08-11
> **Starks said:**
> xsplash is functional beyond that test image?

The "scale paper picture"? I can see it sometimes since I have updated to xsplash 0.3
But there a still some missing parts to make xsplash funtional.

---

### Post by curley_sue on 2009-08-19
> **dinxter said:**
> ah, no need, the grub installed to the mbr was muddled, i should have expected that one after the messing about ive done with it. i'm guessing it might have been easier to see the wood for the trees a little earlier in the day :) all fixed, thanks folks

I dont have the tty's (perhaps due to nvidia?)
could you please explain how did you fix that?

---

### Post by dinxter on 2009-08-19
> **curley_sue said:**
> I dont have the tty's (perhaps due to nvidia?)
could you please explain how did you fix that?
i had broken grub on the mbr so running grub-install /dev/sdX to install to mbr X or dpkg-reconfigure grub-pc and choosing the mbr's to install on fixed it.i doubt that'll be your problem though, more likely nvidia, i've got one of those and combining that with usplash has caused me a lot of bother on tty's

---

