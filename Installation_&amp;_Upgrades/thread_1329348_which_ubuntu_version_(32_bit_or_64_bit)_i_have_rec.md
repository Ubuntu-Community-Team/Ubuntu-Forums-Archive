---
title: "which ubuntu version (32 bit or 64 bit) i have received"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by abhishek66866 on 2009-11-17
Hi 
 
I have requested a free CD, from ubuntu site. The url was [https://shipit.ubuntu.com/myrequest](https://shipit.ubuntu.com/myrequest) .
 
I have received the CD. I want to know that the CD is for ubuntu 64 Bit Architecture or 32 Bit Architecture.
 
I have Windows Vista Home premium 64 Bit OS in my Laptop with intel Core 2 Due Processor. I want to install in my system on windows . 
Will it work in my Laptop or not. Please help

---

### Post by cascade9 on 2009-11-17
Either should work. 

If its the 32bit version, and you have more than 4GB of RAM, you might not be able to use all the RAM.

---

### Post by abhishek66866 on 2009-11-17
does the CD that i have received is for 32 bit or 64 bit architecture

---

### Post by abhishek66866 on 2009-11-17
please some one reply

---

### Post by cascade9 on 2009-11-17
What did I do, chop liver? I thought I had posted :P LOL 

32 bit linux will run on 64 bit machines. Its not an issue. The only possible issue is the 'cant see over 4GB RAM' problem I posted before.....

Edit- By the way, excessive 'bumping' of threads isnt a good, or nice idea. If nobody has answered in 24 hrs or more, its normally fine, but every 20 minutes is bad.

---

### Post by alexfish on 2009-11-17
try putting in cd   the title should show ubuntu "version" i386 for 32bit
                                                        ubuntu "version" amd64 for 64 bit

---

### Post by slakkie on 2009-11-17
Most likely the 32 bit version, boot from CD and run the following in a terminal:

getconf LONG_BIT

This will tell you if it is 32 bit or 64 bit.

---

