---
title: "Choosing the right kernel"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2006-06-10
Hi folks,

after too many problems for a linux newbie, I replaced my 64-Bit Ubuntu with a 32-Bit Ubuntu which I run on an AMD Turion64 cpu.

I hear that there is also a special kernel version for AMD K7. Would it bring me any advantage if I would use the K7 kernel? Or is it not compatible with a 64 Bit cpu.

Total beginner's question, I know. :rolleyes: 

Any recommendations from the experts?

Bye,
Timo

---

### Post by angkor on 2006-06-10
for an amd64 thurion you would install the k7 kernel.

It's failsafe to try because the deafult i386 will still be installed if you don't like the new one, if somethings not working (highly unlikely).

k7 is optimised for your processor, so maybe your pc *feels* a bit faster using this processor. The great advantage is that with the k7 kernel you will have the full use of your RAM, if you have 1G or more installed.

Try it out and see for yourself if the k7 kernel is what you want.

---

### Post by Timokl on 2006-06-10
Thanks for your quick reply. I am apt-getting the k7-kernel package right now. I will tell you about my experience after rebooting. :-)

Bye,
Timo

---

### Post by Timokl on 2006-06-10
I just installed the package *kernel-image-2.4.27-2-k7* with Synaptic. Synaptic installed 4 other packages (which I forgot to remember ](*,) ). Then I rebooted, selected the K7 kernel in the boot menu, but the kernel panicked.

```
Kernel panic: VFS: Unable to mount root fs on 03:03
   APIC error on CPU0 40(40)
```

Do I have to install any other packages?

Bye,
Timo

---

### Post by angkor on 2006-06-10
[QUOTE=Timokl]I just installed the package *kernel-image-2.4.27-2-k7* with Synaptic. Synaptic installed 4 other packages (which I forgot to remember ](*,) ). Then I rebooted, selected the K7 kernel in the boot menu, but the kernel panicked.

```
Kernel panic: VFS: Unable to mount root fs on 03:03
   APIC error on CPU0 40(40)
```

Do I have to install any other packages?

Bye,
Timo[/QUOTE]

You do **not** want to install a 2.4 kernel. It's outdated for desktop use.

Uninstall that kernel with apt-get remove or Synaptic (complete removal).

Try:

```
sudo apt-get install linux-image-k7
```

---

### Post by Timokl on 2006-06-10
[QUOTE=angkor]You do **not** want to install a 2.4 kernel. It's outdated for desktop use.[/QUOTE]

Mostly because it did not work. :-)

> Uninstall that kernel with apt-get remove or Synaptic (complete removal).

Try:

```
sudo apt-get install linux-image-k7
```

Got that. Installed, rebooted - went smoothly. Perhaps it's psychological, but the system *feels* more responsive and quicker (e.g. when it comes to opening Gnome menues)

Angkor, thanks a lot for your help!!!

Bye,
Timo

---

