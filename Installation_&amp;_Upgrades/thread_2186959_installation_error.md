---
title: "installation error"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by sunnysanchit99 on 2013-11-10
hi i am a newbie for ubuntu 12.04 lts few days earlier my ubuntu get damaged .next day i install ubuntu 12.04 lts but during installation it get freezed on installing system process plz help me out from this issue plz

---

### Post by heir4c on 2013-11-10
What hardware have you? CPU, RAM, graphics card ... ?

---

### Post by Bucky Ball on 2013-11-10
You need to provide a LOT more info than that. Unfortunately, we are not psychic. ;)

---

### Post by sunnysanchit99 on 2013-11-10
my laptop configuration is
RAM-8GB
HARD DISK-300 GB
PROCESSOR-AMD A6-5350M APU with Radeon(tm) HD Graphics × 2
OS-UBUNTU 12.04 64 Bit
plz do some guys

---

### Post by Bucky Ball on 2013-11-10
What happens when you boot? Are you trying to dual-boot with Windows? Details of the error? As I say, we can't help you much unless you help us. Provide as much information about what you've done, if anything, to try and fix this and what exactly is happening when you boot the machine.

---

### Post by sunnysanchit99 on 2013-11-12
when i install ubuntu 12.04.3 lts every thing going perfect but at the end when the installing system process starts it freezes ,i wait for finishing the process but nothing happens.this error occurs:-

(WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx)


 and all expermental process also shows error that could not found update plz do some thing i m in lot of depression.thanks in advance

---

### Post by Bucky Ball on 2013-11-12
That is an issue with graphics. From what you're saying you can't install Ubuntu. So, when you get to the screen that says 'Try Ubuntu' 'Install Ubuntu' etc., hit F6 and you will get some options. Choose the 'nomodset' option. Proceed.

I am still a bit confused, though, if you mean Ubuntu gets through the install process but when it reaches the end, it stalls and then you get the error messages. Either way, graphics problem. If you have installed and it hangs, restart the machine and what happens then? Do you get to a screen where you can select OSs, you click Ubuntu and then it hangs?

If so, choose the Ubuntu you want to boot, hit 'e' to edit the kernel line, find the line that ends in 'quiet' 'splash' or both word and at then end of that line add 'nomodset'. 

Control+x to save and proceed with the boot. Good chance that will get you to a desktop.

I presume you have an ATI graphics card and the system is complaining it can't find the right driver. 'nomodset' gets past this issue nine times out of ten. ;)

---

### Post by sunnysanchit99 on 2013-11-14
thanks i will try this

---

