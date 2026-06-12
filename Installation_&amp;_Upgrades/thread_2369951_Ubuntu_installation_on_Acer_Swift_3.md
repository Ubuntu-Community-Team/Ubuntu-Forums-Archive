---
title: "Ubuntu installation on Acer Swift 3"
date: 2017-08-28
forum: Installation &amp; Upgrades
---

### Post by nicosoria on 2017-08-28
Hi there!
I am not new using Ubuntu but I am new working with laptops.

Recently, I've installed Ubuntu on my new Acer Swift 3, with the following conclusions and concerns:
[LIST]
[*]Even I've read a lot of post that somehow the laptop is not compatible with Ubuntu 16.04.3 LTS, so far so good. I only updated the BIOS to the latest version (1.05).
[*]It came with Windows 10 and I made an installation without delete Win10, but two concern came up:
[LIST=1]
[*]Somehow the grub menu works fine with Ubuntu, but when I enter to Windows, it reboots the laptop and go directly to Windows, Is this something that can be fixed?
[*]Do you know if warranty is lost if I make a full installation of Ubuntu?
[/LIST]

[*]Following the point that in Internet, the laptop is being shown as non-compatible with Ubuntu. Does somebody know if there are still compatibility issues?
[/LIST]

I would really appreciate your response, and sorry for my bad english!

Thanks,
Nicolás.

---

### Post by gordintoronto on 2017-08-29
The Swift 3 is a family of computers with varying specs. Do you know what CPU, memory and video yours has?

---

### Post by nicosoria on 2017-08-29
Hi! Thanks for your reply.

Below are the specs:

Windows 10 Home
Intel® Core&#8482; i5-7200U Dual-core (2 núcleos) 2,50 GHz
8 GB, DDR4 SDRAM
256 GB SSD

Model is Swift 3 SF314-52.

Thanks,

---

### Post by gordintoronto on 2017-08-29
With a computer that new, I would suggest Ubuntu 17.04. In a few months, you will need to upgrade to 17.10, and next year, 18.04 -- which will be a long-term release, so you can get off the treadmill.

Acer might not provide warranty service if Ubuntu is the only OS. I'm not sure about this.

---

### Post by abied on 2017-08-29
For number 1. you must turn off fast boot in Win 10; goto setting - power option and uncheck fasboot. And you must install grub in /dev/sda. not sda1.

For 2. warranty Win10 maybe will be lost. but warrant laptop/hardware maybe no. its MAYBE. :)

---

