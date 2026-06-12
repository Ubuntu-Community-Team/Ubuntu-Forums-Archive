---
title: "live cd problem"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by nkd on 2008-01-29
hi all,
I tried out the fiesty fawn live cd. It worked one on all computers, till I tried it out on a server HP 6200. It asks for the username and password and also prompts that by default it will login to ubuntu in 10 secs, but if i let it timeout it fails and returns me to the login prompt again.
I am confused. MD5 check sum shouldnot be the issue as it runs alright without asking me for any login info on all other machines. Isn't it ?!?

:confused: Plz help me out.
thanks 
nishith

---

### Post by Pumalite on 2008-01-29
Wipe your hard drive clean. Then install Ubuntu. You could use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn it to disk, boot from it. Delete everything in your hard drive, then make ona large partition of your hard drive, formatted ext3 if you want. Then install Ubuntu.

---

### Post by nkd on 2008-01-29
hi and thanks for your reply.
But I can't wipe the hdd clean , I wish to make it a dual boot system as there are other users on the system.
That should not be a issue as on the other machines , ubuntu live cd boots up without any issues even if the hdd has winXP and other data.
thanks 
nishith

---

### Post by Pumalite on 2008-01-30
Then make sure the partition you are installing to is formatted; not 'unallocated space'

---

### Post by nkd on 2008-01-30
hi,
sorry I think I need to clarify one thing....
I am having problems with getting the live cd startup ... after I choose the first option i.e, start or install ubuntu.
It normally gives me a desktop on all other machines , but on this server hp 6200 it brings up a login screen and no matter what I do I can't login.

thanks 
nishith

---

### Post by Pumalite on 2008-01-31
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

