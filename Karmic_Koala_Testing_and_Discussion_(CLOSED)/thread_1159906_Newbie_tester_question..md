---
title: "Newbie tester question."
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whitefort on 2009-05-15
Hi, I've never been in on the Alpha stage of testing before.  My question is, is it useless to test the Alpha inside something like Virtualbox?

I don't feel comfortable installing the alpha on my machine 'for real', but I'm wondering if using a virtual machine might just muddy the waters and produce results that are useless for testing and bug hunting.

Thanks!

---

### Post by 23meg on 2009-05-15
While virtual machines are a valid use case, bugs from real hardware are much more useful, and you'll probably have a hard time producing useful debugging information. If, however, you're only looking to test high-level things such as basic userspace apps that aren't deeply hardware dependent, user interfaces and so on, virtual machines should be fine. You should still keep an eye open for at least the known intricacies of the combination of your hardware and the virtualization software, if any.

If you report bugs, remember to indicate that you're running Karmic in a virtual machine, and state which.

---

### Post by whitefort on 2009-05-15
Thanks 23Meg, that's very helpful.

I was planning to install a virtual Koala anyway, just out of curiosity, but wasn't sure if I should submit any bug reports at all.

Thanks again!

---

