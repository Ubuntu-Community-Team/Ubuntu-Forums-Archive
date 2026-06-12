---
title: "Stuck compiling kernel using localmodconfig ..."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2011-06-13
Hi all,

I'm about to compile a custom kernel using localmodconfig using the guide on [this]("https://help.ubuntu.com/community/Kernel/Compile") page. Everything's gone well but now I'm stuck. Can anyone work out what the syntax of the part in bold below is supposed to be? I have tried all combinations, e.g. linux-source-2.6.35-Myimage, and a few other permutations. Nothing seems to work. Probably the ambiguity of the instructions or my ignorance or both:

```
fakeroot make-kpkg --initrd --**append-to-version=-some-string-here** kernel-image kernel-headers
```And anyone got any ideas how I might 'turn OFF   "Compile the kernel with debug info"'?

> ... Ubuntu kernels build with debugging information on, which  makes the  resulting kernel modules (*.ko files) much larger than they  would  otherwise be. To turn this off, go into the config's "Kernel   hacking"<!-- ; then, under "Kernel debugging", --> and turn OFF   "Compile the kernel with debug info". 
 I've hit a few brick walls on the way but they turned out to be wet cardboard. This one's a little more solid. Any clues much appreciated.

* UPDATE: Figured the first part out: '--**append-to-version=-some-string-here' **... should be pretty much what it says. I entered '--append-to-version=MyImage' and it worked! Compiling now. But couldn't work out the second part to switch off debugging.

---

### Post by Bucky Ball on 2011-06-13
Well, I have successfully compiled, installed, booted and am posting from the custom kernel. I didn't change anything in 'menuconfig' on the way but used the 'loadmodconfig' option for the compile which is supposed to install only the modules your system is using and strip the rest (it checks 'lsmod'). All good.

So, I've answered my first question, but not the second; half solved:

> ... Ubuntu kernels build with debugging information on, which  makes the   resulting kernel modules (*.ko files) much larger than they  would   otherwise be. To turn this off, go into the config's **"Kernel    hacking"<!-- ; then, under "Kernel debugging", --> and turn OFF    "Compile the kernel with debug info".**                       Any idea on how to switch it off? I don't understand the bit in bold.

I am going to do a minimal install, add the few apps I need and use for study and interneting, then compile a custom kernel using 'localmodconfig'. Why? Because I want to and for once I have the time! The minimal install I did a couple of days ago is giving me 12 seconds to the login screen. Screamin' along. Going to try Arch next. ;)

Lovin' the linux ...

PS: Tells me I have 399 modules installed but seems about the same time boot as the regular install. I'll keep tweaking and experimenting ...

---

