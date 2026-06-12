---
title: "Is there a way to downgrade feisty kernel to 2.6.17 from edgy"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Saubazi on 2007-04-26
I noticed that I still had a boot option of old edgy kernel after the upgrade.
I am not too happy with Feisty and 2.6.20 - the joystick driver is broken and
it effectively screwed my gaming totally. Where there was 20+ button Saitek stick
it now only sees 16 buttons and mixes them with each other so I think I'd be better off
with old kernel but how do I accomplish that?

I mean I booted into it but then X would not start since the nvidia drivers do not match
I tried to install old linux-headers from package and install the version of nvidia-drivers
the x seemed to be missing but it did not work. Finally even 2.6.20 had problems starting
X - I removed and reinstalled something and then I at least got that one up, but I would not
like to give up that easy. 

Does anyone know how to get back to earlier kernel?

---

### Post by zvacet on 2007-04-26
[http://ubuntuforums.org/showthread.php?t=424316]("http://ubuntuforums.org/showthread.php?t=424316")

---

### Post by Saubazi on 2007-04-27
Well I am not really interested in compiling a vanilla kernel for me - I am more interested in running the existing older kernel 2.6.17 instead of the new 2.6.20 from feisty. It boots and all - only X won't start - it is complaining about the nvidia module being wrong version (older than the one required by xorg) - so I'd like to fix this not really the kernel bit...

---

### Post by H.E. Pennypacker on 2007-05-08
I am interested in this too.  I am having a hardware, though not the same, issue also.

> **zvacet said:**
> [http://ubuntuforums.org/showthread.php?t=424316]("http://ubuntuforums.org/showthread.php?t=424316")

That links to the Master Kernel Thread, which deals with compiling custom kernels.  The original poster/thread starter never asked for how to compile a custom kernel.  We're only interested in moving back several versions.

---

### Post by zvacet on 2007-05-08
I don´t know.Try to upgrade video drivers.

---

### Post by Topsiho on 2007-05-08
I am not sure I understand your problem :confused: 

When upgrading to a new kernel the old kernel remains in the grub menu and can still be selected. Just in case the new kernel does not work as hoped, on your computer.

That is exactly what you write:

"I noticed that I still had a boot option of old edgy kernel after the upgrade."

So why do you not use that kernel?

If I have not understood what you are asking ( I read it several times) I apologize ....

Topsiho

---

### Post by H.E. Pennypacker on 2007-05-08
I did a clean install.  There is no other kernel installed.

---

### Post by Topsiho on 2007-05-10
Sorry, I was reacting to Saubazi's remark "I noticed that I still had a boot option of old edgy kernel after the upgrade."

And of course I assume that if you do an upgrade, even to a newer version, that the old kernels still work, if they are still there in Grub, otherwise there is a critical bug to be reported :)

Topsiho

---

