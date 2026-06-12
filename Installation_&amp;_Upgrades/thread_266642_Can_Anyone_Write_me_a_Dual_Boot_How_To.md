---
title: "Can Anyone Write me a Dual Boot How To?"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Virtute on 2006-09-27
Alright, so heres the situation:

The machine I'm on right now is 100% Dapper Drake Ubuntu with default partitioning and GRUB bootloader settings.  I have a 200gig and all of it is currently being used for Ubuntu.  Things have come up recently and I've decided I need a small Windows partition anyway (for certain design programs and a few games).

Can someone give me a step by step guide on how to go from where I am now to having a dual boot between Ubuntu and Win2k/XP (haven't decided yet)?

Keep in mind that while I'm not a complete noob, if it's possible I like things explained to me.  For example, if you tell me to do something as vague as "Make a GRUB entry," I'll probably end up blowing up my tower.

Thank you in advance!

---

### Post by tagra123 on 2006-09-27
Not sure what software you are using. Have you consider the free VMWare Server or VmPlayer. 

The server makes the install of a new os very simple. There are how-to's in theis forum.

The install of windows takes a little longer than usual but if you have more than 256MB of ram you may consider using this.

I use it and its like have a ubuntu and windows on the same machine without dual booting.  Almost anything that can run on windows will work. DirectX (games) don't work the best yet but I believe I read somewhere that they are working on it,

---

### Post by ssalman on 2006-09-27
will [this ]("https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28dual%29")wiki page help?

---

### Post by pseudonym on 2006-09-27
Another, less risky, option would be to -

1. Buy a cheap 2nd-hand hard drive off ebay.

2. Unplug your linux drive temporarily.

3. Plug the 2nd drive into primary IDE master and install windows.

4. Unplug this drive and plug it into primary IDE slave.

5. PLug your linux drive back into primary IDE master.

6. Edit grub to include windows (I can show you how if necessary).

7. Reboot, and then choose either OS.

THis of course assumes you are using IDE drives. It's probably not economical with SATA. Although, you could still try with win on IDE/linux on SATA, but it has been known to be problematic.

---

### Post by Virtute on 2006-09-27
Well, I just found out that a Dapper Drake boot CD can resize partitions, so I'm all set with that, and I'm experienced enough to be able to install Windows to the freed up space.  I just have one more question;

How do I make a GRUB entry to boot to windows, and should I do this before or after I install Windows?

---

### Post by _teo_ on 2006-09-27
> **Virtute said:**
> How do I make a GRUB entry to boot to windows, and should I do this before or after I install Windows?

This is just an entry in GRUB config file:
/boot/grub/menu.lst

There is an example in that file (read comments), but it is like this:
```

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

```
The above will put an entry in GRUB menu.

It doesn't matter whether Windows is already installed. If not, you will end up rebooting.

---

### Post by _teo_ on 2006-09-27
> **Virtute said:**
> Well, I just found out that a Dapper Drake boot CD can resize partitions, so I'm all set with that, and I'm experienced enough to be able to install Windows to the freed up space.  I just have one more question;


Just one more thing: Windows installation will replace the boot loader in MBR. I don't know any way to prevent it from doing this.

---

### Post by pseudonym on 2006-09-27
Which, apart from the inherent risk of partition resizing,  is why a cheap second hard drive is a good option :)

---

### Post by _teo_ on 2006-09-27
> **pseudonym said:**
> Which, apart from the inherent risk of partition resizing,  is why a cheap second hard drive is a good option :)

Agree, this would be the best solution. Or he could start from scratch and install Windows first and then Ubuntu...

---

