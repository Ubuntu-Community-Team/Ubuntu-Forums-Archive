---
title: "Installing problems with TX 1000 series (tx1220), nvidia graphic card"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by WesleyWex on 2008-03-29
I've just finished installing Ubuntu 7.10 using alternate install CD, all the installation proccess was done with no problems, but the first boot gave me a black screen just after the orange load bar disappeared.

I tried to see what was going on by viewing the console during boot (Ctrl+Alt+F1). The screen disappears when something related to GDM is loaded. It's too fast, so I can't see what it is specifically.

Ctrl+Alt+Del and Ctrl+Alt+Backspace didn't do anything, just as Ctrl+Alt+F1 to F6, only holding the power button resolved.

Now it hanged on "fsck 1.40.2 (12-Jul-2007)", after "Chicking root file system...", this kind of hang I only saw happening when installing Debian on Windows Virtual PC.

I'm installing it on the last portion of my 200 GB hard drive, as a dual boot with Windows Vista.

Vista worked just fine, so I don't believe in hardware failure.

Any clue?

---

### Post by ridgeland on 2008-03-31
To get out of fsck hit [Esc].  I find I have to boot again and then it gets past it.  Edit /etc/fstab to stop checking if you want.

Let it boot fully before going to [Alt]+[Ctrl]+[F1].  Then go there to see if Linux is loaded and GUI is broken.

---

