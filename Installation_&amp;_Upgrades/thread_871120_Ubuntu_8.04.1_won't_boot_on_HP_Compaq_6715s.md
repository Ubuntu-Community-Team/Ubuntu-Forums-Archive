---
title: "Ubuntu 8.04.1 won't boot on HP Compaq 6715s"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by use_R on 2008-07-26
I installed Ububntu 8.04.1 on HP Compaq 6715s with certain interventions (I selected noapic, nolapic, acpi=off during the installation).

But now it won't boot.:guitar:
 
Some useful tip please? Tnx.

---

### Post by Pumalite on 2008-07-26
These links might be useful:
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by use_R on 2008-07-28
Again was alone and found some company, as well as an answer :n) - I have edited /boot/grub/menu.lst file with additional parameters (noapic nolapic acpi=off) at the end of of a line that begins with "# defoptions=". NOw it boots, as well as new problem came - won't shut down (a screen with Ubuntu logo freezes during shut down....). Btw, restart works (no freeze with Ubuntu logo on the screen). I will wait for some tip :).

---

### Post by PmDematagoda on 2008-07-28
About the shutdown problem, it probably is because you turned ACPI off, remove the acpi=off to see if Ubuntu boots up properly(it might) and shuts down properly as well.

---

### Post by use_R on 2008-07-28
I removed "acpi=off" from the file /boot/grub/menu.lst (line that begins with "# defoptions=") and rebooted. 

A good news is that it shuts down automaticaly now, but...

But now it boots very very slowly - during the phase when Ubuntu logo is on the screen, and after - during a message "* Preparing restricted drivers..." is on the screen, and during login. Whole boot lasts now 8minutes! I booted 2 times to check it. Also, some applications staring lasts longer than before (when acpi=off existed).

Is there more acceptible solution?

---

### Post by PmDematagoda on 2008-07-29
> **use_R said:**
> I removed "acpi=off" from the file /boot/grub/menu.lst (line that begins with "# defoptions=") and rebooted. 

A good news is that it shuts down automaticaly now, but...

But now it boots very very slowly - during the phase when Ubuntu logo is on the screen, and after - during a message "* Preparing restricted drivers..." is on the screen, and during login. Whole boot lasts now 8minutes! I booted 2 times to check it. Also, some applications staring lasts longer than before (when acpi=off existed).

Is there more acceptible solution?

You could try experimenting with the options(i.e. turn one off, then the other and so on).

If the above doesn't help, then I suppose you could compile a kernel of your own, but that's another story:).

---

### Post by use_R on 2008-08-09
I tried experimenting, but without success;
- with only "noapic" is turned on,
- with only "nolapic" is turned on,
- with them both turned on,
whatever the case the abovementioned sympthom of 8 minutes login occcured.
When I turned off both - noapic and nolapic - then it didn't boot.

Maybe I should wait for a new version-more adjusted to HP Compaq 6715s- because I thing that ad hoc kernel compiling is out of my knowledge and current inspiration:) scope. Anyway, thanks.

---

### Post by PmDematagoda on 2008-08-09
> **use_R said:**
> I tried experimenting, but without success;
- with only "noapic" is turned on,
- with only "nolapic" is turned on,
- with them both turned on,
whatever the case the abovementioned sympthom of 8 minutes login occcured.
When I turned off both - noapic and nolapic - then it didn't boot.

Maybe I should wait for a new version-more adjusted to HP Compaq 6715s- because I thing that ad hoc kernel compiling is out of my knowledge and current inspiration:) scope. Anyway, thanks.

Perhaps you could try a different distribution? I would recommend something like Fedora.

---

### Post by toocer on 2008-09-20
I dont like the idea of installing another dist but there must be a good solution for this ?

I have read this and tried it, but i still havent got to work as i want it to.

I dont like to mess up things in the boot, isnt there any way to solve this acpi problem ? with a new kernel ? or is it a bigger problem ?

---

### Post by misiek_b on 2008-09-20
Hi, I have hp 6715s with sempron. In order to ubuntu boots corect I had to add parameter to kernel: acpi=off noapic, so obviously system didn't shutdown. Today I changed "acpi=off noapic" to "nohz=off" (I don't remember, where I read this) but it works. System boots corectly and what is good I have acpi.

---

### Post by toocer on 2008-10-10
> **misiek_b said:**
> Hi, I have hp 6715s with sempron. In order to ubuntu boots corect I had to add parameter to kernel: acpi=off noapic, so obviously system didn't shutdown. Today I changed "acpi=off noapic" to "nohz=off" (I don't remember, where I read this) but it works. System boots corectly and what is good I have acpi.

Iam trying this at this moment, and as so far it looks Great..

If i find any problems i will tell ;)

---

### Post by toocer on 2008-10-10
It wooorks.. nohz=off and using this [link]("http://ubuntuforums.org/showthread.php?t=880218&highlight=4312") for the wireless \\:D/

---

