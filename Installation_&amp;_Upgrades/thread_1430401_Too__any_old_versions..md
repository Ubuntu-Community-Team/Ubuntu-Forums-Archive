---
title: "Too  any old versions."
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by volatilepyro on 2010-03-15
Occasionally when I fire up my laptop the grub screen will appear with like eight safe and generic versions of grub. What is this all about, does it take up more memory, and how do I get it to just run with the latest version???

---

### Post by wojox on 2010-03-15
It doesn't take up more memory but does take up space on you drive. You could launch Computer Janitor and remove the old kernels.

---

### Post by oldfred on 2010-03-15
I have heard both pro and con on Computer Janitor as it is agressive on deleting things. If you have installed external software it may remove dependancies as they are not standard.

Be careful not to delete the kernel you are using. You can delete from the command line or from synaptic.

[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Removing kernels should automatically run an update to grub if not:
sudo update-grub.

---

### Post by slakkie on 2010-03-15
```

_rmkernel () {
        local cur_kernel=$1
        local kernel_pkg=$2
        local meta_pkg=$3
        sudo aptitude remove $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

rmkernel() {
    local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
    local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
    local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
    _rmkernel $cur_kernel $kernel_pkg $meta_pkg
    purge_pkg
}

```

You could use the following code to remove older kernels (it will remove all kernels, except the running version.

---

### Post by drs305 on 2010-03-15
For GUI, a good app is ubuntu-tweak. I would imagine Computer Janitor can do this as well but I had problems with it early after its release and haven't gone back to it.

Here is a link on the various ways to remove older kernels (see that section of the guide) as well as instructions on how to use ubuntu-tweak.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

