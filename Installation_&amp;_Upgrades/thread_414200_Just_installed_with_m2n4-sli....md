---
title: "Just installed with m2n4-sli..."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by pross on 2007-04-19
Hope this post helps someone out there!

I just installed the new Feisty, and it looks very nice :D but i did have a number of issues...
 
in order to boot the liveCD i had to pass 'noapic' to the kernel at bootime..ok no biggy..Feisty failed to see my SATA drive..hmm oh well i installed to a IDE

next i boot into it again with noapic and decide to install the nvidia video driver to get the candy :) so i reboot when asked and yay! ..well almost..i have wobbly windows now...but no network! i checked DMESG and it appears the forcedeth module is crashing ...so i decided to try the timer cheatcode i found ages ago...


so now i boot with enable_8524_timer and EVERYTHING works now! ...sound... bluetooth... wobbly stuff...with no errors..

so if your using a M2N4-SLI which uses the NFORCE4 chipset try enable_8524_timer pci=biosirq

---

### Post by alejodan on 2007-11-21
Hi, I have the same hardware, but can't install ubuntu 7.10.
I can start the live version with noapic, but after that, when try to install, the installation process freezes at hardware detection.

Is there any tip in order to complete the installation just like you did?

Thanks in advance,
Alejandro

---

### Post by tim_c on 2007-12-20
Just installed without undue problems, 7.1 after suffering as you!

The answer us very simple if to me bizarre.

Default CD menu item, hit F6, edit out the word QUIET
And hit return. (literally that is all, no overrides)

If you have to reboot before the install is all complete you might have to edit the word out using the "e" to edit method as help prompts.

Finally.

After install you need to edit GRUB menu.lst to remove just the first instace of the word QUIET.
(or have to edit it out on every boot)

{goes away to let head cool down, muttering about mad "features"}

---

