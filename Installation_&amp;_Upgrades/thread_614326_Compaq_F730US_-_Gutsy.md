---
title: "Compaq F730US - Gutsy"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by mschap on 2007-11-15
Okay, I just bought a Compaq F700 series (F730US) laptop.  It has an AMD 64 (Athalon x2) and NVidia for graphics.  I have tried 7.10 both the 64 bit and 32 bit version, regular and safe graphics.  As it boots and loads it doesn't give me the wonderful "live session screen" but rather a bunch of black and white lines.

Question, can I install 7.10 on this thing, and if so how?
Question, should I just return it to Office Depot?

Any suggestions are appreciated and I have limited experience with the install of linux.

Thanks.

---

### Post by Pza3.14159 on 2007-11-16
I have the same machine. I can't take credit for the answer. If I recall correctly you need to add one or both of these boot flags: noapic acpi_os=name="Linux"
I have Gutsy 64 bit (mostly) successfully installed alongside Vista (which I now never use). 
Check the forums for info on the F572US as well. It may take a while to boot so don't despair.

Good luck.

[NOTE: the acpi_os=name="Linux" flag may be unnecessary, at least after install. It may also prevent your USB devices from hotplugging (my USB devices wouldn't hotplug, so I removed the acpi flag and hotplugging started working fine...).]

---

### Post by ZanexGt on 2007-12-18
> **mschap said:**
> Okay, I just bought a Compaq F700 series (F730US) laptop.  It has an AMD 64 (Athalon x2) and NVidia for graphics.  I have tried 7.10 both the 64 bit and 32 bit version, regular and safe graphics.  As it boots and loads it doesn't give me the wonderful "live session screen" but rather a bunch of black and white lines.

Question, can I install 7.10 on this thing, and if so how?
Question, should I just return it to Office Depot?

Any suggestions are appreciated and I have limited experience with the install of linux.

Thanks.

Since your post was 4 weeks ago, I am assuming that you either fixed this problem or gave up. However, I thought I might help you out incase you are still struggling with this problem. 

You can install Gutsy 7.10 on the Compaq F730US without too much trouble.

I had the same problem as you. I would boot up 7.10 Gutsy using the LiveCD or my fresh install and would end up getting the black/white lines you mentioned. In order to fix this, I set the &#8220;noapic&#8221;, sans parenthesis, to the boot loader. 

To do this:
1. .When loading via the LiveCD, hit F6 for more options to add the parameter above.
2. When loading on a fresh install, (first load using the LIVECD AFTER you have installed a fresh copy of Ubuntu. Then, go into your filesystem and edit menu.lst to add the parameter permenantly to the boot loader.

---

### Post by asmodaous on 2007-12-23
How do you remove the acpi flag. I am having trouble trying to do that....HELP!!!

---

### Post by ZanexGt on 2007-12-23
> **asmodaous said:**
> How do you remove the acpi flag. I am having trouble trying to do that....HELP!!!


Chek out this thread for my post on how to remove the noapic flag. If you need to remove the acpi flag, it'll be the same instructions, just a different flag. 

enjoy

---

### Post by Bannor on 2008-01-24
how did you get the wireless to work????

---

### Post by ZanexGt on 2008-01-27
> **Bannor said:**
> how did you get the wireless to work????

Bannor, check out [this](http://ubuntuforums.org/showpost.php?p=4009618&postcount=26) post for info on getting WIFI setup.

---

