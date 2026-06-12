---
title: "Grub rescue because of RAID ? how to not use RAID ?"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by emurb on 2018-01-30
Someone just gave me an unused server with a 10T hard drive in. 
I wanted to format and install Xubuntu 16.04 on it.
So I put my USB key and launched the installation and everything went fine. But when I restart the computer, I get these messages :
"1 Virtual Drive(s) found on the host adapter.
1 Virtual Drive(s) handled by BIOS
error: attempt to read o write outside of disk 'hd0'.
Entering rescue mode...
grub rescue>"
I entered "ls" and I get :
"(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (hd1) (fd0)"


After some researches, I found it happens because of RAID. I don't know at all how it works, and I don't want to use it. I just want to simply install Xubuntu on my 10T hard drive, and that it works without RAID configured.


Could you please help me to do that ? 
(I am a beginner on linux install, so can you tell me the "easy" protocol ?)
Thank you

---

