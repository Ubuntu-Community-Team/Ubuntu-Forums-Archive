---
title: "do-release-upgrade from 24.04 t o 24.10 erases third party source repositories"
date: 2024-10-13
forum: Installation &amp; Upgrades
---

### Post by stephen-liu on 2024-10-13
I just ran `do-release-upgrade` on a few Raspberry Pi Ubuntu Server installations and noticed afterwards that /etc/apt/sources.list.d/ only has ubuntu.sources.
Previous upgrades would retain the third party apt source repositories, commenting out the configuration so that the user can take appropriate action.
In this case, it seems like it just deleted the other source(s) altogether? 

The expected source in question is docker. Strangely, I still see the keyring file at /etc/apt/keyrings/docker.gpg

I have another Ubuntu desktop install where the sources don't seem to be removed, *except* for docker.

---

### Post by tuesdaybarrett on 2024-10-13
i went to software updater. I tried to update third party ppa and it wouldn't allow me to put in password to do that. Some help would nice. Thx

---

### Post by tuesdaybarrett on 2024-10-14
Problem seems to have resolved. Able to include ppa's.

---

