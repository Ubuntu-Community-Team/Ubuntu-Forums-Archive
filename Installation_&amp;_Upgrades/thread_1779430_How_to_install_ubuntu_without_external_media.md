---
title: "How to install ubuntu without external media?"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by Jgke on 2011-06-10
So, my problem is that I don't have any CD's, my USB stick is missing and I don't want to have a WUBI-retarded system. I saw something about a 'frugal install' but can I move from it to an actual install, and how?

---

### Post by ppv on 2011-06-10
You may have to search out for ways to do it but you can install over a network, if you have such a setup. If your computer does have a card reader and it supports booting from it, you could use a memory card too.

---

### Post by coffeecat on 2011-06-10
Is your machine a desktop or laptop? Can you physically remove the hard drive? Are you prepared to do so? Do you have another machine from which you can boot a USB or CD which can temporarily house the hard drive from your first machine?

If the answer to all these is yes then you can use another machine - even one with different hardware - to install Ubuntu and then transplant the HD back into its own machine. You may see some posts that say that this is not possible because of hardware/driver differences. This is simply not so. The Ubuntu kernel autodetects hardware on boot up and automatically loads the appropriate kernel modules (drivers). The only things you need to beware of are:

1 - Don't install any proprietary video drivers until the HD is back in the machine in which it belongs.

2 - You need to be careful where grub is installed. I can't say any more until I know the exact setup you are likely to use.

3 - If your permanent machine is 32-bit and the host machine 64-bit, don't make the mistake of using a 64-bit install medium.

If you want to know more, post back with those answers.

---

### Post by Jgke on 2011-06-10
Good idea about that card reader, didn't think of it myself... But the problem is that the card reader slot in my computer is too big for my phone's card and I don't have the adapter... Looked a bit through the network installing and that looks a bit too complicated for me.

Ah, coffecat ninja. I'm using a laptop with a cd drive and it does support USB booting, but the problem is that I don't have the stick itself nor a CD.

---

### Post by Joe of loath on 2011-06-10
Maybe go out and buy a stack of CD-Rs? They're cheap, and you'll remember everything you needed to burn after a few days :D

---

### Post by coffeecat on 2011-06-10
Sorry. Misread your first post to mean that you couldn't boot CDs or USBs, not that you didn't have any.

Forget everything I posted.

---

### Post by ppv on 2011-06-10
> **Jgke said:**
> Good idea about that card reader, didn't think of it myself... But the problem is that the card reader slot in my computer is too big for my phone's card and I don't have the adapter... Looked a bit through the network installing and that looks a bit too complicated for me.

Ah, coffecat ninja. I'm using a laptop with a cd drive and it does support USB booting, but the problem is that I don't have the stick itself nor a CD.

When connected to the computer with a cable do you see your phone as "Removable media". Then you can try to boot from it with the card in the phone itself. Before writing to the card you might want to make a backup of your files on the card.

---

### Post by ppv on 2011-06-10
> **Jgke said:**
> So, my problem is that I don't have any CD's, my USB stick is missing and I don't want to have a WUBI-retarded system. I saw something about a 'frugal install' but can I move from it to an actual install, and how?

Or you may install it using Wubi and then move it to a partition as a regular install.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Jgke on 2011-06-10
So you mean that by migrating the wubi to another partition it would be a standalone operating system? Yeah, right.
(Memory card through phone didn't work)

---

### Post by wildmanne39 on 2011-06-10
> **Jgke said:**
> So you mean that by migrating the wubi to another partition it would be a standalone operating system? Yeah, right.
(Memory card through phone didn't work)
Hi, yes you can migrate a wubi install if you have a wubi install here is the guide.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Jgke on 2011-06-11
The 20GB partition I reserved for Ubuntu is mounted, while umount states that it is not...

After trying a reboot, my system now seems have it's MBR destroyed. Time to search for CD's...

E: Hah, it seems that I find things not when I want them, but when I need them...
What's the command to repair the MBR?

---

