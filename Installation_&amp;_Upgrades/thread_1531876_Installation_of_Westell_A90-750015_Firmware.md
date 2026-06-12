---
title: "Installation of Westell A90-750015 Firmware?"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by blue_flame on 2010-07-15
I've been having some trouble trying to compile source code to get a .upg file. That file is used to upgrade Westell Gateways.
I went to [http://www.westell.com/versalink-model-327/a90-750015-07-5.html](http://www.westell.com/versalink-model-327/a90-750015-07-5.html)
and downloaded the newest firware source code, as well as, some toolchains and the readme.

The readme states that it's only supported in Fedora Core Release 5.
[After untarring]
From what I understand the readme says to copy the contents of the toolchain into the /opt directory. Then it says to go into the SW directory. Then I'm supposed to use 'make PROFILE=A90-750015' as a command.
I tried compiling it in Ubuntu 9.04, and FC5 (in a virtual machine).

I compiled it in Ubuntu 9.04 first, but that didn't work.
Then I tried compiling it in FC5, but I recieved the same error messages. -_-

imo the source code should compile whether or not it's in FC5. (they were just stating it was compiled in FC5 before).

If you can compile this without error, please let me know what you did.

If I have the SW and toolchains folders in the current directory...
I used `cp -r toolchains /opt/toolchains` to copy the toolchains to the opt direcotry.
Then I used, `cd SW; sudo make PROFILE=A90-750015`

Here are the errors I'm receiving.
```

user@cName:~/Desktop/westell/SW$ sudo make PROFILE=A90-750015
[sudo] password for user: 
making all for A90-750015
make -C /home/user/Desktop/westell/SW/Westell/targets/A90-750015 all
make[1]: Entering directory `/home/user/Desktop/westell/SW/Westell/targets/A90-750015'
print[13]: =0: not found [No such file or directory]
print[14]: =/etc/mime.types: not found [No such file or directory]
print[15]: =/usr/share/etc/mime.types: not found [No such file or directory]
print[16]: =/usr/local/etc/mime.types: not found [No such file or directory]
print[17]: =$HOME/.kshrc{HOME}/.mime.types: not found [No such file or directory]
print[18]: =/usr/bin/x-terminal-emulator: not found [No such file or directory]
print[19]: =application/octet-stream: not found [No such file or directory]
print: line 19: syntax error at line 20: `(' unexpected
print[13]: =0: not found [No such file or directory]
print[14]: =/etc/mime.types: not found [No such file or directory]
print[15]: =/usr/share/etc/mime.types: not found [No such file or directory]
print[16]: =/usr/local/etc/mime.types: not found [No such file or directory]
print[17]: =$HOME/.kshrc{HOME}/.mime.types: not found [No such file or directory]
print[18]: =/usr/bin/x-terminal-emulator: not found [No such file or directory]
print[19]: =application/octet-stream: not found [No such file or directory]
print: line 19: syntax error at line 20: `(' unexpected
echo "A90-750015" > /home/user/Desktop/westell/SW/.PROFILE
print[13]: =0: not found [No such file or directory]
print[14]: =/etc/mime.types: not found [No such file or directory]
print[15]: =/usr/share/etc/mime.types: not found [No such file or directory]
print[16]: =/usr/local/etc/mime.types: not found [No such file or directory]
print[17]: =$HOME/.kshrc{HOME}/.mime.types: not found [No such file or directory]
print[18]: =/usr/bin/x-terminal-emulator: not found [No such file or directory]
print[19]: =application/octet-stream: not found [No such file or directory]
print: line 19: syntax error at line 20: `(' unexpected
print[13]: =0: not found [No such file or directory]
print[14]: =/etc/mime.types: not found [No such file or directory]
print[15]: =/usr/share/etc/mime.types: not found [No such file or directory]
print[16]: =/usr/local/etc/mime.types: not found [No such file or directory]
print[17]: =$HOME/.kshrc{HOME}/.mime.types: not found [No such file or directory]
print[18]: =/usr/bin/x-terminal-emulator: not found [No such file or directory]
print[19]: =application/octet-stream: not found [No such file or directory]
print: line 19: syntax error at line 20: `(' unexpected
print[13]: =0: not found [No such file or directory]
print[14]: =/etc/mime.types: not found [No such file or directory]
print[15]: =/usr/share/etc/mime.types: not found [No such file or directory]
print[16]: =/usr/local/etc/mime.types: not found [No such file or directory]
print[17]: =$HOME/.kshrc{HOME}/.mime.types: not found [No such file or directory]
print[18]: =/usr/bin/x-terminal-emulator: not found [No such file or directory]
print[19]: =application/octet-stream: not found [No such file or directory]
print: line 19: syntax error at line 20: `(' unexpected
print[13]: =0: not found [No such file or directory]
print[14]: =/etc/mime.types: not found [No such file or directory]
print[15]: =/usr/share/etc/mime.types: not found [No such file or directory]
print[16]: =/usr/local/etc/mime.types: not found [No such file or directory]
print[17]: =$HOME/.kshrc{HOME}/.mime.types: not found [No such file or directory]
print[18]: =/usr/bin/x-terminal-emulator: not found [No such file or directory]
print[19]: =application/octet-stream: not found [No such file or directory]
print: line 19: syntax error at line 20: `(' unexpected
***** Building Linux kernel *****
make -C /home/user/Desktop/westell/SW/Broadcom/kernel/linux O=/home/user/Desktop/westell/SW/Westell/targets/A90-750015/objects
make[2]: Entering directory `/home/user/Desktop/westell/SW/Broadcom/kernel/linux'
find . -lname "*" -name "bcm96358" -print -exec rm -f "{}" ";"
./broadcom/char/bcmprocfs/bcm96358
./broadcom/char/atmapi/bcm96358
./broadcom/char/adsl/bcm96358
./broadcom/net/usb/bcm96358
./broadcom/net/wl/bcm96358
./broadcom/net/enet/bcm96358
./broadcom/atm/bcm96358
./opensource/char/serial/bcm96358
./opensource/char/board/bcm963xx/bcm96358
/bin/bash -c " ln -sn impl1 opensource/char/board/bcm963xx/bcm96358; ln -sn impl1 opensource/char/serial/bcm96358; ln -sn impl1 broadcom/atm/bcm96358; ln -sn impl1 broadcom/char/atmapi/bcm96358; ln -sn impl1 broadcom/char/adsl/bcm96358; ln -sn impl1 broadcom/char/bcmprocfs/bcm96358; ln -sn impl2 broadcom/net/enet/bcm96358; ln -sn impl2 broadcom/net/usb/bcm96358; ln -sn impl2 broadcom/net/wl/bcm96358;"
  Using /home/user/Desktop/westell/SW/Broadcom/kernel/linux as source for kernel
  CHK     include/linux/version.h
  SYMLINK include/asm -> include/asm-mips
  CC      scripts/mod/empty.o
/bin/sh: mips-linux-gcc: not found
make[5]: *** [scripts/mod/empty.o] Error 127
make[4]: *** [scripts/mod] Error 2
make[3]: *** [scripts] Error 2
make[2]: *** [_all] Error 2
make[2]: Leaving directory `/home/user/Desktop/westell/SW/Broadcom/kernel/linux'
make[1]: *** [/home/user/Desktop/westell/SW/Westell/targets/A90-750015/objects/vmlinux] Error 2
make[1]: Leaving directory `/home/user/Desktop/westell/SW/Westell/targets/A90-750015'
make: *** [all] Error 2

```Does anyone know how I can fix this?

---

