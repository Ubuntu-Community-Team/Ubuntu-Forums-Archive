---
title: "this kernel requires the following features not present on the CPU: 0:6"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by ab1301 on 2008-08-30
I am trying to install ubuntu server edition on my old laptop.  I looks like ubuntu server edition is not compatible with pentium m?  In any case, other sites say you have to use "rescue broken system" on install cd, then install generic kernel.  When I tried that, it gave me five or six options to mount kernel on or something like that.  It looked like maybe the various partitions?  I didn't want to go any further, because I have dual boot, and I don't want to screw up my windows partitions.  Will picking the wrong option potentially screw up the windows partition?  How am I supposed to know what option is what?

Is there an easier way of doing this?  Like is there a way to just burn a new cd with the correct kernel and re-install? (if so, where can I get a version that works?)

---

### Post by doggerus on 2008-08-30
click the pae/nx box

---

### Post by ab1301 on 2008-08-31
where can I find the pae/nx box?  Is that an option that appears when you initially install? when you run the rescue disk? or what?  I have never seen any such box.

---

### Post by modmadmike on 2008-09-02
He means in the VirtualBox config, because you usually get this error when running it in a virtual machine. However, it seems you are not running it virtually but in fact are running it directly which means it just does not support you cpu. Unfortunately that means you can only run the "Generic" kernel which is found on the Desktop edition only (but it can be installed in the server edition I think, but you need to get to a terminal which you can't because it wont boot) :(

---

### Post by schmoeleco on 2009-01-21
In the main window of VirtualBox.  Click on settings.  In the Linux Settings window that pops up,  General selection on the left, click the Advanced tab on the right.  Enable PAE/NX is in the middle of the window in Extended Features.

---

### Post by csiepka on 2009-02-06
> **schmoeleco said:**
> In the main window of VirtualBox.  Click on settings.  In the Linux Settings window that pops up,  General selection on the left, click the Advanced tab on the right.  Enable PAE/NX is in the middle of the window in Extended Features.

Thanks you fixed my problem!

---

### Post by Alexander Grundner on 2009-02-17
> **schmoeleco said:**
> In the main window of VirtualBox.  Click on settings.  In the Linux Settings window that pops up,  General selection on the left, click the Advanced tab on the right.  Enable PAE/NX is in the middle of the window in Extended Features.

I'm running into the same problem and tried finding the PAE/NX function to enable but it's missing from my version of VirtualBox OSE (1.5.6_OSE). My choices in the Advanced tab for Extended Features are the following:
[X] Enable ACPI
[ ] Enable IO APIC
[X] Enable VT-x/AMD-V

Trying to boot: Ubuntu 8.10 Server i386
Host PC: P4 3.0Ghz processor

---

### Post by Alexander Grundner on 2009-03-07
> **Alexander Grundner said:**
> I'm running into the same problem and tried finding the PAE/NX function to enable but it's missing from my version of VirtualBox OSE (1.5.6_OSE). My choices in the Advanced tab for Extended Features are the following:
[X] Enable ACPI
[ ] Enable IO APIC
[X] Enable VT-x/AMD-V

Trying to boot: Ubuntu 8.10 Server i386
Host PC: P4 3.0Ghz processor

Just a quick update...

I upgraded my host PC to Ubuntu 8.10 (previously 8.04) and installed VirtualBox OSE from the repo and it included the PAE/NX option. Works as advertise! No more errors. Thanks guys.

---

### Post by motapa on 2009-08-12
This solved my problem too. Please mark this thread as solved.

---

### Post by eric3_14159 on 2012-02-12
Just an update for anyone who, like me, runs across this in 2012 from a Google search:

In Ubuntu 11.04, with VirtualBox Graphical User Interface Version 4.0.4_OSE r70112, the pae option can now be found by selecting the virtual machine image needing the configuration, clicking the "Settings" button, clicking "System" in the left-hand bar, and selecting the "Processor" tab in the right pane. There should be an "Enable PAE/NX" checkbox below the processor slider.

---

### Post by oldos2er on 2012-02-12
Closed, necromancy.

---

