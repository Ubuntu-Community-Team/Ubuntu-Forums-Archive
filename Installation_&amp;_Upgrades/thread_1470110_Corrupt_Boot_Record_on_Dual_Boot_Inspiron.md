---
title: "Corrupt Boot Record on Dual Boot Inspiron"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Cerin on 2010-05-02
I bought a Dell Inspiron 1545 laptop, and installed Ubuntu 10.04 to dual boot alongside Windows 7. Regrettably, I did something in Windows 7 that caused it to overwrite the master boot record, so now when I reboot I get the message "No bootable devices". Is there an easy way to fix this, or do I have to wipe out everything and reinstall?

---

### Post by lulio on 2010-06-03
I am faced with the same problem. 
I had finally convinced a friend of mine to try Ubuntu, so I installed 10.04 for her, duel booting with Windows 7. 
Now her computer is erasing its own hard drive and is virtually unfixable. Naturally she blames Ubuntu but I can't understand why it would cause her laptop to crash like this. 
It was installed, by the way, via flashdrive. One that I had used various other times without viruses or glitches of any kind. 
Is there any help for this at all?

---

### Post by darkod on 2010-06-03
When you say erasing its own hard drive, what do you mean exactly? Erasing part of grub2 making it unusable?

Some Dell and HP machines do that because they run some rubbish program in windows, so every time you boot windows it destroys grub2.

[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by lulio on 2010-06-03
Thank you sir! This is quite what I need

---

