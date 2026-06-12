---
title: "kernel build question on feisty : massive initrd file"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by markjf on 2007-04-21
summary: my initrd file after a kernel compile is massive compared to default installed version, why?
default initrd file = 7mb, mine = 44mb

recently set up on old machine to run ubuntu feisty fawn for the purpose of learning more about kernel building.

following the guildlines in here, i managed to get a default setup compiling, with nvidia restricted module (and ndiswrapper thrown in for good fun). i copied the config file from the default build and changed no options (i wanted a "clean" build).

my kernel boots fine, but the initrd file is massive compared to the default ubuntu build.

looking inside the initrd files, i notice that all the .ko files under lib/modules/2.6.xxxxx/kernel/ are much larger in my new compile. this is the only area where the initrd files differ in size.

e.g. the "drivers" subdir takes up 74mb instead of 9.5mb, "fs" subdir is 26mb instead of 2mb.
all the same files seem to be there, but are much bigger.

e.g. 3c59x.ko is 275k in my build, 61k in default build, ext2.ko is 1.3mb in mine, 78k in default.

i've run file on each pair and they both produce same "ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped"

why are my compiled versions so much bigger? and can i reduce them to get my ramdisk size down?

thanks,
mark

p.s. cross posted from beginners section where it was on page 3 in under 30 mins without being read

---

### Post by antiplex on 2007-06-01
i'm having similar issues (plus an additional one) and described them [here (posts # 378 & 379)]("http://ubuntuforums.org/showthread.php?t=311158&page=38") but haven't found any soultion so far :(
hints are very welcome...

edit: i found others have asked something like this before (like in [this thread]("http://ubuntuforums.org/showthread.php?p=2760213") for instance) but nobody seemed to bother, either most people don't check the sizes of their built kernels/modules/initrds or this is a very rare problem that only happens to bloody kernel-compile-beginners...

---

### Post by markjf on 2007-06-01
i found that most of it was just debug info and managed to remove it once i'd found the right option.
iirc, it's Kernel Hacking/Kernel Debugging. turned it off and the initrd file size melted away.

found some articles on stripping the files in the image file, but "strip" actually removes too much information and the kernel doesn't boot.

zcat /boot/initrd.img-2.6.20.3-ubuntu1-mjf-cutdown | cpio -vid
for f in $(find . -type f); do file $f | grep 'not stripped' && strip $f; done

this works as i say, but is too agressive, and your kernel won't boot! but is a good starting point as to working out how to reduce file sizes. i can't remember the final commands i used, googling around i found some information on how not to strip everything and was able to knock a bit more off the file sizes, but the largest chunk of it was simply that the kernel debug was on.

---

### Post by antiplex on 2007-06-01
> **markjf said:**
> i found that most of it was just debug info and managed to remove it once i'd found the right option.
iirc, it's Kernel Hacking/Kernel Debugging. turned it off and the initrd file size melted away.  **thank you very much for that piece of information!**
i just checked and found out that '[COLOR="Sienna"]Kernel hacking / Kernel debuggung[/COLOR]' (CONFIG_DEBUG_KERNEL) and as a sub-feature '[COLOR="Sienna"]Kernel hacking / Compile the kernel with debug info[/COLOR]' (CONFIG_DEBUG_INFO) were both checked though not really necessary if one's not into kernel development, so this seems to be a step into the very right direction.
this appears weird to me in some way since i simply used the lasted config (/boot/config-2.6.20-16-generic) as starting point for my own config thinking that this config might contain exactly the same options as the kernel running which in my case fur sure didn't have these options turned on during compilation. or well, someone striped away the unecessary data... at least its confusing for someone who hasn't been compiling kernels for years.

by the way, i just noticed that your kernel is called 'initrd.img-2.6.20.**_3_**-ubuntu1-mjf-cutdown' which was another issue that was confusing me, because i have that >>3<< also appended but thought since i've seen a >>5<< showing up in the middle row of the output of 'dpgk -l | grep "linux-", this would correspond to the kernels latest sub-sub-sub-revision. so i thought i might have a weird problem with old remnants of earlier tries. 
but as i just checked again recently i found that this only applies to the restriced kernel modules so i guess i might have just gotten a bit too confused by all this kernel-compilation stuff...

again, thanks a lot for letting me know; i will try and see what happens ;)

---

### Post by jacek2v on 2007-06-03
Hey, i have this same problem and I checked solusion ('Kernel hacking / Kernel debuggung' (CONFIG_DEBUG_KERNEL) and as a sub-feature 'Kernel hacking / Compile the kernel with debug info' (CONFIG_DEBUG_INFO)) and it's working :)
Previous my initrd have about 40MB now ~5MB.
 
Thanks a lot

---

### Post by antiplex on 2007-06-05
yes, everything worked out fine form me as well. initrd, vmlinuz and modules are now all smaller than the standard ones, for instance my new initrd.img is ~5.4mb, the standard one ~6.6mb, my vmlinuz is now ~1.2mb, original ~1.7mb.
well, and most important, everything is running like a charm! could say my issue's solved.
thanks again!

cheers, anti :D

---

