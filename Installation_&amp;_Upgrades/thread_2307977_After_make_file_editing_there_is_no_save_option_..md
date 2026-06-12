---
title: "After make file editing there is no save option ."
date: 2015-12-30
forum: Installation &amp; Upgrades
---

### Post by latha2 on 2015-12-30
Dear all,
I have been trying to compiling the linux kernel 2.6.24 on ubuntu 14.04 in which i got an error like 
gcc: error: elf_x86_64: No such file or directory
gcc: error: unrecognized command line option ‘-m’
make[1]: *** [arch/x86/vdso/vdso.so.dbg] Error 1
make: *** [arch/x86/vdso] Error 2
so,I searched ubuntu ask community where I found 
obj-m += test.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules 
But after editing make file It's not showing any save option . 
Is there any other way to compile this linux 2.6.24 ??
Could you please help me out 
Thank you.

---

### Post by sudodus on 2015-12-30
I can't help you with details how to compile an old kernel in Ubuntu 14.04. But I might have an idea about the problem to save from the editor.

The permissions are set such that you have no write permission. Do you know about read, write, execute permissions in linux file systems?

The file that you edit must have write permissions for the user id, that you use, when you edit the file. You can see the permissions with the terminal window command

```
ls -l filename
```

where filename is the name of the file you want to view.

```
ls -l
```

will show the permissions of all files and subdirectories in the current directory.

You can change the permissions with ```
chmod
```. Sometimes you need ```
sudo chmod
``` if the standard user has no permission to change the permissions.

See this link for more details, or browse the internet to find a another good tutorial.

[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

