---
title: "Switching Hard Disk from old computer to new computer"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by BDNiner on 2008-02-27
I was wondering if it is possible to to move my current installation from one computer to another one with different hardware specs? Is the installation tied to the hardware the same way it is in windows? If i have hardware from the same vendor could i move the hard disk and have the computer boot? just like i can in windows without reinstalling linux?

---

### Post by prensing on 2008-02-27
This depends a little on what you may have done to the OS. Given that you are asking the question, I would guess that you have not install a custom kernel, nor carefully trimmed the set up installed modules. Assuming you have not done that kind of thing, I would guess that there is a 95-99% chance that you will have no problems. 

The only issue I could see is special drivers for things like wireless cards. Some wireless cards have semi-proprietary drivers which are not installed by default. If the new box has that, you might not have wireless working until you can get the necessary driver installed.

But for just CPUs, hard drives, etc you should have no problems.

---

### Post by BDNiner on 2008-02-27
The only thing i am changing is the motherboard, CPU and memory. Everything else is going to be the same.

---

### Post by sp0nge on 2008-02-27
This should work with little problem unless you have made major changes to the kernel as mentioned above. 

What are you doing with the hard drive from the other machine, if you don't mind my curiosity.

---

### Post by BDNiner on 2008-02-27
The other machine doesn't have a hard disk. I ordered a new MB, CPU and memory for the linux PC in my sig. The old parts will be used for a simple file/backup server (and whatever else i can think of) in the neat future (once i get the Hard Disks and PCI card that i need to setup raid)

---

