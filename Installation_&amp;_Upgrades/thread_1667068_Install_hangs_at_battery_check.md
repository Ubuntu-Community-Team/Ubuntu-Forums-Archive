---
title: "Install hangs at battery check"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by TechieSteve on 2011-01-14
Hi all!

I'm trying to install 10.10 to my very old 1GHhz Athlon based desktop machine, but when I boot with the CD in the drive, the machine just hangs at the 1st screen.

Pressing Esc during boot to see what is going on, I find that the boot always gets as far as:
"Checking battery status..."

As a desktop machine, it doesn't even have a battery. Is there anything I can do about this? Can I disable this check?

The CD worked fine in a work machine (and quite nice it looked too btw!)

Many thanks guys

Steve

---

### Post by gordintoronto on 2011-01-14
It's the video adapter, not the battery. (And your computer does actually have a battery, which keeps the clock running when it is unplugged.)

You probably need to specify a boot parameter. See:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gordintoronto on 2011-01-14
It's the video adapter, not the battery. (And your computer does actually have a battery, which keeps the clock running when it is unplugged.)

You probably need to specify a boot parameter. See:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gordintoronto on 2011-01-14
It's the video adapter, not the battery. (And your computer does actually have a battery, which keeps the clock running when it is unplugged.)

You probably need to specify a boot parameter. See:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by TechieSteve on 2011-01-15
> **gordintoronto said:**
> It's the video adapter, not the battery. (And your computer does actually have a battery, which keeps the clock running when it is unplugged.)

You probably need to specify a boot parameter. See:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Yes sorry, I forgot about that battery, but I assumed that the message was more likely to relate to the power source, such as in a laptop.

I think you are right in that it is not the battery state that is causing the problem, as I used a boot option to disable the battery state check, and it just hung at another point instead.

What leads you to think video adaptor? 

I tried several of the common boot option described in that link, but none seemed to work.

What else could I try guys?

Is it worth trying to update my (very old) bios?
And if its a video adaptor problem, is at maybe also worth updating my video card bios if possible?

Many thanks guys

Steve

---

### Post by TechieSteve on 2011-01-15
> **gordintoronto said:**
> It's the video adapter, not the battery. (And your computer does actually have a battery, which keeps the clock running when it is unplugged.)

You probably need to specify a boot parameter. See:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Yes sorry, I forgot about that battery, but I assumed that the message was more likely to relate to the power source, such as in a laptop.

I think you are right in that it is not the battery state that is causing the problem, as I used a boot option to disable the battery state check, and it just hung at another point instead.

What leads you to think video adaptor? 

I tried several of the common boot option described in that link, but none seemed to work.

What else could I try guys?

Is it worth trying to update my (very old) bios?
And if its a video adaptor problem, is at maybe also worth updating my video card bios if possible?

Many thanks guys

Steve

---

### Post by TechieSteve on 2011-01-15
> **gordintoronto said:**
> It's the video adapter, not the battery. (And your computer does actually have a battery, which keeps the clock running when it is unplugged.)

You probably need to specify a boot parameter. See:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Yes sorry, I forgot about that battery, but I assumed that the message was more likely to relate to the power source, such as in a laptop.

I think you are right in that it is not the battery state that is causing the problem, as I used a boot option to disable the battery state check, and it just hung at another point instead.

What leads you to think video adaptor? 

I tried several of the common boot option described in that link, but none seemed to work.

What else could I try guys?

Is it worth trying to update my (very old) bios?
And if its a video adaptor problem, is at maybe also worth updating my video card bios if possible?

Many thanks guys

Steve

---

### Post by TechieSteve on 2011-01-15
Sorry for the multiple post guys, I seem to be having a problem with posting to the forum

Steve

---

### Post by gordintoronto on 2011-01-15
It's possible that the problem is one of these:
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) 

Experience says, it's usually the video adapter -- not that it is bad or out of date, just that it's not well supported in Ubuntu. Especially with very old video adapters.

By the way, everyone is having trouble posting to the forums, it's not just you.

---

