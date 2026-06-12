---
title: "Ubuntu wont start up"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by downloadfreak on 2008-10-16
Hello,

I have a problem with my ubuntu (8.10 beta). It wont start up. I'm using a laptop and I tried many times but it just wont. I don't know things about other ways to start up than just press the button...

Thanks,
downladfreak

---

### Post by Ryadt on 2008-10-16
Please post in the Intrepid sub-forum. This forum is meant only for stable releases.

---

### Post by keplerspeed on 2008-10-16
Can you please explain exactly whats happening? Assuming you have installed Ubuntu, you should first get a BIOS then the GRUB bootloader. Can you explain what is happening when you press the on button?

Also, can you boot from a cd, to use the Ubuntu live cd?

Good point, can this thread please be moved.

---

### Post by Joeb454 on 2008-10-16
Moved to Intrepid Ibex Testing & Discussion

---

### Post by downloadfreak on 2008-10-16
Sorry for posting in the wrong forum
> **keplerspeed said:**
> Can you please explain exactly whats happening? Assuming you have installed Ubuntu, you should first get a BIOS then the GRUB bootloader. Can you explain what is happening when you press the on button?

Also, can you boot from a cd, to use the Ubuntu live cd?

Good point, can this thread please be moved.

Yesterday it just worked fine, and there was an update so I just updated. When I start it up it doesn't do anything. Only one time it gave me the option you also get in terminal, but I didn't get it again.

---

### Post by stephantom on 2008-10-16
Could be that you're seeing [bug #263059](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263059) too. Maybe you can contribute information to that report.

---

### Post by minisori on 2008-10-16
It can be also the vesa bug with the splash enabled.

---

### Post by downloadfreak on 2008-10-16
I don't think it's the irst one because it doesn't matter if I have my wifi card in or out it just don't work.

Second also probably not because it should be a bit the same.

---

### Post by downloadfreak on 2008-10-16
Or isn''t there a safe mode to start up? Or can't I change kernel?

Please I need help with it.

---

### Post by aethralis on 2008-10-16
When it's starting up try hitting the esc key and you should be greeted with the option of choosing different kernel versions.

---

### Post by downloadfreak on 2008-10-16
Strange I don't get that option...

---

### Post by minisori on 2008-10-17
Don't you see grub menu ? Start in safe mode should be there.

Check if it's related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

If that is your case you can do 2 things:

1. You should start in safe mode and edit /boot/grub/menu.lst, (example: nano /boot/grub/menu.lst)

In that file search for: ## ## End Default Options ##

Just after that is the config of the kernels showing in your start, go to the first line that you can see beginning with "kernel", there just delete the word "splash" at the end. Save and restart.

2. You can also just boot in safe mode, if you don't want to touch anything till it's properly fixed, and from there resume into normal boot.

The problem is caused by usplash, which is not used in safe mode, if that was your problem.

---

### Post by inportb on 2008-10-17
You don't get to choose kernels? Do you use GRUB at all?

---

