---
title: "What does this mean?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by LinXNut on 2011-07-27
Hi, I haven't used Linux in awhile, but I went to update and this showed up.

```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
jonathan@Xubuntu-Lap:~$ 
```In the top right of my screen, theres that little red icon that bothers me to update. However through the terminal it tells me the packages have been kept back? What do i do? 

Thanks,
LinXNut

---

### Post by Revolutionary101 on 2011-07-27
This is no big deal. For some reason I too have been unable to update those specific packages via terminal. I would suggest to just run Update Manager or update via Synaptic. That will update those packages for you.

Hope that helps!

---

### Post by LinXNut on 2011-07-28
Ok thank you...Just kind of odd. Aren't those packages in the same repo as Natty?

---

### Post by coffeecat on 2011-07-28
That can happen if you've installed another and later version of the kernel from a ppa repository. Apt-get is telling you about the latest release of the kernel that's in the main repo, but won't update it because you have a later one from elsewhere. For example, when kernel 2.6.38-8 was the current kernel in Natty, I installed 2.6.39-0 from a ppa, and apt-get wouldn't install 2.6.38-10 when it became available.

The answer is as Revolutionary101 describes or, if you want to use apt-get, use dist-upgrade instead of upgrade. Thus:

```
sudo apt-get dist-upgrade
```

Out of interest, do you have any 3rd party or ppa repositories enabled?

---

