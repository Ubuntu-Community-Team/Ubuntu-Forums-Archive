---
title: "Beagle board Bootloader compilation"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2009-12-15
Hello, 

i saw all the steps for compiling in the beagleboard website. i am getting some errors while doing that steps. now i have to boot from mmc card. for that i installed tollchain fpr ARM processor in my host computer. AFter installing that toolchain i gave "make" to compile "xloader". But found the following error

"root@ariem-desktop:/home/xloader# make
arm-none-linux-gnueabi-gcc -Wa,-gstabs -D__ASSEMBLY__ -g  -Os   -fno-strict-aliasing  -fno-common -ffixed-r8  -D__KERNEL__ -DTEXT_BASE=0x40200800 -I/home/xloader/include -fno-builtin -ffreestanding -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -pipe  -DCONFIG_ARM -D__ARM__ -march=armv7-a  -c -o cpu/omap3/start.o /home/xloader/cpu/omap3/start.S
make: arm-none-linux-gnueabi-gcc: Command not found
make: *** [cpu/omap3/start.o] Error 127
root@ariem-desktop:/home/xloader# "

   i dont know what  is wrong

---

