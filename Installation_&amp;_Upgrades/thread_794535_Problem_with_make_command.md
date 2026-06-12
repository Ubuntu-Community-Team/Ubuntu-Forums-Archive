---
title: "Problem with make command"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by kurotenshi on 2008-05-14
i've been using Ubuntu for some time and never had this problem, but since i've reinstaled 7.10 i can't use the make command, it always does something like this:
(example installing madwifi)
```
carlos@carlos-laptop:~/Área de Trabalho/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/carlos/Área de Trabalho/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `de'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

```

Don't know if this is the only problem 'cause make clean seams to work but then....

```
carlos@carlos-laptop:~/Área de Trabalho/madwifi-0.9.4$ make install
sh scripts/find-madwifi-modules.sh 2.6.22-14-generic
make[1]: Entering directory `/home/carlos/Área de Trabalho/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/carlos/Área de Trabalho/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1

```

really need help 'cause i depend allot on wifi and i want to install other stuff

---

### Post by teaker1s on 2008-05-17
double check you have
```
sudo apt-get install build-essential
```
also 
```
sudo make install
```   needs root permission to install

---

