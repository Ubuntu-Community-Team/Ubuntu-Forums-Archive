---
title: "ububtu not working"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by xcalibur32 on 2007-07-04
Hi,
I just installed ubuntu on vista machine (64 bit). The installation was ok. I created the partitons and after reboot, the grub would not load the kernel. It would crash. However I tried recovery mode and it was fine and in the command prompt, I typed startx and got a gui. But i think since it did login as admin., I could not get the system config etc.. Earlier, the live cd did not work for installation, so I had to use the alternate cd. 

I would appreciate if anybody could help me get this working

Thanks

---

### Post by robert@debian on 2007-07-04
As user "root" you should have access to all system conifguration files.
However, Ubuntu disabled by default user root.
Therefore your user "admin" should be prompted for a password when you try to access
the system config. 

Since you are new to Linux you may want to check this [**introduction**]("https://help.ubuntu.com/7.04/administrative/C/") about administrative tasks.

---

### Post by kevinlyfellow on 2007-07-04
Let's see your grub configuration.  Login using recovery and post your menu.lst.  You can enter this command to get it
```
cat /boot/grub/menu.lst
```

---

### Post by xcalibur32 on 2007-07-04
I tried booting from the live cd again and below is the error message I get,

MP-BIOS bug:8254 timer not connected to IO-APIC

kernel panic - not syncing :IO-APIC +timer dosenn't work! try using the 'noapic' kernel parameter



Any fixes?

Thanks

---

### Post by kevinlyfellow on 2007-07-04
> **xcalibur32 said:**
> I tried booting from the live cd again and below is the error message I get,

MP-BIOS bug:8254 timer not connected to IO-APIC

kernel panic - not syncing :IO-APIC +timer dosenn't work! try using the 'noapic' kernel parameter



Any fixes?

Thanks

It's been a while since I booted an ubuntu cd and I don't have one on hand, but most cds will have a prompt that says
```
boot:
```
In there type something like
```
ubuntu noapic
```
or
```
linux noapic
```
or even
```
noapic
```

---

