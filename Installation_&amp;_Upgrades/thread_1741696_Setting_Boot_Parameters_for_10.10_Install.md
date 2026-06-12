---
title: "Setting Boot Parameters for 10.10 Install"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Robert Finley on 2011-04-28
My keyboard doesn't work after the bootloader.

I've read that I need to add "i8042.nopnp=1 i8042.dumbkbd=1" to the boot options.

I have a 10.10 factory disk.
How?

---

### Post by mikewhatever on 2011-04-28
```
gksudo gedit /etc/default/grub
```

...edit the file so that the relevant line looks as follows:
```
GRUB_CMDLINE_LINUX="i8042.nopnp=1 i8042.dumbkbd=1"
```

...save and exit, then run **sudo update-grub**.

---

### Post by Robert Finley on 2011-04-28
That sounds like after it's installed.  I can't get through the installation process without the keyboard.

---

### Post by mikewhatever on 2011-04-28
Hm..., how are you going to type boot options if the keyboard doesn't work? Tricky.

---

### Post by Robert Finley on 2011-04-28
As previously stated, my keyboard stops working AFTER the bootloader

the fix is here: [http://www.linuxforums.org/forum/laptops-netbooks-minibooks/125767-solved-keyboard-not-working-after-boot-loader.html](http://www.linuxforums.org/forum/laptops-netbooks-minibooks/125767-solved-keyboard-not-working-after-boot-loader.html)

I'm looking for someone to explain how to do it when installing Ubuntu 10.10.

---

### Post by Robert Finley on 2011-04-28
I pressed esc and F6 at the boot menu. But that didn't get it. I ESC'd to cli but it didn't recognize the command..

---

### Post by Robert Finley on 2011-04-28
Use a USB keyboard to install and then edit grub?

Will it work?

---

### Post by mikewhatever on 2011-04-28
> **Robert Finley said:**
> I pressed esc and F6 at the boot menu. But that didn't get it. I ESC'd to cli but it didn't recognize the command..

Have you managed to type those boot options after hitting f6 and then Esc? There should have been an editable line down the bottom.

---

### Post by Robert Finley on 2011-04-28
> **mikewhatever said:**
> There should have been an editable line down the bottom.

That's what I was looking for. Thanks!

Unfortunately, entering them did not fix anything. Any ideas? I'm fresh out.  I've been in various forums and IRC channels for a year now trying to figure it out.

---

### Post by mikewhatever on 2011-04-28
Don't know really. What's the model of your computer/keyboard? Is it a desktop/laptop?

---

### Post by Robert Finley on 2011-04-28
Laptop= Acer 5517

---

### Post by mikewhatever on 2011-04-29
Hm..., the internet is not particularly overwhelmed with people complaining about keyboard problems on Acer 5517, but you've been fighting it for a year. Odd. I found reports of wifi and mic not working, but keyboard problems were non-existent.
[http://ubuntuforums.org/showthread.php?t=1331788](http://ubuntuforums.org/showthread.php?t=1331788)
[http://www.linlap.com/wiki/acer+aspire+5517](http://www.linlap.com/wiki/acer+aspire+5517)

---

