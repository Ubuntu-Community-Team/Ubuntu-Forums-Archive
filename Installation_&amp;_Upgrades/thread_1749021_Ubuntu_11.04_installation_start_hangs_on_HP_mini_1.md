---
title: "Ubuntu 11.04 installation start hangs on HP mini 110"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Harikrishna.J on 2011-05-04
HI,

I have a HP mini 110 netbook with Windows7 starter and dual boot with Ubuntu 10.10. It works very good.

Now I tried to install 11.04, but installation start screen itself hangs...  :(

Any solutions please suggest.

Regards,
HARI

---

### Post by jfmessier on 2011-05-19
When booting from a USB stick, insert the following on the option line before booting Ubuntu: 

**acpi=off noapic**

You should be able to do this by using F10. That is the key I used to boot my USB installation setup, which I created using unetbootin under Windows. 

But once the installation is completed, you will also need to insert this option permanently in the boot. 

You need to manually  (as root) edit the file

** /etc/default/grub**

and insert the option. Then, execute the command:

**update-grub** 

(as root)

---

### Post by Quipuot on 2011-09-11
I have exactly the same problem. I have the Ubuntu 11.04 image on USB, but when I try to boot from USB, the screen goes dark or I just get a single curser. I've tried to follow the suggestions from jfmessier, but I was unsuccessful (I not a linux user, so perhaps I just need more detailed instructions?)

If anyone has a solution for running Ubuntu 11.04 on the HP Mini 110 I would appreciate it.
(It is an HP Mini 110-1020NR)

---

