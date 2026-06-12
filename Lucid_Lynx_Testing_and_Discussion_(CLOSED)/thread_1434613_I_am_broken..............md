---
title: "I am broken............."
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by plun on 2010-03-20
```
E: I wasn't able to locate a file for the linux-headers-2.6.32-16 package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the linux-headers-2.6.32-16 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download

```

Cannot figure out howto fix this with aptitude or apt-get.....:^o

---

### Post by kansasnoob on 2010-03-20
I'd begin by using Synaptic to see if it recognizes any broken packages.

---

### Post by plun on 2010-03-20
> **kansasnoob said:**
> I'd begin by using Synaptic to see if it recognizes any broken packages.

I have done that but dpkg just freezes.....

(its OK on my laptop, was updating my desktop when this happended)

---

### Post by ronacc on 2010-03-20
have you checked /var/cache/apt/archives to see if the pkg is actually there ?

---

### Post by kansasnoob on 2010-03-20
> **plun said:**
> I have done that but dpkg just freezes.....

(its OK on my laptop, was updating my desktop when this happended)

Then I'd guess "sudo dpkg --configure -a" would show the same?

If so I'd try cleansing any partially or improperly installed .debs:

```
sudo apt-get clean
```

Then try to "update and dist-upgrade" again:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Beyond that it would probably be good to have a look at your sources.list:

```
cat /etc/apt/sources.list
```

Maybe also check for "free-space" issues:

```
df -H
```

```
sudo du -sh /*
```

---

### Post by ronacc on 2010-03-20
Just noticed something that may be related , I have updated twice today early AM and just now , several packages this morning many just now , my initrd regenerated and I rebooted ok ( using Nvidia 195.35.12 ) but synaptic shows NO HISTORY for today , yesterday and before show ok ???

---

### Post by plun on 2010-03-20
Thanks.....

sudo apt-get clean works.....   "up and running";)

---

### Post by kansasnoob on 2010-03-20
> **plun said:**
> Thanks.....

sudo apt-get clean works.....   "up and running";)

Awesome :D

---

