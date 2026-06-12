---
title: "Help on speeding up kernel compile"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by NuNn DaDdY on 2008-09-15
How would I go about speeding up my kernel compile time so that it doesn't take hours to preform.

---

### Post by Partyboi2 on 2008-09-15
You could look at something like [[COLOR=Blue]distcc[/COLOR]]("http://myrddin.org/howto/using-distcc-with-debian/").
Here is abit more info if you decide to go with distcc, this was taken from the "kernel/Compile" Wiki
> If you have AMD64 machines available on your local net, they can still participate in building 32-bit code; distcc seems to handle that automatically.   However, with distcc taking over all compiles by default, you will need to set HOSTCC so that when kernel builds want to use the compiler on the host itself, they don't end up distributing jobs to the 64-bit server. If you fail to do that, you'll get link-compatibility failures between 64-bit and 32-bit code. My make-kpkg command, with /usr/lib/ccache at the head of my $PATH, looks like: 

MAKEFLAGS="HOSTCC=/usr/bin/gcc CCACHE_PREFIX=distcc" make-kpkg --rootcmd fakeroot --initrd --append-to-version=-suspend2 kernel-image kernel-headers kernel-source

---

