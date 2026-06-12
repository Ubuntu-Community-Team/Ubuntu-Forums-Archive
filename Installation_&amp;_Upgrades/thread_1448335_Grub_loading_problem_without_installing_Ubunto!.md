---
title: "Grub loading problem without installing Ubunto!"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by Onewinged on 2010-04-06
My husband was checking out if he'd like to use ubunto on his windows 7 pc and ran the trial demo, ever since this when ever he attempts to boot his pc he gets the following error message :
Grub loading
error no such disk
Grub rescue
He can not acess windows and has no windows 7 install or recovery disk. Is there anyway we can fix this?
Thanks in advance

---

### Post by dstew on 2010-04-06
What do you mean by "ran the trial demo"? Did you try to install Ubuntu? Do you have an Ubuntu Live CD?

---

### Post by Onewinged on 2010-04-06
He's tried to uninstall without any sucess and he ran the demonstration of ubunto on the ubunto live CD.

---

### Post by Mark Phelps on 2010-04-06
> **Onewinged said:**
> He can not access windows and has no windows 7 install or recovery disk. Is there anyway we can fix this?

Will answer this second part first ...

If you go to the link below and follow the instructions, you will be able to download an ISO of a Win7 Repair CD -- which you can then burn to a CD and boot from in order to restore Win7 boot capability:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

But what is confusing about your problem description is that the "try without installing" is exactly that -- a temporary loading of the kernel and other software to a RAM disk (virtual disk created solely in memory) and it has NO EFFECT on the host machine.

The only way you would be getting a GRUB menu is if he attempted to install Ubuntu.

---

