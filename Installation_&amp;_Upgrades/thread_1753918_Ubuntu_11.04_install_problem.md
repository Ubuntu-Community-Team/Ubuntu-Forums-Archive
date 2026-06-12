---
title: "Ubuntu 11.04 install problem"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by lorddc on 2011-05-09
Hi, im having trouble installing ubuntu 11.4 on a mini-itx board, it keeps saying  "graphics intilization fail" i also tried with 10.10 and that says the same but i have no trouble booting a linux based off of an older ubuntu
any ideas?

thanks
PS: im using a ide to CF convertor with an 8GB CF card

---

### Post by sanderj on 2011-05-09
> **lorddc said:**
> Hi, im having trouble installing ubuntu 11.4 on a mini-itx board, it keeps saying  "graphics intilization fail" i also tried with 10.10 and that says the same but i have no trouble booting a linux based off of an older ubuntu
any ideas?

thanks
PS: im using a ide to CF convertor with an 8GB CF card

I would play with the boot options (press F6) and set the graphics resolution to VGA.

---

### Post by lorddc on 2011-05-09
nothing happens when i press F6, also there is currently no OS on the system

---

### Post by sanderj on 2011-05-09
> **lorddc said:**
> nothing happens when i press F6, also there is currently no OS on the system

You should boot from the Live-CD. See the boot options on [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions). Graphics is via F4.

---

### Post by lorddc on 2011-05-09
When i press escape all it does it stop the boot process and leave a flashing _ .

after typing help i get "This kernel requires the following features not present on the CPU: cx8 cmov"

---

### Post by sanderj on 2011-05-09
> **lorddc said:**
> When i press escape all it does it stop the boot process and leave a flashing _ .

after typing help i get "This kernel requires the following features not present on the CPU: cx8 cmov"

... and did you Google that message? Do you have a VIA C3 processor? If so, it looks like Ubuntu does not run on that CPU.

---

### Post by lorddc on 2011-05-09
It is a VIA C3 800mhz, googled it and looks like i cant use ubuntu, shame.

Thanks for the help anyway.

---

