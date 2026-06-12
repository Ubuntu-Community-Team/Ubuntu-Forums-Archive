---
title: "Fail loading linux (after feces upgrade) [yay pics]"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by boast on 2007-04-21
Upgraded from 6.10, Recovery mode or using old kernel versions doesn't work either. here are pics when I select different kernel versions/recovery.mode

[img]http://img261.imageshack.us/img261/7958/img0509ps8.jpg[/img]
[img]http://img249.imageshack.us/img249/8591/img0510aq8.jpg[/img]
[img]http://img124.imageshack.us/img124/2392/img0504af8.jpg[/img]
[img]http://img69.imageshack.us/img69/197/img0501pb5.jpg[/img]

---

### Post by boast on 2007-04-21
ok, I figured it out. 

Fiesty = my GF2 PCI video card isn't supported anymore, and decides to spit it out tons of errors with it installed.  wtf?!

---

### Post by boast on 2007-04-22
bump

TTT

---

### Post by boast on 2007-04-24
last hopeful bump

---

### Post by boast on 2007-04-26
ok, feeling optimistic today. bump :)

---

### Post by boast on 2007-04-28
bump

---

### Post by lame_duck on 2007-04-28
Can you boot to bash and install the GF2 drivers for Linux from the nVidia site?

---

### Post by boast on 2007-04-28
with the card installed, no.

---

### Post by RAKninja on 2007-04-28
you got an integrated gfx chip?  whith my bios set to PCI controlled i get the same errors, and about the same help as you've been getting.

---

### Post by boast on 2007-04-29
my integrated chip is the intel i810 or w/e. I'm trying to get my geforce2 pci to work.

bump^

---

### Post by boast on 2007-05-03
bump

---

### Post by boast on 2007-05-06
bump

---

### Post by boast on 2007-05-11
bump

---

### Post by boast on 2007-06-07
bump

---

### Post by boast on 2007-06-09
bump

---

### Post by boast on 2007-06-12
bump

---

### Post by stchman on 2007-06-12
> **boast said:**
> Upgraded from 6.10, Recovery mode or using old kernel versions doesn't work either. here are pics when I select different kernel versions/recovery.mode

[img]http://img261.imageshack.us/img261/7958/img0509ps8.jpg[/img]
[img]http://img249.imageshack.us/img249/8591/img0510aq8.jpg[/img]
[img]http://img124.imageshack.us/img124/2392/img0504af8.jpg[/img]
[img]http://img69.imageshack.us/img69/197/img0501pb5.jpg[/img]

My old GF2 GTP AGP works well with clean install of Feisty.  When you say upgraded did you do clean install or upgrade manager?

I have never had any luck with upgrades I prefer clean install.

---

### Post by boast on 2007-06-12
upgrade manager.

i wish the computer had an agp slot :(

---

### Post by stchman on 2007-06-13
> **boast said:**
> upgrade manager.

i wish the computer had an agp slot :(

I recommend you do a clean install.  I tried the upgrade manager path and it was nothing but problems for me.  That PCI GF2 should work the same as my AGP model did.

Remember that for the GF2 cards you need to use the nvidia legacy drivers.  When you are done installing Feisty use these commands.  Feisty's restricted driver for nvidia is somewhat hit or miss for older legacy cards.

sudo apt-get install nvidia-glx-legacy
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable


I have a procedure on my site that deals with ATI and Nvidia drivers.

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

Hope this helps.

---

