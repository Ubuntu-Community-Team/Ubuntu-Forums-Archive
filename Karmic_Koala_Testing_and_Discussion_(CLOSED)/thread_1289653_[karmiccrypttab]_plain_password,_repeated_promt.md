---
title: "[karmic/crypttab] plain password, repeated promt"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by getshoxed on 2009-10-12
Hi all,

I have a problem with my encrypted disks.

I installed a completely new ubuntu 9.10 beta server and updatet it (aptitude update / safe-upgrade), installed gdm, xorg and gnome-core and rebooted.

Also I edited the crypttab to encode my 2 crypted HDDs (and a crypted boot as set up by the server-installer)

data_crypt UUID=22....... luks,loud,noearly 
download_crypt UUID=33... luks,loud,noearly

Now when I reboot I get following behaviour:

Password-promt for System-HDD

*enter pwd*

Linux booting...

sda5_crypt (running)... [the System-HDD] 
data_crypt (starting) 
Enter passphrase to unlock......... (data_crypt): [promt]

*entering the _right_ password*

I press enter and the password gets appended in PLAN text to the :, followed by the same qeustion for the password again
...(data_crypt): *PASSWORT_IN_PLAIN*Enter passphrase......(data_crypt): [promt]

*entering password*

key slot 0 unlocked


Exactly the same happens with the second HDD,  1 plain output, 1 success

after unlocking the second HDD following appears:

key slot 0 ...

*download_crypt (started)...

Now the terminal stops, a promt is blinking 2 lines below.... for ever...  If I hit enter, it just continues as normal and starts up until login-prompt.

What could be wrong here? Didn't find anything with google that helped me :(

Another really annoying event is that GDM starts right when the first passowrd-promt is waiting. So I have to switch back to tty1 and enter the passphrases.
Can this be avoided?  First unlock all HDDs then continue boot?

I hope you can help me with this one. If any further information is needed, please tell me... but as mentioned above, it's a clean fresh install.

Thanks for reading
Markus


*** cross-posted here after no answer in 24h in the german forums  [[german thread]]("http://forum.ubuntuusers.de/topic/cryptsetup-crypttab-mehrere-abfragen-plain-pa/")

---

