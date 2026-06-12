---
title: "Lpia Kernel"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cariboo on 2009-01-28
I noticed in the Jaunty Changes Digest, that there is a lpia kernel available, will this work with my Intel Atom powered media center?

JIm

---

### Post by bgerlich on 2009-01-28
Lpia is an acronym for Low Power Intel Architecture, so yes it will work on Menlow (atom) platform. I haven't looked to much into it but I would imagine that this kernel aims to be a paradigm of prolonging battery life and low power usage.
 I don't know if this would be beneficial for a media center, where low latency would be important.

---

### Post by Confuseling on 2009-04-07
I've heard that packages compiled optimised for LPIA will run faster on Atoms, as well as using less power.

The drawback being that not many third party repositories are compiling for LPIA at present (although you can probably just force it to ignore architecture from i386 binaries, you won't get updates). Ubuntu are in the process of copying their channels over, so I suppose the choice comes down to how much you intend to use third party software.

Questions: Anyone using LPIA? (particularly on netbooks?)

Can you tell any difference in speed / battery life?

Thanks.

---

### Post by dirtylobster on 2009-04-07
I'd like to but haven't figured out how to do it yet. I'm running standard i386 at the moment.

---

### Post by Confuseling on 2009-04-14
Well, installing LPIA through USB turned out to be pretty straightforward using the USB creator in ubuntu and a daily build image - unetbootin just GPFed my Windows machine.

Interestingly, I've found this thread [http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835), and can confirm that the script can be used to repackage i386 debs for LPIA, although obviously there's no guarantee that they'll work. Very handy - I just hope they update OK.

I don't have any frame of reference so can't comment on performance / battery difference between i386 and LPIA. My major concern now though is that if I decide I want to update to the .29 or even .30 kernel, which as I understand it have subsumed LPIA support into the main branch, I don't know if I'll be able to do it without a full reinstall. Trying to install .29 complained about the architecture being wrong - and I'm not feeling brave enough to force or repackage it. Anybody know any more than I do?

---

### Post by Zorael on 2009-04-15
What's different, then? What options at compile time makes it aimed for lpia?

edit: Or is it an option passed to the compiler itself, instead of a kernel .config option?

---

### Post by Confuseling on 2009-04-15
If you mean when downloading a new kernel, I've just been trying the precompiled debs. I'm on a SSD, so I don't really want to compile a kernel unless I have to - I've heard its absolutely brutal from an IO operations perspective.

---

### Post by Zorael on 2009-04-15
I need to patch the source to get dithering to work properly when using KMS (2.6.29.1), and I like to toy around with the .config file in general. I'm using kernelcheck to automate things though, so if it's an argument passed to the actual compiler no wonder I missed it.

---

### Post by Confuseling on 2009-04-15
I'm afraid I'm not sure.

I did a fresh install of the LPIA version from an LPIA iso - whether you can compile the normal i386 source into different architectures, and whether using an LPIA kernel with i386 software would get you anywhere is beyond me.

Can you compile it into x64?

---

