---
title: "Failed bootloader after installing ubuntu"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by magda2 on 2015-11-11
Hi,

first I've installed Windows 7, then Ubuntu. After restarting I got  "grub resuce> ", so that I run ubuntu Live CD, installed via terminal boot-repair and run "recommended repair". 
After restarting my laptop still got "grub rescue > "

My log is here: [http://paste.ubuntu.com/13230601/](http://paste.ubuntu.com/13230601/)

I would appreciate any help/hints how to deal with it.

Magda

---

### Post by michele19 on 2015-11-22
I am having the same problem too. Did you ever figure out the problem and get it fixed?

---

### Post by oldfred on 2015-11-23
You show grub 2.00 installed, unless script parses MBR incorrectly.
And Boot-Repair says it installed 2.02.
Are you using the same live installer version as you have installed? 14.04?
And I have the original 14.04 without the LTS Enablement stack to get newer kernels, but my version is still shown as 14.04.3. You are showing 14.04.1, so was your system updated?
I also have  3.13.0-68-generic, but yours shows -32 as most current?

I would use Boot-Repair's advanced mode and run the full uninstall/reinstall of grub2. I think that also updates to newest kernel, but you may have to check a box to have it do it.

---

