---
title: "[SOLVED] upgrading from 6.06 to 7.04"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by shortybookit on 2007-09-01
i am new to ubuntu but i tried to download the 7.04 but i kept getting errors on my iso
so i downloaded the 6.06 version assuming you could upgrade after installing it the updata manager came up but i am still in 6.06 there was 153 updates

then i read  you can update from 6.10 to 7 with the update manager but after these updates i am still @ 6.06 so again how do i get to version 7? with out download an iso because the 5 mirrors i downloaded from all had errors thank you

new user

---

### Post by Pumalite on 2007-09-01
Have to go from 6.06 to 6.10, then you can go to 7.04

---

### Post by shortybookit on 2007-09-01
how do i get to 6.10 besides using the updata manager because according to that i am complelty updated

---

### Post by Pumalite on 2007-09-01
I think it is:
sudo apt-get dist-upgrade
But I'm not sure. Maybe someone here can confirm or correct this.

---

### Post by merlinus on 2007-09-01
This may work:

```

gksu "update-manager -c"

```

Pumalite's suggestion is also a good one, if this gives errors.

-merlin

---

### Post by shortybookit on 2007-09-02
worked now i am 6.10 same thing to get to 7?

---

### Post by merlinus on 2007-09-02
Should work....

-merlin

---

