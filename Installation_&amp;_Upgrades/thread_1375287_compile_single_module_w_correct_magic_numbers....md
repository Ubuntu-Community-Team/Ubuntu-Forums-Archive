---
title: "compile single module w/ correct magic numbers..."
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by sfabel on 2010-01-07
Hello all,

I need a single module that is in the staging directory of the 2.6.32 tree. I've downloaded the 2.6.32 mainline packages from the kernel-team ppa from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/")

After I installed the linux-{image,header} packages, I found out that the staging modules had not been enabled. So I installed the source package, extracted the tar.bz2 file in a tmp directory and adjusted the config to include the single module that I needed from the staging directory.

Since I did not know how to compile/install a single module, I just did a naive "make modules" and then "sudo make modules_install". However, this created a different directory unter /lib/modules:
```

/lib/modules$ ls -l
total 12
drwxr-xr-x 5 root root 4096 2010-01-07 09:35 2.6.31-17-generic
drwxr-xr-x 3 root root 4096 2010-01-07 12:31 2.6.32
drwxr-xr-x 5 root root 4096 2010-01-07 09:50 2.6.32-02063203-generic
```

The "2.6.32-02063203-generic" is where the modules from the binary packages are stored, whereas my "make modules_install" created the "2.6.32" subdirectory. Also, the version numbers differ inside the modules themselves:
```

vermagic:       2.6.32 SMP mod_unload modversions 

```

vs.

```

vermagic:       2.6.32-02063203-generic SMP mod_unload modversions 

```

So, I suppose my question is: how do I proceed? Uninstall the binary packages, compile my own kernel? Use some magic command that changes the vermagic field in my compiled module?

Just looking for the easiest way without compromising system stability in terms of APT.

Thanks for any help,

Stephan

---

