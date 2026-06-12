---
title: "Issues Booting Up"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by BU2007 on 2007-01-19
Hi all,

I recently installed Ubuntu 6.10 on my Dimension 9150 (w/ an ATI graphics card). I had issues during the install and found this post [http://ubuntuforums.org/showthread.php?t=337736&highlight=x300]("http://ubuntuforums.org/showthread.php?t=337736&highlight=x300"). I followed the procedure that ClintiePoo has outlined and it worked like a charm.  However, everytime I restart my machine I am receive the "(initramfs)" prompt to which I type 'exit' and everything loads up fine.

Anyone know how I can remove this prompt from appearing at boot?

---

### Post by cmoz on 2007-03-22
> **BU2007 said:**
> Hi all,

I recently installed Ubuntu 6.10 on my Dimension 9150 (w/ an ATI graphics card). I had issues during the install and found this post [http://ubuntuforums.org/showthread.php?t=337736&highlight=x300]("http://ubuntuforums.org/showthread.php?t=337736&highlight=x300"). I followed the procedure that ClintiePoo has outlined and it worked like a charm.  However, everytime I restart my machine I am receive the "(initramfs)" prompt to which I type 'exit' and everything loads up fine.

Anyone know how I can remove this prompt from appearing at boot?

I'm having the exact same problem on a desktop with an Nvidia card. Anyone know how to fix this? it's getting really irritating

---

### Post by SilverZero on 2007-03-31
> **BU2007 said:**
> Hi all,

I recently installed Ubuntu 6.10 on my Dimension 9150 (w/ an ATI graphics card). I had issues during the install and found this post [http://ubuntuforums.org/showthread.php?t=337736&highlight=x300]("http://ubuntuforums.org/showthread.php?t=337736&highlight=x300"). I followed the procedure that ClintiePoo has outlined and it worked like a charm.

Which graphics card do you have? I have an XPS400, which is the same as the 9150, and an X300SE card. I was able to get through the system install, but whenever I try to install the fglrx drivers, I get black screens on "startx." I'm only able to get into the desktop using the vesa drivers. Any suggestions?

UPDATE: For anybody else having trouble, I used [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and the latest installer from the ATI website, and it worked great. The "aticonfig --overlay-type=Xv" step aborted every time for some reason, but it didn't affect the installation as far as I can tell.

---

### Post by eapache on 2007-03-31
This is at the bottom of ClintiePoo's thread:

> 
Ok, I figured out how to stop the prompt from appearing. Open a terminal, and edit the file
Code:

/boot/grub/menu.lst

Do a search for the word "break", and remove it. In VIM you can do
Code:

:%s/break//g

That will take the break out of the boot sequence.


---

