---
title: "upgrading 7.10 to 8.04 when /dev/sda3 = /home"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by notepad on 2008-05-16
im running ubuntu 7.10 on a dell inspiron 6400 laptop and thinking about upgrading to 8.04.

sda1 = winxp
sda2 = /
sda3 = /home
sda4 = swap

should i upgrade or do a fresh install given that /home (sda3) could theoretically remain untouched and save me the need to configure user accounts etc all over again?

---

### Post by notepad on 2008-05-17
bump

---

### Post by Kadaz on 2008-05-17
I'm in the same situation as you.
7.10 works nicely for me, considering of fresh install 8.04 but worry about my /home.
I won't upgrade it via apt-get dist-upgrade coz afraid of any failure and the bandwidth of OZ is not cheap..:???:

---

### Post by macaholic on 2008-05-17
> **notepad said:**
> im running ubuntu 7.10 on a dell inspiron 6400 laptop and thinking about upgrading to 8.04.

sda1 = winxp
sda2 = /
sda3 = /home
sda4 = swap

should i upgrade or do a fresh install given that /home (sda3) could theoretically remain untouched and save me the need to configure user accounts etc all over again?
It's ypur decision, you can do either theoretically. Doing a clean install is always a good thing, so I would suggest that.

---

### Post by notepad on 2008-05-17
> **Kadaz said:**
> I'm in the same situation as you.
7.10 works nicely for me, considering of fresh install 8.04 but worry about my /home.
I won't upgrade it via apt-get dist-upgrade coz afraid of any failure and the bandwidth of OZ is not cheap..:???:

ive downloaded the 8.04 iso from files.bigpond.com where it doesnt count towards my mortgage i mean data transfer allowance. a lot of isp's offer free mirroring of a few sites etc so consult your isp's site for tips.

as for keeping /home - ive not done it before so im waiting for somebody to offer some advice before i accidentally destroy my wifes gnome desktop etc.

---

### Post by zvacet on 2008-05-17
@ **notepad**

You can upgrade via net or from alternate CD.In both cases your home partition will be intact.But if you want to do fresh install you will do it by delete your root and install Hardy there.**Do not format home partition**.

---

### Post by coppertrail on 2008-05-17
> **notepad said:**
> im running ubuntu 7.10 on a dell inspiron 6400 laptop and thinking about upgrading to 8.04.

sda1 = winxp
sda2 = /
sda3 = /home
sda4 = swap

should i upgrade or do a fresh install given that /home (sda3) could theoretically remain untouched and save me the need to configure user accounts etc all over again?I have a very similar setup to yours (I'm dual booting on an Inspiron 6000).

Just did the upgrade through update manager, everything's fine.

---

### Post by notepad on 2008-05-18
i left my /home as it was (sda3) and did a new install on sda2.

DO NOT DO THIS.

i should have upgraded which apparently is a different iso to the livecd iso. i proceeded with a normal installation without formatting /home and it still asked me for my username, real name, password etc! then it looked at my ntfs partition and kindly asked if i wanted to import those users.

HELL NO! i wanted to import my /home ffs!

when i logged myself in though, it pretty much gave me all the settings on my gnome desktop etc that i had before. it didnt let me simply add the previous users because their /home directories already existed. perhaps i should have tried adding those users at install time? i dont remember if its even possible. i got through it by renaming users home directories and then adding the users, then changing the directory names all back again.

i should have downloaded the "alternate" iso and upgraded using that instead of starting again. now ive got to setup heaps of applications and plugins again and its going to take ages.

---

### Post by Kadaz on 2008-05-20
> **notepad said:**
> i left my /home as it was (sda3) and did a new install on sda2.

DO NOT DO THIS.

i should have upgraded which apparently is a different iso to the livecd iso. i proceeded with a normal installation without formatting /home and it still asked me for my username, real name, password etc! then it looked at my ntfs partition and kindly asked if i wanted to import those users.

HELL NO! i wanted to import my /home ffs!

when i logged myself in though, it pretty much gave me all the settings on my gnome desktop etc that i had before. it didnt let me simply add the previous users because their /home directories already existed. perhaps i should have tried adding those users at install time? i dont remember if its even possible. i got through it by renaming users home directories and then adding the users, then changing the directory names all back again.

i should have downloaded the "alternate" iso and upgraded using that instead of starting again. now ive got to setup heaps of applications and plugins again and its going to take ages.
well, i've upgraded to 8.04 successfully.
it doesn't allow to add any user account more during the installation.
i've no problem at all since it only got one user account in my /home, so i think i can't help you, sorry~

---

