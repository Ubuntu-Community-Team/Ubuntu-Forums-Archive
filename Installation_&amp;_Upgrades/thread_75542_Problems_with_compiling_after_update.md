---
title: "Problems with compiling after update"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by hav0x on 2005-10-13
So i did a clean install of breezy wanting a fresh start after the excelent experience that hoary was, but i cant seem to be able to compile my USB ADSL modem drivers.
I get this error:

[INDENT][FONT="Arial"]
(.....)
make[1]: Entrando no diretório `/usr/amedyn/module'
rm -f xdslusb_2.6.o
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/usr/amedyn/module XDSLUSB-MODULE=amedyn modules
make: *** **/lib/modules/2.6.12-9-386/build: Arquivo ou diretório nao encontrado.  Pare.**
make: Entrando em um diretório desconhecidomake: Saindo de um diretório desconhecidomake[1]: ** [normal] Erro 2
make[1]: Saindo do diretório `/usr/amedyn/module'
make: ** [AME_MODULE] Erro 2
hav0x@hellgate:/usr/amedyn$
[/FONT][/INDENT]

Translation, kind of:
***/lib/modules/2.6.12-9-386/build : file or directory not found. Stop.***

What am i missing here?
I installed everything it says it needs (namely libatm/dev libusb/dev rp-pppoe), i even installedd the linux-kernel-header i found on the cd. but no go :(
Does anyone have an idea what i might be missing?
It sux not being able to connect, linux offline is like a boat trying o rock climb.
help :confused: 
The whole thing is available here:
[http://phpfi.com/82307](http://phpfi.com/82307)
These are the drivers, also trying to get help there :(
[http://sourceforge.net/projects/zyxel630-11/](http://sourceforge.net/projects/zyxel630-11/)


thank you, 
hav0x

---

