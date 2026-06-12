---
title: "Updating Karmic"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Duskao on 2009-08-13
This is just a quickie. With 9.10 will it be necessary to manually choose to update your system, or will it pop up automatically like with 9.04?

---

### Post by infamousrev on 2009-08-13
At my box I need to do a manual sudo aptitude update && sudo aptitude full-upgrade

But I guess it depends on what services you have running

---

### Post by taavikko on 2009-08-13
> **Duskao said:**
> This is just a quickie. With 9.10 will it be necessary to manually choose to update your system, or will it pop up automatically like with 9.04?

If you have set in synaptic that check for new releases, then it will propt you after release.

check that
```
taavikko@hp-dv5:~$ cat /etc/update-manager/
meta-release        release-upgrades    release-upgrades.d/ 
taavikko@hp-dv5:~$ cat /etc/update-manager/release-upgrades
# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=normal
```

the "Prompt=normal" is set


EDIT// misread the question. but for people who wants to upgrade 9.04 -> 9.10

---

### Post by GeorgeVita on 2009-08-13
> **Duskao said:**
> This is just a quickie. With 9.10 will it be necessary to manually choose to update your system, or will it pop up automatically like with 9.04?

Hi **Duskao**,
as now we are running the 'development phase' some default settings are floating. I believe that in final release this will be 'popped' automatically as it is more convenient for the average user.
For the testing period, I personally use all 'Pre-released updates' (Software Sources) and/or the later kernel (daily-build). Some times additionally the 3rd party PPAs (network manager). It depends on the tests I like to do.

Regards,
George

---

### Post by slakkie on 2009-08-13
I currently use this, since I got fed up with having to repeat myself so often:

```

rmpkg() {
    sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
    sudo aptitude clean
}

uppkg() {
    sudo aptitude update && sudo aptitude safe-upgrade
    rmpkg
}

```

---

### Post by Jesus_Valdez on 2009-08-13
since this is already open...

 Will GRUB2 be automatic update, or You'll have to do it manually? 

Thanks.

---

### Post by malachi1990 on 2009-08-14
You will have to update GRUB manually, if you do an OS upgrade.  If you are doing a clean install, GRUB2 is installed by defualt.

I believe that the reason given was the danger to your setup by upgrading the bootloader.

---

