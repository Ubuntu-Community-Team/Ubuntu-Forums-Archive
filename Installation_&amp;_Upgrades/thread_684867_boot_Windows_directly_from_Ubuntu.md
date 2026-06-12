---
title: "boot Windows directly from Ubuntu"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by pytheas22 on 2008-02-01
I apologize if this is not the right forum for this question.  I also understand that this is not an Ubuntu-specific question, but since I always get excellent help on these forums, I wanted to ask here before trying someplace else.

I would like to employ the following scenario:

1. I take a computer with Windows XP already installed, and encrypt its entire hard drive using Truecrypt.  I also set up a grub entry for the XP partition.
2. I install a minimalist Linux distribution to a USB flash drive and boot the machine to that.
3. once Linux boots, a script is run to mount the XP partition using Truecrypt (the user would have to enter a Truecrypt password first, obviously).
4. If the password is correct, the XP partition gets mounted, and the computer then boots to the XP system with a command like

```
$ grub_reboot [Windows entry number]
```

5.  Else the computer reboots/asks for the Truecrypt password again, or whatever.

The crucial issue, as I see it, is whether or not the XP partition will remain unencrypted even while the machine is rebooting from Linux to Windows.  I think this would depend on precisely how the grub reboot command works: will the operating system be totally shut down and Truecypt disabled, or will the XP partition remain unencrypted throughout the reboot and hence accessible?

If anyone has suggestions on whether or not this would work, or another way to workaround the possibility of the XP partition getting reencrypted during reboot, please let me know.

Thanks in advance for any help.

EDIT: I've thought this through more and talked with some people and have realized that it probably wouldn't work, because at some point the Linux kernel would be replaced by the XP kernel, killing Truecrypt.  However, using something like xen to run XP on top of Linux would probably work, right?

---

### Post by dfarce on 2008-02-02
I am by far a complete noob coming to anything linux or unix, but I think that it wouldn't work because as you said, as soon as you boot Xp, truecrypt would be terminated. Your workaround with Xen would probably work, but then you have the problem of dealing with a VM. What I would suggest is to use vista [/shiver] and use the drive encryption feature. Which versions actually work with it you'll have to research, but that would probably be the easiest, most pain free, and fastest way to get what you want.

---

### Post by Julita on 2008-02-02
I think that the easiest way is to use VirtualBox.

---

### Post by Craigus on 2008-02-02
> will the XP partition remain unencrypted throughout the reboot and hence accessible?

It won't, because it is never unencypted - the Truecrypt driver does the encyption work on-the-fly.

Once you reboot into another OS, that driver is not longer running.

Have a look at Compusec - it's free:

[http://www.ce-infosys.com/english/downloads/free_compusec/index.html]("http://www.ce-infosys.com/english/downloads/free_compusec/index.html")

---

### Post by pytheas22 on 2008-02-02
Thanks for the responses.  CompuSec looks like it might do exactly what I need; I'll check it out more.

> What I would suggest is to use vista [/shiver] and use the drive encryption feature

Unfortunately the computers I'm working with all run XP and won't be upgraded to Vista for an indefinite amount of time.  XP also has built-in encryption called EFS, but it's tied to the Windows account password, which is easy to crack, and I was also able to recover some EFS-"encrypted" files just by using forensics disaster recovery tools like photorec.  Vista's Bit Locker hopefully works better, but it's not an option right now.

Xen would probably work too but I think it's only supported on relatively modern hardware, and it's still not as stable as I would like.  So I'll check out CompuSec.

---

