---
title: "ubuntu 11.10 64bit blank screen"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by shpark7 on 2011-12-20
Hi all,

I'm having trouble in installing 11.10 along with Windows 7 on other partition. I tried with two DVD images and a USB installer, but all gave the same symptom.

I can successfully see "Installer boot menu".

However, both "Run Ubuntu from this USB" and "Install Ubuntu on a Hard Disk" show purple Ubuntu screen with five dots, and right after that, it turns black and freezes.

FYI, installing 10.04 went smoothly without any issue.

Please help me with any useful tip, link, keyword to look for.

Thanks,
Sung Hee

---

### Post by emmomalick on 2011-12-20
Which Software are you using to create your USB? I mean it's Unetbootin or something else?

Try "nomodeset" or any other parameter like "noapic" or "acpi=of".

For more see this.

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

It works fine with Natty and Lucid so as well as might also with Oneiric also.

---

### Post by shpark7 on 2011-12-20
Wow, the link perfectly resolved my problem. 

Thanks!

---

### Post by Rubi1200 on 2011-12-20
Hi and welcome to the forums shpark7 :)

Good support there from emmomalick.

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy :)

---

### Post by emmomalick on 2011-12-21
It worked for you :) 

Welcome.

---

