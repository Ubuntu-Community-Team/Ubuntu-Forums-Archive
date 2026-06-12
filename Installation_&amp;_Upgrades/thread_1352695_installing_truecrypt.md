---
title: "installing truecrypt"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by uo4 on 2009-12-11
how can i install truecrypt on my ubuntu. I dont get it i did searches but the instructions are very unclear for a novice

---

### Post by aysiu on 2009-12-11
**Step 1**
Go to the [TrueCrypt download page](http://www.truecrypt.org/downloads) and scroll down until you get to the part where you select your Linux distribution and hardware platform.

**Step 2**
From the dropdown menu, select *Ubuntu - x86 .deb* (unless you're absolutely sure you install 64-bit Ubuntu, in which case you should get the x64 one).

**Step 3**
Click *Download*

**Step 4**
Right-click on *truecrypt-6.3a-ubuntu-x86.tar.gz* and select *Extract here*

**Step 5**
Double-click *truecrypt-6.3a-setup-ubuntu-x86*

**Step 6**
Select *Run*

**Step 7**
Select *Install TrueCrypt* and accept the license agreement

**Step 8**
This should launch GDebi (also called *Package Installer*). Click *Install Package*

Now if you go to Applications > Other > TrueCrypt, it should be in the menu.

---

### Post by uo4 on 2009-12-11
thanks for taking the time to help me out

---

### Post by zozza on 2009-12-13
I agree - most helpful. 

I am also wondering if there is a CLI command that would have extracted the .deb file without needing the file browser?

I use tar, then file browser, then I can use dpkg after copying the executable from /tmp to ~.

But is there a way of using the CLI to obtain the .deb file?

Thanks.

---

### Post by aysiu on 2009-12-13
Unfortunately not. The untarred setup file appears to be a binary file. If it were a text script, I could just open it and see what it does to get the .deb file.

---

### Post by zozza on 2009-12-13
Is this a normal way to install programs?

Seems rather convoluted to me.

Why not just download a .deb file?

---

### Post by aysiu on 2009-12-13
> **zozza said:**
> Is this a normal way to install programs?

Seems rather convoluted to me.

Why not just download a .deb file?
No, it's not normal. It's specific to TrueCrypt. Normally you go through the repositories or just download and double-click a .deb file.

---

### Post by johntkucz on 2011-06-10
> **aysiu said:**
> **Step 1**
Go to the [TrueCrypt download page](http://www.truecrypt.org/downloads) and scroll down until you get to the part where you select your Linux distribution and hardware platform.

**Step 2**
From the dropdown menu, select *Ubuntu - x86 .deb* (unless you're absolutely sure you install 64-bit Ubuntu, in which case you should get the x64 one).

**Step 3**
Click *Download*

**Step 4**
Right-click on *truecrypt-6.3a-ubuntu-x86.tar.gz* and select *Extract here*

**Step 5**
Double-click *truecrypt-6.3a-setup-ubuntu-x86*

**Step 6**
Select *Run*

**Step 7**
Select *Install TrueCrypt* and accept the license agreement

**Step 8**
This should launch GDebi (also called *Package Installer*). Click *Install Package*

Now if you go to Applications > Other > TrueCrypt, it should be in the menu.


When I "run" the extracted package it wants to open it in a text editor and it is a shellscript.  thanks.

---

### Post by johntkucz on 2011-06-10
nvm ./truecrypt-7a-setup-x86  in cli worked.  I like cli more than gui at most times I am realizing!

---

