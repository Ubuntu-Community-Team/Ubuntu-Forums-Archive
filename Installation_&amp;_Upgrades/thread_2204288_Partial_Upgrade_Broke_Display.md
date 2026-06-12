---
title: "Partial Upgrade Broke Display"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by NM5TF on 2014-02-07
while Ubuntu 12.04.4 was doing an upgrade the other day, my ISP decided to do some maintenance
on the DNS server....of course they failed to announce this in advance or I would have logged out...:(

when trying to boot up I now get an error complaining about my swap partition & and error on line 16
of /etc/fstab......AFAIK, fstab is only 13 lines long......something got corrupted it seems.....:confused:

it will get me to the CLI at least so I tried this...

```
sudo service lightdm start
```

this gave me a screen full of error messages, but the 1 that got my attention was something like
" no display found " or similar.....maybe the X server got corrupted ???

I have 2 other distros running just fine, Mint 16 & Trusty 14.04, but need to get 12.04 back to working correctly....](*,)

any thoughts as how to proceed ???

TIA,

tommy

---

### Post by Bashing-om on 2014-02-07
NM5TF; Hi !

Yeah, an interrupted update == bad news !

Try terminal codes :
```

sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
##All that does is update it again and do some in-house checks.

```

I do not know why, but double crossed fingers seems to help in a situation such as this.
Else: start looking at the dependencies, and what is yet to get installed and updated.

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by NM5TF on 2014-02-07
> **Bashing-om said:**
> NM5TF; Hi !

Yeah, an interrupted update == bad news !

Try terminal codes :
```

sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
##All that does is update it again and do some in-house checks.

```

I do not know why, but double crossed fingers seems to help in a situation such as this.
Else: start looking at the dependencies, and what is yet to get installed and updated.

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

thanx for reply om

have already tried update/upgrade....

will try dist-upgrade next....then -f install followed by  dpkg --configure -a

when looking at /var/log/Xorg.0.log I noticed a message stating that screens were found,
but were not in a usable configuration....I am assuming my Xorg.conf file got corrupted...

I also just noticed that when booting up it will flash the Ubuntu 12.04 purple screen for
just an instant before dropping to the black log-in screen.....

---

### Post by NM5TF on 2014-02-07
a little more information...

after running above commands I managed to get a little further along....although the desktop
is still not working....

when running start lightdm now it gets further than before....it now hangs at "load fallback
graphics device"....this is also verified in /var/log/Xorg.0.log......it states "nvidia kernel
failed to initialize".....

it appears that the nvidia driver is either corrupted or missing....

I also noticed that the nvidia 304 driver was listed as "held back" when doing
upgrade.....maybe this is a clue ???

tommy

---

### Post by Bashing-om on 2014-02-07
NM5TF; Yeah,

Proprietary drivers are always problematic in an upgrade situation.

Might try booting with the "nomodeset" boot parameter option, maybe then will boot to the GUI ? That will point us in a direction to look. 
Have you tried purging the driver and (re-)installing ?
Presently I do not think we can point fingers at the operating system. But ?
What is your level of experience ? As in, any guidance required for the above ?

If not one thing
[INDENT][INDENT]we can do something else
[/INDENT][/INDENT]

---

### Post by NM5TF on 2014-02-07
> **Bashing-om said:**
> NM5TF; Yeah,

Proprietary drivers are always problematic in an upgrade situation.

Might try booting with the "nomodeset" boot parameter option, maybe then will boot to the GUI ? That will point us in a direction to look. 
Have you tried purging the driver and (re-)installing ?
Presently I do not think we can point fingers at the operating system. But ?
What is your level of experience ? As in, any guidance required for the above ?

If not one thing
[INDENT][INDENT]we can do something else
[/INDENT][/INDENT]

will try nomodeset boot option again....tried it earlier with no results...will try it with VT=7
option turned off to see any error messages....

will definitely try purge & reinstall of drivers....think that is most likely cause of problems....

level of *nix experience is not quite noob, but not a software guru either.....was hardware guy
for 46+ years....been running Ubuntu since Fall of 2008.....been around computers since
1960's as a user mostly....

thanx for the tips.....will try them & get back

tommy

---

### Post by NM5TF on 2014-02-07
it's now FIXED :D

as suspected the nvidia drivers were corrupted....purge/reinstall fixed it....:popcorn:

the fix was as follows for anyone else that has this problem....

```

sudo apt-get purge nvidia-*
sudo dkms status
sudo apt-get install nvidia-current-updates nvidia-settings-updates

```

reboot & should work now....\\:D/

thanx for help Bashing-om :guitar:

---

### Post by Bashing-om on 2014-02-07
NM5TF: Hey great !

Sometimes another mind to bounce things off of is all that is needed.

Hope to see more of you ( we can use all the help here we can get ) .

[INDENT][INDENT]Happy trails to you
[/INDENT][/INDENT]

---

### Post by NM5TF on 2014-02-07
> **Bashing-om said:**
> NM5TF: Hey great !

Sometimes another mind to bounce things off of is all that is needed.

Hope to see more of you ( we can use all the help here we can get ) .

[INDENT][INDENT]Happy trails to you
[/INDENT][/INDENT]

I agree it's always helpful to have someone else to work with...

The Ubuntu Forums are the BEST LINUX RESOURCE AVAILABLE.....unfortunately, can't say
the same for the Mint Forums....you're pretty much on your own over there...good thing
it's derived from Ubuntu as I can always find answers here...

tommy

---

