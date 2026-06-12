---
title: "No boot, no recovery mode"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by paglia96 on 2009-12-15
When i try to boot the normal boot or the recovery mode [IMG]http://www.google.it/images/cleardot.gif[/IMG]Visualizza caratteri romani
appears an message 
fcsk or similar and then block....

Why?

---

### Post by zeroandone on 2009-12-15
When did it start? After the fresh install?

---

### Post by paglia96 on 2009-12-15
> **zeroandone said:**
> When did it start? After the fresh install?
No, after the fresh install (the daily version of today) i installed the update them i rebooted and i installed the drivers nvidia for the graphic them when i rebooted i received the message

---

### Post by vade on 2009-12-15
Does the system respond to alt-sysrq-REISUB?

---

### Post by zeroandone on 2009-12-15
> **paglia96 said:**
> No, after the fresh install (the daily version of today) i installed the update them i rebooted and i installed the drivers nvidia for the graphic them when i rebooted i received the message

You didn't perform any Partial Upgrade or remove any packages, did you?

---

### Post by trulan on 2009-12-15
It's the nvidia drivers.  Somebody really needs to fix this problem!

You'll need to boot from a live cd and set your computer to use the vesa drivers for now.

---

### Post by gnomeuser on 2009-12-15
> **trulan said:**
> It's the nvidia drivers.  Somebody really needs to fix this problem!

You'll need to boot from a live cd and set your computer to use the vesa drivers for now.

For once it is actually not the nvidia drivers, well it is but only because they need dkms. There is a line missing in dkms-installer which causes this (please look at my previous posting in the other thread on this for the solution).

---

### Post by paglia96 on 2009-12-16
> **zeroandone said:**
> You didn't perform any Partial Upgrade or remove any packages, did you?
No i didn't

So the problem are nvidia drivers or the dkms?

Scuse me me for my bad english, i'm italian ;)

---

### Post by vikrant82 on 2009-12-16
Try adding nomodeset to kernel line. I had a similar issue. Once booted I updated available packages and the boot up issue was gone.

---

### Post by paglia96 on 2009-12-17
> **vikrant82 said:**
> Try adding nomodeset to kernel line. I had a similar issue. Once booted I updated available packages and the boot up issue was gone.

How can i add nomodeset?

---

### Post by VMC on 2009-12-17
> **paglia96 said:**
> How can i add nomodeset?

When you get the grub menu, push 'E' then edit the linux line. 
At the end of the line add nomodeset. Then Ctrl+X to boot.

---

### Post by paglia96 on 2009-12-17
> **VMC said:**
> When you get the grub menu, push 'E' then edit the linux line. 
At the end of the line add nomodeset. Then Ctrl+X to boot.
Ok, y tried but there are many lines, in what i musat add nomedeset?

---

### Post by zika on 2009-12-17
> **paglia96 said:**
> Ok, y tried but there are many lines, in what i musat add nomedeset?The one starting with "linux" ... one before the last.

---

### Post by paglia96 on 2009-12-18
Don't change anything :-(

---

### Post by VMC on 2009-12-18
> **paglia96 said:**
> Don't change anything :-(

Remove "quite" & "splash", if its on the "linux" line, and have only "nomodeset" after "ro". For example:

```
linux /vmlinuz root=UUID=51d4bcac-151a-44a7-9578-9461042679c7 ro nomoeset
```

Then reboot and look at the output being displayed on your screen. Look for any errors.

---

### Post by paglia96 on 2009-12-19
> **VMC said:**
> Remove "quite" & "splash", if its on the "linux" line, and have only "nomodeset" after "ro". For example:

```
linux /vmlinuz root=UUID=51d4bcac-151a-44a7-9578-9461042679c7 ro nomoeset
```Then reboot and look at the output being displayed on your screen. Look for any errors.
There aren't any error

---

