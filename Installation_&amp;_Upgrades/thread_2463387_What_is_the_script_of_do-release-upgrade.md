---
title: "What is the script of do-release-upgrade"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by tomhsiung on 2021-06-10
Hello, everyone

Due to some reason, my do-release-upgrade process was interrupted and I was not able to execute the `[COLOR=var(--black-800)][FONT=var(--ff-mono)]Remove obsolete packages? [/FONT][/COLOR]` step.

So does anyone know the script of that step? Just want to remove the obsolete packages after upgrading. Thanks

Tom

PS: So far I had done this,

```
sudo -i

apt-get update
apt-get autoremove
apt-get clean
 
UNUSCONF=$(dpkg -l|grep "^rc" | awk '{print $2}')
apt-get remove --purge $UNUSCONF


NEWKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')


ADDKERNEL="linux-(image|headers|ubuntu-modules|restricted-modules)"


METAKERNEL="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"


UNUSKERNELS=$(dpkg -l | awk '{print $2}' | grep -E $ADDKERNEL | grep -vE $METAKERNEL | grep -v $NEWKERNEL)


apt-get remove --purge $UNUSKERNELS


update-grub
```

---

### Post by MAFoElffen on 2021-06-10
> **tomhsiung said:**
> Due to some reason, my do-release-upgrade process was interrupted...  Just want to remove the obsolete packages after upgrading. 
The first 5 lines of your "PS" code:
```

sudo -i


apt-get update
apt-get autoremove
apt-get clean

```
...should have removed "obsolete packages." if you think you have more there, you can generate a list of obsolete packages via:
```

apt-show-versions | grep 'No available version'

```
But saying that you had an interupted Apt process, you might also do:
```

sudo apt-get install -f

```
...to fix any broken packages caused by that interruption.

---

### Post by tomhsiung on 2021-06-11
Thank you, pal. Yes, I had upgraded successfully. And I just want to know the script of the do-release-upgrade program for removing the obsolete packages.

---

### Post by MAFoElffen on 2021-06-11
If that happens again, if you do:
```

dpkg configure -a 

```
...then it usually reconnects to the process of that where it let off, unless there are some packages to repair first.

---

