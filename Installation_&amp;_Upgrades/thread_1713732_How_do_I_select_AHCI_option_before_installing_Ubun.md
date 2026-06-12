---
title: "How do I select AHCI option before installing Ubuntu?"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-03-24
In order for TRIM to work on an SSD with encryption, I need to make sure to "select the AHCI option before installing the operating system."

Does anybody know how to do this? I have no idea what this is talking about. I'll be installing 11.04 with no dual-boot. Just Ubuntu alone.

---

### Post by Bucky Ball on 2011-03-24
Why 11.04? Not even released yet. Not interested in trying something stable with longer support; 10.04 LTS for instance?

Go 11.04 and this will be the least of your worries. ;)

---

### Post by nrundy on 2011-03-24
for a different computer. the desktop will be running 10.04. I want to have some fun with 11.04 :)

---

### Post by nrundy on 2011-03-25
nobody has any experience doing this AHCI thing?

---

### Post by Quackers on 2011-03-25
It is a setting in your bios.

---

### Post by nrundy on 2011-03-26
So I just go into the BIOS and look for AHCI? then make sure it is "Enabled". Then I can proceed to encrypt the partition and install the OS?

This is all there is to it?

---

### Post by Quackers on 2011-03-26
It is for me :-)
It may not be called AHCI though. It can be called other things. Anything that refers to enhanced or advanced compatible may be it :-)

---

### Post by nrundy on 2011-03-26
okay. Thanks Quack, much appreciated :)

encrypted 11.04 here I come :)

---

### Post by Quackers on 2011-03-26
Encrypted is not something I use. Nothing too important on here :-)

---

### Post by nrundy on 2011-03-26
it's the only sure-thing for being able to "wipe" the drive on an SSD before you get rid of it at end of life. traditional HDD wipe protocols don't work on SSD

---

### Post by Quackers on 2011-03-26
Oh, a hammer does that :-)

---

### Post by BadgerKid on 2011-03-28
> **nrundy said:**
> In order for TRIM to work on an SSD with encryption, I need to make sure to "select the AHCI option before installing the operating system."

Does anybody know how to do this? I have no idea what this is talking about. I'll be installing 11.04 with no dual-boot. Just Ubuntu alone.

You may want to check whether your hardware supports AHCI, e.g.,

[http://www.bootbeta.com/blog/does-your-computer-support-sata-ahci.html](http://www.bootbeta.com/blog/does-your-computer-support-sata-ahci.html)

---

