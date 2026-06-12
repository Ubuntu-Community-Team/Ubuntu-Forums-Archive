---
title: "Ubuntu 9.10 Boot problem"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by bingo23 on 2010-04-13
Have been successfully running Ubuntu 9.10 for a week now with no issues whatsoever in Windows 7 (downloaded via wubi).
 
Today however when I am presented with the Wjndows 7 / Ubuntu options and I choose Ubuntu, ikt fails to boot and I am faced with the following Screen:-
 
Heading - GNU GRUB version 1.97~beta4
 
then - [ Minimal BASH-like line editing is supported. For this first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]
 
then - sh:grub>_
 
Any advice appreciated.

---

### Post by ubername on 2010-04-13
Try selecting the 'recovery' ubuntu option from the grub menu (assuming you didn't disable the creation of recovery options) and then select the 'grub' option, which should reconfigure grub for you.

---

### Post by bingo23 on 2010-04-13
Do you mean type in 'recovery' alongside the prompt sh:grub>_
 
Thanks

---

### Post by bingo23 on 2010-04-13
If I TAB after sh:grub>_ I am presented with the following:-
 
Possible commands are:
. [badram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rmmod root save_env search set sleep source terminal_input.console terminal_output.console test unset
 
Any clues please

---

### Post by ubername on 2010-04-13
> **bingo23 said:**
> Do you mean type in 'recovery' alongside the prompt sh:grub>_
 
Thanks

Sorry. reboot the machine and when you get the menu that lets you choose ubuntu or windows there should be (at least) two options for ubuntu, one with (recovery) in brackets after it. Selecting that will take you to a text based menu where one of the options is 'grub'. Choose that.

---

### Post by robheus on 2010-04-13
> **ubername said:**
> Sorry. reboot the machine and when you get the menu that lets you choose ubuntu or windows there should be (at least) two options for ubuntu, one with (recovery) in brackets after it. Selecting that will take you to a text based menu where one of the options is 'grub'. Choose that.

I experienced the same kind of problem as described here.

However, I have two seperate menus: one for choosing between Windows or Ubuntu, and one for the Ubuntu installation.
That second menu is now gone, and I get the minimal Grub shell.

There is no recovery option there, I have to type the commands manually.

I only got so far as that the machine will boot into ubuntu, but then stops in the BusyBox because the root device can't be mounted or something.

What is my root device in a Wubi installation on the secondary partition (or perhaps this is a extended partition?).

---

