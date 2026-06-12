---
title: "&quot;nolapic&quot; what does it do?"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by lukeminus on 2007-12-05
Kiaora,

I have a simple Q. When I did my install I had to add the command *nolapic* for it to proceed. What does it actually do and will it effect Ubuntu's overall performance now that it is installed? (if so what do I need to do to change it?)

I have AMD64 Turion x2 processors and using the AMD64 version of Ubuntu if that makes any difference. :)

Chur,

Luke.

---

### Post by Pumalite on 2007-12-05
[http://ubuntuforums.org/archive/index.php/t-3000.html](http://ubuntuforums.org/archive/index.php/t-3000.html)

---

### Post by lukeminus on 2007-12-05
> APIC is a fancy interrupt router , sending interrupts to be handled by the least busy processor in a SMP (multi processor) system. Disabling it on a uniprocessor system makes absolutely no impact on performance or anything else.


Disabling apic on a SMP system could cause lower performance under high load conditions. Of course, APIC should never break on a SMP system!

Cheers... the above thread said it had no impact on a uni-processor system, but as I am using a multiprocessor system, does this have an effect on performance, and should I/how would I change it?

Cheers folks

---

