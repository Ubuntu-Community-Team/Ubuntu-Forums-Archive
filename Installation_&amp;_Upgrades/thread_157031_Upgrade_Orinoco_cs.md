---
title: "Upgrade Orinoco_cs"
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by mweston on 2006-04-08
OK guys, I've read through countless "How-to's" to fix this issue, but I think I must be missing something.

I'm trying to get my WPC11 v.3 to scan so that I can use airsnort or Kismet, or...any of the sniffers. So far, no good.

Installed linux-headers 2.6.12-10-386, linux-headers 2.6.12-10 and gcc-3.4, downloaded orinoco-0.15rc2. I switched to the directory where the driver was unpacked and typed "make":

make -C /usr/src/linux-headers-2.6.12-10-386 M=/home/matt/orinoco_driver/orinoco -0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.o
In file included from /home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:11 7:
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h: In function `hermes_present' :
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 o f `readw' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqm ask':
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 o f `writew' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h: In function `hermes_read_wor ds':
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 o f `readw' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h: In function `hermes_write_wo rds':
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 o f `writew' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h: In function `hermes_clear_wo rds':
/home/matt/orinoco_driver/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 o f `writew' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pc i_cor_reset':
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing ar g 2 of `writew' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing ar g 2 of `writew' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing ar g 1 of `readw' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing ar g 1 of `readw' makes pointer from integer without a cast
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pc i_suspend':
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arg uments to function `pci_save_state'
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pc i_resume':
/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arg uments to function `pci_restore_state'
make[2]: *** [/home/matt/orinoco_driver/orinoco-0.15rc2/orinoco_pci.o] [COLOR="Red"]Error 1[/COLOR]
make[1]: *** [_module_/home/matt/orinoco_driver/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] [COLOR="Red"]Error 2[/COLOR]

The warnings worry me, but the errors...I'm not sure what to do about them.
I tried makefile anyway, but Dmesg still shows:
 
[4294775.655000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au> , Pavel Roskin <proski@gnu.org>, et al)
[4294775.692000] orinoco_cs 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id. au>, Pavel Roskin <proski@gnu.org>, et al)


My computer is a Compaq Armada 7400 333mhz and the card is a linksys WPC11 v3 - which should be a viable candidate for this upgrade - I think. 

I'm hoping that I'm missing something simple.  Any ideas?

Tks,

---

