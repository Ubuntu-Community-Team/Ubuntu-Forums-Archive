---
title: "Intel C++ Compiler, installation failed"
date: 2006-05-20
forum: Installation &amp; Upgrades
---

### Post by peter_kk on 2006-05-20
Hi,

I was trying to install Intel C++ Compiler 9.0, but it displayes me Installation failed at the end...

I have login to root account, i have unpack tar file with icc, i have run ./install.sh

i have type 1, i have type 1 and i have type my license number.

Later i got this:

```

Checking RPM version ...

Checking Dependencies ...
Checking Kernel and glibc dependencies ...

install_cc.sh can't identify your machine type, glibc, or kernel.

This product is supported for use with the following combinations   :

    Machine Type                Kernel  glibc

1.  IA-32/EM64T                 2.4.x   2.2.5
    IA-32/EM64T                 2.4.x   2.2.4
    IA-32/EM64T                 2.4.x   2.2.93
    IA-32/EM64T                 2.4.x   2.3.2
    IA-32/EM64T                 2.6.x   2.3.x
    IA-32/EM64T                 2.6.x   2.4.x

x.  Exit

If you would you like to perform an unsupported install of this product, enter the number corresponding to the platform most similar to yours. Otherwise, enter "x" to exit   :    

```

I'm typing 1 to continue. Btw: My PC is 32bit Intel Centrino 1.6MHz and my operating system is the latest kubuntu beta 2, and uname -r = 2.6.15-23-386

After that i'm typing the Typical Install (i have try also Custom Install but this also don't work)

Later i'm asked for agree the license terms and conditions.

Later i'm choosing the installation paths (i'm choosing the defaults)

Instantly after that...

```

--------------------------------------------------------------------------------
Substitute Headers for Intel(R) C++ Compiler for 32-bit applications, Version 9.0
Installing...
Installation successful.
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
Intel(R) C++ Compiler for 32-bit applications, Version 9.0
Installing...
Installation failed.
--------------------------------------------------------------------------------


```

Btw:I don't see any log files in the unpacked folder.

Could anyone help me?

Greets&Thanks
Peter_K

---

### Post by Sef on 2006-05-20
Please don't double post. Thank you.

For the other thread, click on the link below.

[http://ubuntuforums.org/showthread.php?t=179589]("http://ubuntuforums.org/showthread.php?t=179589")

---

### Post by peter_kk on 2006-05-20
[QUOTE=Sef]Please don't double post. Thank you.[/QUOTE]

Not double but triple :mrgreen: 

But why nobody want to answer :(

---

