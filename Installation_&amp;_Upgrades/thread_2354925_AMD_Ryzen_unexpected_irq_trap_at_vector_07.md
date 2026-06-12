---
title: "AMD Ryzen unexpected irq trap at vector 07"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by Ben_Mather on 2017-03-07
Hello,

I have just upgraded my computer to AMD Ryzen with a Gigabyte Aorus  AX370 Gaming 5 motherboard and when I boot into the Ubuntu LiveUSB I  can't get past the Ubuntu splash screen, instead "unexpected irq trap at  vector 07" continuously prints on-screen. This issue has also been  reported over at [https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/935547-amd-ryzen-on-linux](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/935547-amd-ryzen-on-linux) but is still unresolved.

Ryzen is fully compatible with the Linux 4.10 kernel so I've been  attempting to install Ubuntu 17.04, but the same issue occurs for 16.10  and 16.04. I tried a Fedora 25 LiveUSB and it installed flawlessly,  which tells me it is not a hardware fault or a kernel fault. (Even though Fedora installs  fine it is not my desired end-game - I would rather stick with Ubuntu!)

Other things I've noticed:
[LIST]
[*]Ubuntu will boot if acpi=off is set in the GRUB bootloader, but acpi=ht will not. 
[*]Error code 56 - Invalid CPU type or speed - will display on the motherboard whenever Ubuntu is booting. 
[*]I cannot find the source of the IRQ trap from ```
cat /proc/interupts
``` 
[/LIST]

Any help would be greatly appreciated!

---

### Post by mgilbertnz on 2017-03-08
I'm having the exact same problem.  I've got a Ryzen 1800X and the GA-AX370 Gaming 5 motherboard too.

By setting pci=noacpi as a kernel parameter I've managed to boot Ubuntu.  Hopefully this is a bios issue which gets corrected soon.

---

### Post by QIII on 2017-03-08
This is purely a kernel issue -- and I have read in several places that the Ubuntu 4.10 kernel is not yet compatible with the Ryzens even though the mainline 4.10 kernel is.

I think this is just a waiting game for Ubuntu users right now.

---

### Post by mgilbertnz on 2017-03-08
I just resolved this issue by updating my BIOS to version F4.

[http://www.gigabyte.us/Motherboard/GA-AX370-GAMING-5-rev-10#support-dl](http://www.gigabyte.us/Motherboard/GA-AX370-GAMING-5-rev-10#support-dl)

I downloaded the bios zip, extracted the files to a USB flash drive, reboot and press END key on bios page to enter QFlash.  Then updated it and now no more Unexpected Vector issues.

Hope this helps!

---

### Post by Ben_Mather on 2017-03-08
BIOS version F4 doesn't fix it for me :(
Did you change anything from the default settings in the BIOS?

Perhaps QIII is right and Ubuntu's custom compiled 4.10 kernel is playing havoc with Ryzen. Looks like I'll stick with Fedora for now.

---

### Post by QIII on 2017-03-08
In the "use what works" department, sticking with Fedora would be fine idea.

:)

---

### Post by QIII on 2017-03-08
You know...

The 4.11rc kernel is available in the ubuntu mainline kernel ppa...

---

### Post by Ben_Mather on 2017-03-08
I tried installing 4.11rc but it did not prevail :(

---

### Post by ludo-surfer on 2017-03-11
I have the same error here when trying to install ubuntu 17.04 beta daily iso.
Gigabyte AX370 gaming 5 too.

---

### Post by Ben_Mather on 2017-03-11
My running hypothesis is that there is some hardware on the Gigabyte AX370 gaming 5 motherboard that Ubuntu doesn't like. I'd assume it would be the same issue on Ubuntu derivatives.

Have you tried installing Fedora? That works for me.

---

### Post by P-I H on 2017-03-12
In my case the system boots fine, both on zesty and Ubuntu 16.04.2, with a MSI-B350-Tomahawk motherboard and the AMI bios from 02-15.
However sensors are missing, there is an X.org problem and **journalctl -p warning -b** gives some unexpected information
```
mar 12 05:57:11 pi-MSI-B350-Tomahawk-Kingstone kernel: AMD-Vi: Event logged [
mar 12 05:57:11 pi-MSI-B350-Tomahawk-Kingstone kernel: IO_PAGE_FAULT device=24:00.0 domain=0x0003 address=0x000000f4004dc600 flags=0x0010]

```

---

### Post by epb9000 on 2017-03-23
> **Ben_Mather said:**
> My running hypothesis is that there is some hardware on the Gigabyte AX370 gaming 5 motherboard that Ubuntu doesn't like. I'd assume it would be the same issue on Ubuntu derivatives.

Have you tried installing Fedora? That works for me.
Fedora worked fine for me too. (Gigabyte GA-AB350 Gaming, Ryzen 7 1700)

But I really wanted to use Ubuntu LTS, so I cloned the Fedora kernel repo and built 4.10.4 from branch F25.  I have a couple of warnings in the journal, but aside from that things seems to be working fine.

---

### Post by mirth99 on 2017-03-31
I have exactly the same problem with Ryzen 1800+ on Gigabyte AB350-Gaming 3 motherboard. 
[LIST]
[*]Ubuntu variations (Ubuntu, Neon, Kubuntu, Budgie) and openSUSE do NOT WORK out of the box. It stalls with a bunch of 'irq trap at vector 07' messages.
[*]I have to add acpi=off to the kernel parameters. At that point it runs/installs, but runs on only one core and the system locks up during shutdown.
[*]I tried other acpi paramaters, nothing works.
[*]I tried to compile a new kernel but it takes forever with only one core... I gave up after a couple of hours.
[*]Fedora and KaOSx run/install with no problems at all.
[*]Needless to say, this is a really serious problem. I have run exclusively Kubuntu for years. If this isn't fixed soon, I'l have to switch to a non-Ubuntu based distro.
[*]Gigabyte has not updated the bios at all.
[/LIST]

---

### Post by sorin7486 on 2017-04-22
> **mirth99 said:**
> I have exactly the same problem with Ryzen 1800+ on Gigabyte AB350-Gaming 3 motherboard. 
[LIST]
[*]Ubuntu variations (Ubuntu, Neon, Kubuntu, Budgie) and openSUSE do NOT WORK out of the box. It stalls with a bunch of 'irq trap at vector 07' messages.
[*]I have to add acpi=off to the kernel parameters. At that point it runs/installs, but runs on only one core and the system locks up during shutdown.
[*]I tried other acpi paramaters, nothing works.
[*]I tried to compile a new kernel but it takes forever with only one core... I gave up after a couple of hours.
[*]Fedora and KaOSx run/install with no problems at all.
[*]Needless to say, this is a really serious problem. I have run exclusively Kubuntu for years. If this isn't fixed soon, I'l have to switch to a non-Ubuntu based distro.
[*]Gigabyte has not updated the bios at all.
[/LIST]

I have a Gigabyte Gaming 3 board as well with a Ryzen 1600 and Linux Mint runs with all cores using Kernel 4.4.0. On newer kernel versions I have the same problems you do having to start with acpi=off and running only one core. The downside is that my graphics card doesn't work on 4.4.0, but I can live with that until I find a solution to this.

---

### Post by jonnyboysmithy on 2017-04-24
> **sorin7486 said:**
> I have a Gigabyte Gaming 3 board as well with a Ryzen 1600 and Linux Mint runs with all cores using Kernel 4.4.0. On newer kernel versions I have the same problems you do having to start with acpi=off and running only one core. The downside is that my graphics card doesn't work on 4.4.0, but I can live with that until I find a solution to this.

I have found ubuntu 14.04 which runs kernel 4.4 to work just beautifully out of the box. I also have a ryzen 1600 and I have a gigabyte gaming 3: specifically: AB350m HD3
However, I require kernel 4.6 or newer for some of my hardware (intel 826NGW) and it appears ubuntu 16.04 with kernel 4.8 has the irq trap issue.

tl;dr, similar hardware, I'm on the same boat.

Any known fix?

---

### Post by sorin7486 on 2017-04-24
> **jonnyboysmithy said:**
> I have found ubuntu 14.04 which runs kernel 4.4 to work just beautifully out of the box. I also have a ryzen 1600 and I have a gigabyte gaming 3: specifically: AB350m HD3
However, I require kernel 4.6 or newer for some of my hardware (intel 826NGW) and it appears ubuntu 16.04 with kernel 4.8 has the irq trap issue.

tl;dr, similar hardware, I'm on the same boat.

Any known fix?

I found a solution to the problem: there is an issue logged in launchpad for this and someone from the kernel team provided a custom kernel build that works for me:

[https://bugs.launchpad.net/ubuntu/+sour](https://bugs.launchpad.net/ubuntu/+sour) ... ug/1671360

You can download the kernel from here:

[http://kernel.ubuntu.com/~jsalisbury/lp1671360/](http://kernel.ubuntu.com/~jsalisbury/lp1671360/)

---

### Post by intercambionosopa on 2017-05-21
[IMG]https://community.amd.com/servlet/JiveServlet/showImage/2-2799447-121120/WP_20170519_10_13_33_Pro.jpg[/IMG]
Apparently eh tested almost all the distros that there are at least: Linux Mint 18.1 "currently running kernel 4.4". fedora 25" displays the installation but then black screen . opensuse 42.1 apparently without problems.
Distributions with faults vector 07 . any distro of Ubuntu currently 17.04.
I think you can resolve also notify gigabyte of some things that it is sending.
__
This is what notify gigabyte.
"A few days ago I bought my first Gigabyte GA-AX370 gaming 5 with the disappointment that "almost" any version of Linux is available.
Unfortunately eh read other users upset by the matter and wanting to return the product. I believe Gigabyte should clearly mention that Linux doesn't have any support.
What I am is the following:
"Due to different Linux support condition provided by chipset vendors, please download Linux driver from the web site of the chipset manufacturers or third party web site.".
From this Gigabyte does not mention that the system work" standard mode" becoming believe the user to at least the operating system to function. Not to mention that in all the web only a line of site makes mention of linux with a tiny and a bit confusing."
I hope that you have at least some sort of recognition to the user.
Thank you and I look forward to your reply as soon as possible."

Nvidia forum :
Make sure you're running the latest BIOS. From what I've seen on the Ubuntu and Linux tracker, I believe the the maintainers enabled some gpio/debugging flags (GPIO_AMDPT and GPIO_AMD8111) in the Ubuntu kernel and this caused IRQ issues on specific Gigabyte AM4 boards with certain BIOS revisions. Also, you need at least Kernel 4.10 to properly utilise AMD Ryzen processors/chipsets. 


You could try running the latest mainline 4.10/4.11 kernel (without the Ubuntu modifications) or try out this kernel which was compiled without those flags. This isn't an Nvidia issue, it's up to the Kernel devs to fix it. BTW, dump Linux Mint, they don't care about recent kernels.


-----------
Español
Al parecer eh probado casi todas las distros que hay al menos: Linux mint 18.1 "actualmente funcionando a kernel 4.4". fedora 25" muestra la instalacion pero luego pantalla en negro . opensuse 42.1 al parecer sin problemas. 
Distribuciones con fallos vector 07 . toda distro de ubuntu actualmente 17.04. 
Creo que se puede resolver igualmente notifique a gigabyte de algunas cositas que se esta mandando.
______________ 
Esto es lo que notifique a gigabyte. 
"Hace unos dias eh comprado mi primera placa Gigabyte GA-AX370 gaming 5 con la decepcion de que "casi" ninguna version de linux esta disponible. 
Desgraciadamente eh leido a otros usuarios molestos por el asunto y queriendo devolver el producto. A mi entender Gigabyte deberia de mencionar claramente que LINUX no tiene ningun soporte. 
Lo que me encuentro es lo siguiente:
"Debido a la diferente condición de soporte para Linux proporcionadas por proveedores de chipsets, por favor descargue el controlador de Linux desde el sitio web de los fabricantes de Chipsets o sitio web de terceros.".
A partir de esto Gigabyte no menciona que el sistema funcione a" modo estandar" haciéndose creer al usuario que al menos el sistema operativo pudiera funcionar. Sin mencionar que en toda la web solo un renglon del sitio hace mencion a linux con una letra diminuta y un texto algo confuso".
Espero que se tenga algun tipo de reconocimiento minimo al usuario. 
Gracias y espero su respuesta a la brevedad."

---

### Post by peter-ludwig on 2017-11-26
I am running Ryzen 1700x on Gigabyte AX370-Gaming K5
First it took around 15-20 secs until the PC passed BIOS. After I think the 3rd Bios this went smooth (5 - 10 secs to pass BIOS). But I always had those funny BIOS messages but they never troubled my OS / PC. I am running Mint Mate 17.3 and 18.1.

I updated lately to Kernel 4.11.0-14-generic. Because I thought the warnings would disappear. But they just changed.

I still got now the BIOS message:

> 
*irq 7*: *nobody cared* (try booting with the "*irqpoll*" option)
handlers:
[<ffffffffb6e962a0>] amd_gpio_irq_handler
Disabling IRQ #7


I always can read this in dmesg: (is that important?)

> 
Hardware name: Gigabyte Technology Co., Ltd. AX370-Gaming K5/AX370-Gaming K5-CF, BIOS F5a 09/08/2017
[15120.402851] Call Trace:
[15120.402852]  dump_stack+0x63/0x90
[15120.402852]  __warn+0xcb/0xf0
[15120.402853]  warn_slowpath_fmt+0x5a/0x80
[15120.402854]  mce_amd_feature_init+0x27b/0x2c0
[15120.402855]  __mcheck_cpu_init_vendor+0xa0/0xc0
[15120.402856]  mce_syscore_resume+0x22/0x30
[15120.402857]  syscore_resume+0x49/0x190
[15120.402858]  hibernation_snapshot+0x29e/0x3c0
[15120.402859]  hibernate+0x1a4/0x340
[15120.402860]  state_store+0xe5/0xf0
[15120.402861]  kobj_attr_store+0xf/0x20
[15120.402861]  sysfs_kf_write+0x37/0x40
[15120.402862]  kernfs_fop_write+0x120/0x1a0
[15120.402863]  __vfs_write+0x18/0x40
[15120.402864]  vfs_write+0xb8/0x1b0
[15120.402865]  SyS_write+0x55/0xc0
[15120.402866]  entry_SYSCALL_64_fastpath+0x1e/0xad


**OR this**

 Call Trace:
[    2.169612]  <IRQ>
[    2.169616]  dump_stack+0x63/0x90
[    2.169619]  __report_bad_irq+0x33/0xc0
[    2.169620]  note_interrupt+0x23e/0x280
[    2.169621]  handle_irq_event_percpu+0x54/0x80
[    2.169622]  handle_irq_event+0x3b/0x60
[    2.169623]  handle_fasteoi_irq+0x8f/0x140
[    2.169626]  handle_irq+0x1a/0x30
[    2.169628]  do_IRQ+0x46/0xd0
[    2.169629]  common_interrupt+0x89/0x89
[    2.169630] RIP: 0010:native_safe_halt+0x6/0x10
[    2.169631] RSP: 0018:ffffffffb7803d60 EFLAGS: 00000246 ORIG_RAX: ffffffffffffffc8
[    2.169632] RAX: 0000000000000000 RBX: ffff9408fa8e1000 RCX: 000000000000001f
[    2.169633] RDX: 4ec4ec4ec4ec4ec5 RSI: 0000000000000034 RDI: ffff9408fa8e1064
[    2.169633] RBP: ffffffffb7803d60 R08: ffff94091ec181e4 R09: 0000000000000018
[    2.169634] R10: ffffffffb7803db0 R11: 00000000000000ee R12: ffff9408fa8e1064
[    2.169634] R13: 0000000000000001 R14: 0000000000000001 R15: 0000000000000001
[    2.169635]  </IRQ>
[    2.169636]  acpi_safe_halt.part.4+0xe/0x20
[    2.169637]  acpi_idle_do_entry+0x38/0x50
[    2.169639]  acpi_idle_enter+0x112/0x2d0
[    2.169641]  ? sched_clock+0x9/0x10
[    2.169642]  cpuidle_enter_state+0xfa/0x2d0
[    2.169643]  cpuidle_enter+0x17/0x20
[    2.169645]  call_cpuidle+0x23/0x40
[    2.169646]  do_idle+0x17f/0x1f0
[    2.169647]  cpu_startup_entry+0x71/0x80
[    2.169648]  rest_init+0x77/0x80
[    2.169650]  start_kernel+0x473/0x494
[    2.169652]  ? early_idt_handler_array+0x120/0x120
[    2.169653]  x86_64_start_reservations+0x24/0x26
[    2.169654]  x86_64_start_kernel+0x143/0x166
[    2.169655]  start_cpu+0x14/0x14



I am not sure if this is important because for me everything runs fine. I can even hibernate which I really like. No crashs, hangs or similar. Once a month I only can move the mouse but nothing else will work for 2-3 minutes. (No click on anything, no NUM Key, No SYSREQ, no switching to console ...) The PC halts completely (I know because even the clock stops running) But after these 2-3 min. everything runs fine again. But I have this "big" since 12-18 months now. So no specific kernel thingy.

---

### Post by cactus-man on 2018-07-15
I have same problem. Linux Mint, based of ubuntu, works very well and I don't notice to many differences between it and ubuntu. I am running Mint 19.

---

