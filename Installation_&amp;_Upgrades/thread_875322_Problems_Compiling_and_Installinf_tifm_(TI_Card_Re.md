---
title: "Problems Compiling and Installinf tifm (TI Card Reader)"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by matthanielcm on 2008-07-30
Hello everybody,

I kind of a noob so I was wondering if naybody could help me out.

I have a TI 5-in-1 card reader on my Toshiba Satellite A105-S4011 laptop but, I can't get it to work. 

None of this works:

> To test your card reader, open a terminal and type the following commands:

Code:

sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tifm_sd

Now insert a card and it should auto mount. If all went well and you see a Nautilus window with the contents of your card, you can make this permanent by editing the /etc/modules file:

Code:

sudo gedit /etc/modules

and add the following lines:

Code:

tifm_7xx1
tifm_core
tifm_sd

save and close the file (remember to leave a blank line after the last row).

Try this it should work.

So I'm currently trying to install the drivers manually by compiling and this is what I get:
> 
matthaniel@matthaniel-laptop:~/driver$ make
echo /home/matthaniel/driver
/home/matthaniel/driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/matthaniel/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/matthaniel/driver/tifm_sd.o
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_transfer_data’:
/home/matthaniel/driver/tifm_sd.c:194: error: ‘struct scatterlist’ has no member named ‘page’
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_bounce_block’:
/home/matthaniel/driver/tifm_sd.c:243: error: ‘struct scatterlist’ has no member named ‘page’
/home/matthaniel/driver/tifm_sd.c:250: error: ‘struct scatterlist’ has no member named ‘page’
/home/matthaniel/driver/tifm_sd.c:254: error: ‘struct scatterlist’ has no member named ‘page’
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_check_status’:
/home/matthaniel/driver/tifm_sd.c:407: error: ‘MMC_ERR_NONE’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c:407: error: (Each undeclared identifier is reported only once
/home/matthaniel/driver/tifm_sd.c:407: error: for each function it appears in.)
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_card_event’:
/home/matthaniel/driver/tifm_sd.c:507: error: ‘MMC_ERR_NONE’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c:524: error: ‘MMC_ERR_TIMEOUT’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c:526: error: ‘MMC_ERR_BADCRC’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_request’:
/home/matthaniel/driver/tifm_sd.c:726: error: ‘MMC_ERR_TIMEOUT’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_probe’:
/home/matthaniel/driver/tifm_sd.c:972: error: ‘MMC_VDD_32_33’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c:972: error: ‘MMC_VDD_33_34’ undeclared (first use in this function)
/home/matthaniel/driver/tifm_sd.c:982: error: ‘struct mmc_host’ has no member named ‘max_blk_count’
/home/matthaniel/driver/tifm_sd.c:983: error: ‘struct mmc_host’ has no member named ‘max_blk_count’
/home/matthaniel/driver/tifm_sd.c:985: error: ‘struct mmc_host’ has no member named ‘max_blk_size’
/home/matthaniel/driver/tifm_sd.c:986: error: ‘struct mmc_host’ has no member named ‘max_blk_count’
/home/matthaniel/driver/tifm_sd.c:986: error: ‘struct mmc_host’ has no member named ‘max_blk_size’
/home/matthaniel/driver/tifm_sd.c:987: error: ‘struct mmc_host’ has no member named ‘max_req_size’
/home/matthaniel/driver/tifm_sd.c: In function ‘tifm_sd_remove’:
/home/matthaniel/driver/tifm_sd.c:1021: error: ‘MMC_ERR_TIMEOUT’ undeclared (first use in this function)
make[2]: *** [/home/matthaniel/driver/tifm_sd.o] Error 1
make[1]: *** [_module_/home/matthaniel/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

I'm running Hardy 8.04 and my kernel is 2.6.24-19-generic. 

I've already installed build-essential and gcc 3.3, 3.4, 4.1, 4.2.

I've searched the internet looking for solutions and nothing has worked so far. Is there anything else that might fix it that i've not found yet.

Thanks everybody!

---

