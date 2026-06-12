---
title: "ARM tollchain support"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2009-12-15
Hello,
    I am trying to install ARM tollchain in my GCC. But i am not getting to install correctly. When i try to compile an u boot image i am getting the following errors in last few lines ..

```

make[1]: Leaving directory `/home/ariem/Desktop/u-boot-200901-lange51/tools'
make -C examples all
make[1]: execvp: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: Permission denied
make[1]: Entering directory `/home/ariem/Desktop/u-boot-200901-lange51/examples'
/bin/sh: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: is a directory
dirname: missing operand
Try `dirname --help' for more information.
/bin/sh: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: is a directory
dirname: missing operand
Try `dirname --help' for more information.
/home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc  -Os   -fno-strict-aliasing -fno-common -ffixed-r8 -msoft-float   -D__KERNEL__ -DTEXT_BASE=0x97800000 -I/home/ariem/Desktop/u-boot-200901-lange51/include -fno-builtin -ffreestanding -nostdinc -isystem  -pipe  -DCONFIG_ARM -D__ARM__   -Wall -Wstrict-prototypes  -c -o hello_world.o hello_world.c
make[1]: execvp: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: Permission denied
make[1]: *** [hello_world.o] Error 127
make[1]: Leaving directory `/home/ariem/Desktop/u-boot-200901-lange51/examples'
make: *** [examples] Error 2
ariem@ariem-desktop:~/Desktop/u-boot-200901-lange51$
```
what will be the error. can anyone tell me. i think the path exported is wrong. please help me

---

### Post by shariefbe on 2009-12-15
I think there might be a PATH error
i installed my compiler in /home/CodeSourcery/Sourcery_G++_Lite/bin

So shall i export the path as 
```
export PATH=$PATH:/home//CodeSourcery/Sourcery_G++_Lite/bin
```
or
```
export ARM_TOOLCHAIN=/home/ariem/CodeSourcery/Sourcery_G++_Lite/bin/
```
is it right? which is correct one?

Then what will come for 
```

export CROSS_COMPILE=
```
why it is needed?

---

### Post by 71GA on 2011-01-04
> **shariefbe said:**
> Hello,
    I am trying to install ARM tollchain in my GCC. But i am not getting to install correctly. When i try to compile an u boot image i am getting the following errors in last few lines ..

```

make[1]: Leaving directory `/home/ariem/Desktop/u-boot-200901-lange51/tools'
make -C examples all
make[1]: execvp: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: [COLOR=Red]Permission denied[/COLOR]
make[1]: Entering directory `/home/ariem/Desktop/u-boot-200901-lange51/examples'
/bin/sh: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: is a directory
dirname: missing operand
Try `dirname --help' for more information.
/bin/sh: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: is a directory
dirname: missing operand
Try `dirname --help' for more information.
/home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc  -Os   -fno-strict-aliasing -fno-common -ffixed-r8 -msoft-float   -D__KERNEL__ -DTEXT_BASE=0x97800000 -I/home/ariem/Desktop/u-boot-200901-lange51/include -fno-builtin -ffreestanding -nostdinc -isystem  -pipe  -DCONFIG_ARM -D__ARM__   -Wall -Wstrict-prototypes  -c -o hello_world.o hello_world.c
make[1]: execvp: /home/ariem/CodeSourcery/Sourcery_G++_Lite/lib/gcc: Permission denied
make[1]: *** [hello_world.o] Error 127
make[1]: Leaving directory `/home/ariem/Desktop/u-boot-200901-lange51/examples'
make: *** [examples] Error 2
ariem@ariem-desktop:~/Desktop/u-boot-200901-lange51$
```what will be the error. can anyone tell me. i think the path exported is wrong. please help me

The [COLOR=Red]red[/COLOR] text indicates you dont have a permission. You need to use sudo command to grant you superuser priviliges. 

I ve managed to set up **ARM** toolchain (Sourcery G++ Lite allso), but i have a problem compiling source files for **ARM[COLOR=Red]9[/COLOR]**.

---

### Post by 71GA on 2011-01-04
> **shariefbe said:**
> I think there might be a PATH error
i installed my compiler in /home/CodeSourcery/Sourcery_G++_Lite/bin

So shall i export the path as 
```
export PATH=$PATH:/home//CodeSourcery/Sourcery_G++_Lite/bin
```or
```
export ARM_TOOLCHAIN=/home/ariem/CodeSourcery/Sourcery_G++_Lite/bin/
```is it right? which is correct one?

Then what will come for 
```

export CROSS_COMPILE=
```why it is needed?


First of all check what locations are currently stored in ur PATH enviroment variable. Use command 
```
printenv
```
to check that. You will see that PATH aint empty. There are numerous locations stored there and are sepparated by "[COLOR=Blue]**:**[/COLOR]".

Make sure that when you use command
```
PATH=/home/codesourcery/lib[COLOR=Blue]**:**[/COLOR][COLOR=Red]"${PATH}"[/COLOR] 
```you specify blue and red code. You can read this command just like any program command. First you say that variable (PATH) is (=) path you want to add (/home/codesourcery/lib) then you add blue code to separate this path from other paths and 
then you specify variable (PATH) values that are currently saved there.

To make sure you added new directory sucessfully again use setenv command and look if your directory is one of the directories in PATH variable. If it is so then use 
comand 
```
export PATH
```

Hope it helps.

---

