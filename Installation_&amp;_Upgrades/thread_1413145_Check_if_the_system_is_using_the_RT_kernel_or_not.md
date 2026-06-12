---
title: "Check if the system is using the RT kernel or not?"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by cub on 2010-02-22
I followed the installation guide on [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) doing the Full Upgrade (including installing the linux-rt).

Everything seems to be working fine, but I was surprised then the Update Manager suggest to update kernel and it says generic.

And when I open System Monitor it says "Kernel Linux 2.6.31-14-generic". Should this be a "-rt" kernel?
In Synaptic Package Manager it says that I have linux-rt installed, version 2.6.31.9.10.

So, I'm very unsure whether I should accept the updates from Update Manager?
Which kernel is my laptop using? Can I check this any other way to be sure?

---

### Post by cchhrriiss121212 on 2010-02-22
As you are using regular ubuntu you will still be prompted to download generic kernels. System monitor is correct: you are still using a generic kernel.
GRUB lets you decide which kernel you use when you boot up, in karmic I think the menu will not display itself unless you press a button (shift I think).
Solution:
Check you have all the correct headers for your rt kernel, then download a nice GUI program called startup manager from synaptic. Open it up and you will be able to select which kernel to use when you boot without having to go through GRUB menu each time.

---

### Post by zvacet on 2010-02-22
To see witch kernel you use type in terminal

```
lsb_release -a
```

or

```
uname -a
```

You probably have both (generic and rt).If rt is working O.K. you can remove generic kernel from synaptic by typing in search box linux-image.Then find linux-image-generic and remove it.As I said do it when you are sure that rt is working.

---

### Post by cub on 2010-02-22
Thanks! And yes, it apparently run the generic kernel. I will do the boot option as suggested.

Is there any reason I might want to change a boot into the generic or rt kernel? For instance, to boot with generic when I'm not going to do any recording and just ordinary pc stuff? Or is it all the same and always boot with rt kernel?

---

### Post by cchhrriiss121212 on 2010-02-22
Generic kernel has no advantage over the rt variant, providing that they both run the way they should. Some systems are unstable with the rt, so I usually keep the generic around just in case.

---

### Post by zvacet on 2010-02-23
> Is there any reason I might want to change a boot into the generic or rt kernel? For instance, to boot with generic when I'm not going to do any recording and just ordinary pc stuff? Or is it all the same and always boot with rt kernel?

I never used it but as far I understand rt is adjust for ubuntu studio.So there is no reason for not using it all time.Of course if it works as it should.

---

