---
title: "make AND make install throwing errors even when in root"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by CloudArchitect on 2010-05-13
I'm still a beginner in ubuntu. I've looked all over google but nobody has quite the same problem it seems, so I figured I would ask for some guidance here to make sense of it. I tried to make install gnuboy 0.9.13, and when I do sudo make install I get this huge mega error (I did do ./configure before I did make install). 

> 
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-mem -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c lcd.c -o lcd.o
cc1: error: unrecognised command line option "-fforce-mem"
make: *** [lcd.o] Error 1
Make throws the same error.

It looks like it's something to do with the GCC compiler not liking something. And the fact that gnuboy is on a beta version doesn't help either. But in theory it should install it. Is there anything I'm missing here? 

Peace and thanks in advance :guitar:

---

### Post by anglican on 2010-05-14
> **CloudArchitect said:**
> I'm still a beginner in ubuntu. I've looked all over google but nobody has quite the same problem it seems, so I figured I would ask for some guidance here to make sense of it. I tried to make install gnuboy 0.9.13, and when I do sudo make install I get this huge mega error (I did do ./configure before I did make install). 

Make throws the same error.

It looks like it's something to do with the GCC compiler not liking something. And the fact that gnuboy is on a beta version doesn't help either. But in theory it should install it. Is there anything I'm missing here? 

Peace and thanks in advance :guitar:
-fforce-mem was removed from gcc-4.3. Try editing the makefile(s) to remove this option... and submitting a bug report for gnuboy.

H

---

### Post by CloudArchitect on 2010-05-14
Heyy thanks a lot for the reply and the information there :)

Unfortunately removing -fforce-mem made this happen instead

> 
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c lcd.c -o lcd.o
lcd.c: In function ‘bg_scan’:
lcd.c:238: warning: incompatible implicit declaration of built-in function ‘memcpy’
lcd.c: In function ‘bg_scan_pri’:
lcd.c:301: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c:305: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c: In function ‘wnd_scan_pri’:
lcd.c:331: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c:337: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c:341: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c: In function ‘spr_scan’:
lcd.c:490: warning: incompatible implicit declaration of built-in function ‘memcpy’
lcd.c: In function ‘lcd_refreshline’:
lcd.c:603: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c:690: warning: incompatible implicit declaration of built-in function ‘memcpy’
lcd.c: In function ‘vram_dirty’:
lcd.c:800: warning: incompatible implicit declaration of built-in function ‘memset’
lcd.c: In function ‘lcd_reset’:
lcd.c:819: warning: incompatible implicit declaration of built-in function ‘memset’
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c refresh.c -o refresh.o
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c lcdc.c -o lcdc.o
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c palette.c -o palette.o
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c cpu.c -o cpu.o
gcc -O3 -DALLOW_UNALIGNED_IO  -fstrength-reduce -fthread-jumps  -fcse-follow-jumps -fcse-skip-blocks -frerun-cse-after-loop  -fschedule-insns -fschedule-insns2 -fexpensive-optimizations  -fforce-addr -fomit-frame-pointer -I. -I/usr/local/include  -I./sys/nix -DHAVE_CONFIG_H -DIS_LITTLE_ENDIAN -DUSE_ASM -I./asm/i386 -DIS_LINUX -c mem.c -o mem.o
mem.c: In function ‘ioreg_write’:
mem.c:232: error: label at end of compound statement
make: *** [mem.o] Error 1
:confused:

---

