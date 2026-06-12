---
title: "Update from 11.04 to 11.10 errors.  Files not found Grub Rescue&gt; ?"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by JDulin on 2011-10-19
I recently tried updating from 11.04 to 11.10 (64-bit), originally by downloading and install 11.10 from within 11.04.  However, after restarting my computer I received a frozen error message that listed processes the computer tried to start.  Most of them were successful except for "Error reporting" and another, less important function.

I then tried to install Ubuntu 11.10 from a CD.  This installation went smoothly, but OS still will not boot properly, and instead gives me the message "Error: file not found" and the prompt "Grub rescue> ", since then I have tried another from CD install with different settings, and still receive the second error prompt.

Has anyone seen this problem before or know how it could be fixed?  I fear that the issue may be my SSD and not the software, although the SDD is only 4 months old.  My computer specs are:

Intel i7 CPU
8 GB RAM
1 TB Western Digital HDD (Windows)
60 GB OCZ Ability SDD (Ubuntu)
Nvidia 480 GPU

I would greatly appreciate any input!

---

### Post by coffeecat on 2011-10-19
Welcome to the forum!

The times I have seen an "Error: file not found" from grub is when I have added a custom grub entry and made a syntax or other error myself. That would not be the case here but, nevertheless, it would be a good idea to see all the grub configurations and other data to see why you are getting that error. Boot up the live Ubuntu CD, choose "try Ubuntu" to get to the live desktop, make sure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of your RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for readability. Hopefully, we'll be able to see what is wrong from that.

---

