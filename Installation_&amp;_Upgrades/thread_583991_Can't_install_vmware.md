---
title: "Can't install vmware"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2007-10-20
I installed gutsy having had feisty previously feisty, clean installed, and like many others, found that I could not add new software. It kept telling me that the software can't be installed on my computer type (i386), which of course is rubbish.  So, as recommended, I went into software sources and ticked everything. This seemed to fix the problem,

until...

Today I wanted to install vmware player. I went to add/remove programs, and searched for it. It found one, but it refuses to install with the same error as above.

I searched with Synaptic, and it doesn't find it at all.

Why is this happening in gutsy?

---

### Post by ldesilva on 2007-10-20
I did a search on vmware on synpatics and could not find it too. I ended up downloading it from vmware site and install it manually. 

By the way, I have installed vmware server 1.04 and works perfectly well on 7.10.

---

### Post by ubnewbie2 on 2007-10-20
> **ldesilva said:**
> I did a search on vmware on synpatics and could not find it too. I ended up downloading it from vmware site and install it manually. 

By the way, I have installed vmware server 1.04 and works perfectly well on 7.10.

Yes, I will have to go that way too if Ubuntu's package system remains broken like this.

...and I might go for vmware server like you did too :)

---

### Post by sciadellacometarossa on 2007-10-20
I also installed vmware player 2, the config script (vmware-config.pl) tried to compile a new module for my kernel and it failed!
The error message indicates a page on vmware site, and there it is a little patch which allow the module generation.

Let us know if you closed the case.

---

### Post by ubnewbie2 on 2007-10-20
> **sciadellacometarossa said:**
> I also installed vmware player 2, the config script (vmware-config.pl) tried to compile a new module for my kernel and it failed!
The error message indicates a page on vmware site, and there it is a little patch which allow the module generation.

Let us know if you closed the case.

Well, yes, there are alternatives for vmplayer, but for me, the "case" is the problem with Gutsy's add/remove program system.  If that isn't resolved, then this problem can keep re-occurring, and there won't always be an alternative (for me) to just installing Ubuntu's package.

---

### Post by Floppyjoe on 2007-10-20
I can't get vmware to work on Gutsy 7.10 either. I think this is because of the kernel modules that are needed for the new kernel are not made yet. To use VMWARE I have to boot with the old kernel.

---

### Post by ubnewbie2 on 2007-10-21
> **Floppyjoe said:**
> I can't get vmware to work on Gutsy 7.10 either. I think this is because of the kernel modules that are needed for the new kernel are not made yet. To use VMWARE I have to boot with the old kernel.

Yes, but the install script you get in the download from vmware goes ahead and compiles all the modules it needs just fine.  A few minutes later, I have a working vmware player running with gutsy's kernel, no problems

---

