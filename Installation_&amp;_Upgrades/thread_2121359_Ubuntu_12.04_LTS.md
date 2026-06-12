---
title: "Ubuntu 12.04 LTS"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by 2danny9 on 2013-03-01
Hi everyone,

I tried to install my own kernel, I was hoping it would not overwrite the kernel that was there but each time it does it (doing this on VM).

1) I download and extract kernel to /usr/src.
2) I then configure via make menufconfig
3) I then use: make -j # [COLOR=#414141][FONT=Arial]&&[/FONT][/COLOR] make[COLOR=#414141][FONT=Arial] [/FONT][/COLOR]modules_install [COLOR=#414141][FONT=Arial]&&[/FONT][/COLOR] make install
4) I think I (have and have not) run this: **mkinitrd -o initrd**
5) I then run the: sudo update-gurb 

Each time I;ve tried (4th time I think!) it replaces the kernel.

Is it possible to install the kernel along another kernel? 
I have a feeling it has something to do with: bzImage and preparing GRUB/.

I'm following a sort of guide thing that wan'ts to me compile a kernel and do my own system call. It doesn't however list how to do anything with the kernel other than naming options such as make install etc. 

Very sorry if this has already been posted, I've looked on google and I'm getting software based applications to do it and among other things.

A thank you for reading my thread,

Daniel

---

### Post by 2danny9 on 2013-03-03
Help Anyone?

Have I even posted in correct thread?

Thanks,

Dan

---

