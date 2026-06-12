---
title: "Switchingkernels on the fly?"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Asix on 2007-03-02
I've upgraded to Edgy (from Dapper) about four months ago, and, of course, Edgy came with the brand - new kernel back then, and everything went fine for a while.
Then, I added some more printers, network interface cards, modems and so on to my computer, and then the pain started.
The new kernel didn't recognize several devices, and I've tried everything, but nothing worked. Then, I decided to recompile older kernel, which comes with Dapper, and then try again.
And then, a miracle happened. All hardware was working properly after rolling back to older kernel. But, the older kernel is also incompatible with some other set of devices, and if I switch back to Edgy's kernel, then they will work, but these previous ones won't.
So, my question is: is there a way I could change kernels on the fly without the need to reboot the system? Is that actually possible to do in Linux? Thanks in advance.

---

### Post by jimbren on 2007-03-02
You have to reboot to go from one kernel to another.

jimbo

---

