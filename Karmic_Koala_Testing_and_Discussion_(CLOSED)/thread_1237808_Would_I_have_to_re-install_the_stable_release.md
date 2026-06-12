---
title: "Would I have to re-install the stable release"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Assim on 2009-08-11
After the stable release of Karmic Koala which will be available in October, would I have to re-install the stable version or the system will automatically update from the testing to stable version of Karmic Koala?

---

### Post by afv on 2009-08-11
If you keep updating you'll have the stable release.

---

### Post by Assim on 2009-08-12
> **afv said:**
> If you keep updating you'll have the stable release.
And that is from the Update Manager, right? :confused:

---

### Post by bacardiandwatermelon on 2009-08-12
Yes.. Update manager will give you updates... :-)

---

### Post by Martje_001 on 2009-08-12
I would still reinstall though. You have been running unstable software for months by then, God knows what it did ;-).

---

### Post by Assim on 2009-08-12
Thanks everywhere for the information. :)

---

### Post by Sand &amp; Mercury on 2009-08-12
> **Martje_001 said:**
> I would still reinstall though. You have been running unstable software for months by then, God knows what it did ;-).
Yup... even if you're running the versions of the software included that are considered stable, your system may well be still funky from changes caused by previous updates and software. Happened to me last development cycle and affected me in a big way.

---

### Post by Assim on 2009-08-12
Great, I'll make sure to download the new ISO and re-install after the stable release. :)

Thanks. ;)

---

### Post by taavikko on 2009-08-12
> **Assim said:**
> Great, I'll make sure to download the new ISO and re-install after the stable release. :)

Thanks. ;)

Really no need...

It's good thing to learn how to cleanup system so reinstallations can be avoided.

---

### Post by Assim on 2009-08-12
> **taavikko said:**
> Really no need...

It's good thing to learn how to cleanup system so reinstallations can be avoided.
When I installed it, it said something like that it's a pre-release version, so maybe the installation of the unstable version would be done differently or it's fine? :confused:

---

### Post by taavikko on 2009-08-12
> **Assim said:**
> When I installed it, it said something like that it's a pre-release version, so maybe the installation of the unstable version would be done differently or it's fine? :confused:

Yes. just keep it updated via update-manager / apt and it will become the official release of 9.10

---

### Post by Assim on 2009-08-12
Will do. Thanks. ;)

---

### Post by andrewabc on 2009-08-12
If you installed during alphas, and update to final, then I'd recommend formatting and installing fresh final version.

If you install beta or RC you might be fine to upgrade. With updating alphas there can be leftover data and I know I had a dozen kernels installed taking up a couple gb of space, which I had to remove from synaptic after every kernel update.

If you have no problem installing final version I'd do that. Or you can update, but I'd make sure to have final version downloaded and burnt to cd in case something were to go wrong with your install.

Can't go wrong with fresh install :)

---

### Post by taavikko on 2009-08-12
cleaning cruft packages
```
sudo aptitude purge `dpkg -l |grep "^rc" | awk '{print $2}'`
```

Removing obsolete packages,
```
sudo aptitude purge `aptitude search "~o" | awk {print $2}'`
```
this removes locally installed .deb and libdvdcss2 too, so careful

Cleaning ~/ just rm .fies&folders/ 
with exceptions.

Whoa, no need to reinstall....

---

### Post by Assim on 2009-08-12
Awesome. Thanks. ;)

---

