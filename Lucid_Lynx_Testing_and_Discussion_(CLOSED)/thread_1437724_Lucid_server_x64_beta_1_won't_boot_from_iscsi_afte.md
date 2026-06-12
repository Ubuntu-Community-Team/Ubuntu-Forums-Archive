---
title: "Lucid server x64 beta 1 won't boot from iscsi after a succesfull install"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheR on 2010-03-24
I have already filed bug report but it doesn't hurt maybe somebody has got idea here:

I am trying to boot OS on a diskless server from iscsi (ubuntu 9.10 open-iscsi) server. 

Instalation of image went perfect. I was asked for target server and have installed OS on selected LUN.

I have Intel dual 10Gb 82598EB NIC and am trying a remote boot through Intel® iSCSI Remote Boot option.

Communication settings look OK (I get message that LUN of proper size was found on server) but after that screen is cleared an cursor blinks in the third (not first) line of screen. 

Karmic also doesn't work.


by
TheR

---

### Post by KB1JWQ on 2010-03-24
Interesting problem.  Unfortunately my iSCSI knowledge centers around RedHat, but....

Can you paste your grub configuration from the iSCSI LUN?

---

