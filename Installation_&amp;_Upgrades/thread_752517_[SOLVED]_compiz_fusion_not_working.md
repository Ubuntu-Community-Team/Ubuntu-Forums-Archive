---
title: "[SOLVED] compiz fusion not working"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by soumyajit pramanick on 2008-04-11
after installing the latest update compiz fusion was removed was removed from my system entirely, and i am missing it dearly.. will it return again in some later updates? or do i have to install it manually? if i have to install it manually then how? please help.:(

---

### Post by petzworld999 on 2008-04-11
You could do the following from a terminal:

```

sudo apt-get install compiz* xserver-xgl

```

This will install all the Compiz packages in the repositories, when you are done, you can type 
```

sudo apt-get remove compiz-kde 

```
to uninstall the KDE components.

---

### Post by soumyajit pramanick on 2008-04-11
i tried above and got this error

Note, selecting libgnome-compiz-manager0 for regex 'compiz*'
Note, selecting compiz-extra for regex 'compiz*'
Note, selecting libcompizconfig0 for regex 'compiz*'
Note, selecting ocaml-native-compilers for regex 'compiz*'
Note, selecting compiz-dev for regex 'compiz*'
Note, selecting lisp-compiler for regex 'compiz*'
Note, selecting compiz-gtk for regex 'compiz*'
Note, selecting compiz-kde for regex 'compiz*'
Note, selecting d-compiler for regex 'compiz*'
Note, selecting gdc-4.1 instead of d-compiler
Note, selecting libsnmp-mib-compiler-perl for regex 'compiz*'
Note, selecting compizconfig-backend-gconf for regex 'compiz*'
Note, selecting libcompizconfig-backend-gconf for regex 'compiz*'
Note, selecting c-compiler-avr for regex 'compiz*'
Note, selecting gcc-avr instead of c-compiler-avr
Note, selecting gcompizthemer for regex 'compiz*'
Note, selecting emerald instead of gcompizthemer
Note, selecting haskell-compiler for regex 'compiz*'
Note, selecting ghc6 instead of haskell-compiler
Note, selecting c-sharp-3.0-compiler for regex 'compiz*'
Note, selecting mono-gmcs instead of c-sharp-3.0-compiler
Note, selecting compiz-fusion-bcop for regex 'compiz*'
Note, selecting c-compiler for regex 'compiz*'
Note, selecting fortran-compiler for regex 'compiz*'
Note, selecting compiz-plugins for regex 'compiz*'
Note, selecting ocaml-compiler-libs-3.10.0 for regex 'compiz*'
Note, selecting ocaml-compiler-libs instead of ocaml-compiler-libs-3.10.0
Note, selecting libgnome-compiz-manager-dev for regex 'compiz*'
Note, selecting kicker-taskbar-compiz for regex 'compiz*'
Note, selecting c-sharp-2.0-compiler for regex 'compiz*'
Note, selecting mono-gmcs instead of c-sharp-2.0-compiler
Note, selecting compizconfig-settings-manager for regex 'compiz*'
Note, selecting python-compizconfig for regex 'compiz*'
Note, selecting ocaml-best-compilers for regex 'compiz*'
Note, selecting ocaml-native-compilers instead of ocaml-best-compilers
Note, selecting objc++-compiler for regex 'compiz*'
Note, selecting fortran95-compiler for regex 'compiz*'
Note, selecting pnet-compiler for regex 'compiz*'
Note, selecting c-sharp-compiler for regex 'compiz*'
Note, selecting objc-compiler for regex 'compiz*'
Note, selecting compiz-bcop for regex 'compiz*'
Note, selecting kicker-compiz for regex 'compiz*'
Note, selecting java-compiler for regex 'compiz*'
Note, selecting pascal-compiler for regex 'compiz*'
Note, selecting java2-compiler for regex 'compiz*'
Note, selecting libgnome-compiz-manager for regex 'compiz*'
Note, selecting c++-compiler for regex 'compiz*'
Note, selecting libcompizconfig0-dev for regex 'compiz*'
Note, selecting compizconfig-backend-kconfig for regex 'compiz*'
Note, selecting compiz-fusion-plugins-extra for regex 'compiz*'
Note, selecting fp-compiler for regex 'compiz*'
Note, selecting compiz-compcomm-plugins-main for regex 'compiz*'
Note, selecting compiz for regex 'compiz*'
Note, selecting libcompizconfig-backend-kconfig for regex 'compiz*'
Note, selecting ada-compiler for regex 'compiz*'
Note, selecting compiz-core for regex 'compiz*'
Note, selecting gnome-compiz-manager for regex 'compiz*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz*'
Note, selecting c-compiler-m68hc11 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc11
Note, selecting c-compiler-m68hc12 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc12
Note, selecting ocaml-compiler-libs for regex 'compiz*'
Note, selecting fortran77-compiler for regex 'compiz*'
Note, selecting compiz-gnome for regex 'compiz*'
Note, selecting libgnome-compiz-manager0-dev for regex 'compiz*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: compizconfig-backend-gconf (>= 0.7.4) but 0.7.2-0ubuntu1 is to be installed
E: Broken packages

now as i am pretty dumb at using linux (migrated from windows very recently) please help me out with a detailed procedure......:(

---

### Post by overdrank on 2008-04-11
> **soumyajit pramanick said:**
> after installing the latest update compiz fusion was removed was removed from my system entirely, and i am missing it dearly.. will it return again in some later updates? or do i have to install it manually? if i have to install it manually then how? please help.:(

HI and I assume you are using Hardy ?  What is the model of the graphics card?

---

### Post by soumyajit pramanick on 2008-04-11
by the way i am using the hardy heron beta release..

---

### Post by moneyd on 2008-04-11
greetings, i am having a similar problem (made an original post here [http://ubuntuforums.org/showthread.php?t=752536](http://ubuntuforums.org/showthread.php?t=752536))

some of the compiz packages upgraded to 0.7.4 but some are still at 0.7.2 and the 0.7.4's will not install as a result of incompatible dependencies, so im yet to figure out how to get compiz working on my gnome desktop since the upgrade.

any help is more than welcome, thank you

edit: nvidia video card, nvidia-glx-new 169.12+2.6.24-16.34 (hardy) installed

---

### Post by soumyajit pramanick on 2008-04-11
i  am using lenovo r60 laptop with integrated graphics...no separate graphics card...
but compiz was working fine...

---

### Post by moneyd on 2008-04-11
all compiz packages are now 0.7.4 in the repo, im installing now that should solve the issue

above confirmed

thanks to the repo managers for the quick upstream fix
cheers

---

### Post by soumyajit pramanick on 2008-04-11
> **moneyd said:**
> all compiz packages are now 0.7.4 in the repo, im installing now that should solve the issue

above confirmed

thanks to the repo managers for the quick upstream fix
cheers

please tell me elaborately how do i go about the installation...:confused:

---

### Post by soumyajit pramanick on 2008-04-11
can i install it using synaptic package manager?
if yes, then which packages should i install?

---

### Post by soumyajit pramanick on 2008-04-11
or please give me the codes that i can just copy and paste as i am pretty dumb at using linux.

---

