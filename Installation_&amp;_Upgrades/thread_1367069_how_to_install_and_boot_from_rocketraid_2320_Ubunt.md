---
title: "how to install and boot from rocketraid 2320 Ubuntu 9.10"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by genkindama on 2009-12-29
Hi everyone,

I'm desperately trying to install Ubuntu 9.10 server on a rocket raid 2320. I used Ubuntu 9.10 live cd to compile rr232x.ko for kernel 2.6.31-14, since on highpoint site there are no pre-compiled driver for the distro.
Now I managed to let Ubuntu see the controller in live cd environment and during installation of ubuntu server.
I can install ubuntu server on rr2320, but I can't make the server boot properly.
What is the correct procedure to make the server boot on rr2320?
Thank you in advance!

---

### Post by rudical on 2010-02-03
Hi,

Can you tell me how used the Ubuntu 9.10 live cd to compile rr232x.ko? I'm very new to linux and have no idea how to do this. If you could tell step by step I'd really appreciate it.

---

### Post by genkindama on 2010-02-04
[QUOTE=rudical;8770245]Hi,

Can you tell me how used the Ubuntu 9.10 live cd to compile rr232x.ko? [...]


well I booted the live cd and downloaded open sorce driver from highpoint site.
I followed Readme included and generated rr232x.ko
insmod rr232x.ko (to load the driver)
That's all.

Anyway, no one seemed to be able to solve my problem, so I had to use Centos 5.0. How I hate it.

---

### Post by slockton on 2010-02-17
> **rudical said:**
> Hi,

Can you tell me how used the Ubuntu 9.10 live cd to compile rr232x.ko? I'm very new to linux and have no idea how to do this. If you could tell step by step I'd really appreciate it.

Go here: [http://www.highpoint-tech.com/USA/bios_rr2320.htm](http://www.highpoint-tech.com/USA/bios_rr2320.htm)

Download the "Open Source driver". Unzip it by right clicking the downloaded file and selecting "Open with archive manager". From here you can uncompress the folder to wherever you choose.

Open up a Terminal window and cd to this folder. The README takes you through the next steps (following instructions for For Linux kernel 2.6), but here's what I did from this point:

cd product/rr232x/linux
sudo make
sudo make install

Then I rebooted and after gparted recognized my 7.28 TB raid 5 array. I'm formatting it as ext3 as I type.

Good luck.

S

---

### Post by genkindama on 2010-02-18
ok. I'm trying again. Now we all know how to create the correct driver for ubuntu from opensource highpoint driver.
How can I put this driver in the boot image so that I can boot from highpoint raid? Does anybody know? Really? Come on, I wanna get rid of that centos!

---

