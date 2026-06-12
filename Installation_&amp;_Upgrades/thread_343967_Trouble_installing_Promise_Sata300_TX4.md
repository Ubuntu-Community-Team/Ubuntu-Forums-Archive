---
title: "Trouble installing Promise Sata300 TX4"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by thefutoneng on 2007-01-22
I am a fairly new Linux user with this being my first attempt to install some new hardware.  I recently purchased the Promise Sata300 TX4 and two Seagate Barracudas to use are storage.  I was running Dapper when i first tried to install the card and the machine could not find it.  I did a fresh install of Edgy off of a live CD and it "found" the drives but I was not able to format them.

After I completed a fresh install of Edgy, I followed the Keebler's tutorial to install the Promise drivers.

[http://www.ubuntuforums.org/showthread.php?t=126199](http://www.ubuntuforums.org/showthread.php?t=126199)

I've downloaded everything i need and I get the following errors when I try running a "make bzImage" and also a "make install"

init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x533): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x81b): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0x941): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xbd7): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x4263): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x4f16): more undefined references to `__stack_chk_fail' follow
make: *** [.tmp_vmlinux1] Error 1


I got this card because I had read in several forums that it worked with Ubuntu out of the box.  Any help would be greatly appreciated.

---

### Post by thor918 on 2007-01-29
well for me it worked out of the box,
I'm running the server version of ubuntu.
only thing that dosen't work is the hotswap functionality....

if you run
lspci
you should see if the card is detected
this is what my readout got:
0000:02:0b.0 Mass storage controller: Promise Technology, Inc. PDC20718 (SATA 300 TX4) (rev 02)


by the way don't use edgy for stability...

---

