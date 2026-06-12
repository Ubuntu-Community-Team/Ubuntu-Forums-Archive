---
title: "kernel panic - not syncing: attempted to kill init!"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by javravenx on 2008-06-06
hello anyone that might answer, 

i am desperatly trying to install ubuntu onto my computer however everytime i try to boot the live CD i get the message:

[93.930234] kernel panic - not syncinc: attempted to kill init!

i'm not sure but attempting to kill anything wheather it be "init" or not seems pretty serious. so can anyone help me? 


Javan

---

### Post by jpkotta on 2008-06-06
[http://www.linuxquestions.org/questions/linux-software-2/explained-kernel-panic-not-syncing-attempted-to-kill-init-353920/?](http://www.linuxquestions.org/questions/linux-software-2/explained-kernel-panic-not-syncing-attempted-to-kill-init-353920/?)

You have to get more information like the link says.

---

### Post by double.espresso on 2008-09-01
I too am having a kernel panic whilst attempting to install 8.04.01

Here's some more information:

I get the language menu, then the install menu. Doesn't matter whether I go for install, or 'try without making changes' - I get the loading kernel progress bar then lots of progress messages, along the lines of:

[54.661542] [<c0282818>] driver_probe_device+0x88/0x190

... nothing that says error, or failed to do anything, etc.

Then:

[54.663432] =======================
[54.663509] Code: fc c3 55 31 ed 57 56 31 f6 53 83 ... (etc - about 3 lines of hex pairs)
[54.666345] EIP: [<c024d11a>] acpi_rs_get_pci_routing_table_length+0x29/0xa1
SS:ESP 0068:de433e00
[54.666670] ---[ end trace ca143223eefdc828 ]---
[54.666768] Kernel panic - not syncing: Attempted to kill init!


...which is game over.

I've tried the memory test on the CD and after 25+ hours there are no reported errors in the 256MB of RAM.

The numbers in the square brackets at the line starts are different each time (last time the kernel panic line started [49.731890]), if they mean anything for diagnosis.

However, the 3 lines of hex pairs appear the same each time, as are all the other numbers - EIP, routing_table_length, SS:ESP, end trace, all of it.

Should have added in the above list, the last thing it appears to do is:

[<c0421420>] kernel_init+0x0/0x320
[<c0421420>] kernel_init+0x0/0x320
[<c0105677>] kernel_thread_helper+0x7/0x10

(yes, the kernel_init line is there twice, identical but for the [54.whatever] at the line start)


Machine is a tiny, tiny, Viglen "Contender MPC" (see [www.enviroquiet.com](www.enviroquiet.com)), albeit an older version with a mere 400MHz processor and 256MB RAM. The current machine is offered with Ubuntu pre-installed, I believe, as was the older version.

Any suggestions, at all?

I'm wanting to set it up as a small, low-energy, print server.

Many thanks.

---

### Post by Andy Armstrong on 2008-12-19
> Machine is a tiny, tiny, Viglen "Contender MPC"

I've just had the same problem with a Viglen MPC-L. You need to add

```
acpi=off
```

and possibly

```
pnpbios=off
```

to the kernel boot line. Hit escape to get the grub menu, 'e' to edit the entry and then follow the instructions to edit the kernel line.

Once you have Ubuntu installed you can make the changes permanent by editing /boot/grub/menu.lst. Here's a fragment of mine (scroll to the right to see the important bit of the kernel line):

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c14bb3bf-df34-4205-baa5-a2053a7449f1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c14bb3bf-df34-4205-baa5-a2053a7449f1 ro splash acpi=off pnpbios=off
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

Note that I *think* you'll also need to make sure that you're running the generic kernel. I've installed Intrepid server on mine so I replaced linux-image-server with linux-image-generic. I don't think the MPC will boot from the default server kernel.

---

