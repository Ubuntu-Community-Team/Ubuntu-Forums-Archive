---
title: "Windows 8.1 with UEFI and Ubuntu 14.10 dual boot grub error after factory reset"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by bob_smith3 on 2015-05-14
Hi all;
Recently, my Lenovo G50-45 on the Windows 8.1 partition was infected with a stubborn rootkit, which opened many backdoors in the system, and dropped off many sorts of malware. I decided to completely restore the computer to the factory settings, instead of dealing with each piece of malware at a time. So I erased the Ubuntu partition, and followed the procedure in Windows 8.1, to factory reset the computer (including reformatting all drives). However, during the factory reset process, Windows had restarted the computer, and it loaded into GNU Grub version 2.02~beta2-15. Now, I am stuck at a Grub screen which appears as follows:

```
                                                                                     GNU Grub version 2.02~beta2-15

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file
completions.

grub>


```

Since this machine came default with Windows 8.1 (With UEFI), I cannot access the BIOS at startup, I must go through Windows 8.1 (Security feature). None of the function keys work at startup.

So now, I have no operating system, and stuck at this GNU Grub screen.

All input as to how I can resolve this would be greatly appreciated.

Thanks!

---

### Post by oldfred on 2015-05-14
Did you have Ubuntu in UEFI mode or in BIOS/CSM mode?

Can you use one time boot key, often f10 or f12, but varies by vendor?

Some can get into UEFI/BIOS with total cold reboot. Power down, if laptop remove battery and hold power switch for 10 sec or so to remove all power left in system. Then reboot and immediately press correct key to get into UEFI.

My motherboard had settings for fast boot (not Windows fast startup). That included fast on cold boot, warm reboot and sec delay. So I set my system for full startup on cold boot which give me more time to get into UEFI and 3 sec delay on warm reboot. I then added 3 sec delay in grub menu. And that 6 sec is a lot of my reboot time, but necessary if I need to get into system.

---

### Post by bob_smith3 on 2015-05-14
Solution was simple as ever.
All I needed to type was a simple exit command, and it directed me straight to the bootloaders of Windows and Ubuntu. So I selected the Windows option and continued with the factory reset.
Thanks for your help!

---

### Post by Vladlenin5000 on 2015-05-15
Glad it works now.

If you need to access UEFI settings - actually a preboot menu with a few options including the settings and one time boot order - you need to press ESC during post.
In this case it wouldn't have helped though because you were already booting from the correct drive but because you deleted the Ubuntu partitions you somehow messed the bootloader. Probably a waste of time also, deleting the partitions: A full Windows recovery to factory defaults most likely would have done it for you.

---

### Post by mattharris4 on 2015-05-18
> **bob_smith3 said:**
> Solution was simple as ever.
All I needed to type was a simple exit command, and it directed me straight to the bootloaders of Windows and Ubuntu. So I selected the Windows option and continued with the factory reset.
Thanks for your help!

Out of curiosity what was the "simple exit command"?  Posting it may help others in the same situation.

---

### Post by Vladlenin5000 on 2015-05-19
> **mattharris4 said:**
> Out of curiosity what was the "simple exit command"?  Posting it may help others in the same situation.

exit

---

### Post by mattharris4 on 2015-05-20
^ Thank you.  I appreciate you posting the "simple exit command".  The way you wrote the sentence it wasn't clear (to me anyway) that the command was "exit".  Things aren't always that simple in computer land.

---

