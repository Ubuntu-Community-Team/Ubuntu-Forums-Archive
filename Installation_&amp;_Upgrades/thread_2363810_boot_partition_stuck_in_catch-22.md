---
title: "/boot partition stuck in catch-22"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by bproffit on 2017-06-14
If I try to remove any old kernel, it fails because it reports unmet dependencies on that kernel. But if I try apt-get -f install to fix that I get an error that they can't be installed because the /boot partition is full. I don't know why old kernels can't just be purged whether there are unmet dependencies or not, but right now I'm stuck. Can anyone give me advice on how to break this impasse?

---

### Post by ian-weisser on 2017-06-14
There are hundreds of similar threads in this forum, so the advice is pretty well known.
In 16.04 and newer releases of Ubuntu, older kernels are automatically removed...unless you have (perhaps unknowingly) disabled that functionality.

Try to use apt autoremove to uninstall old kernel packages.
If that works, great.
If it fails due to out-of-space, then use dpkg to manually uninstall one old kernel package, then try autoremove again.

The 'unmet dependency' error is important. It could indicate one of several problems caused by the out-of-space condition.
Please copy-and-paste the complete error message so we can tell which problem you have.

---

### Post by sccman on 2017-06-15
Try ian-weisser's suggestion first.

If that doesn't work, open a terminal (Ctrl + Alt + t). What is the output of the commands:

```
df -h | grep /boot
```

And:

```
du -ah /boot | sort -n -r | head -n 10
```

---

