---
title: "System Hangs: 2.6.32-19-generic"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Doctor Mike on 2010-04-03
Since updating the kernel from 2.6.32-18-generic to 2.6.32-19-generic my system hangs, slows down more and more then becomes unusable (overnight). I can't point to a specific conflict, but wonder if it's an issue with my old ATI Radeon (REV 100) video card and the development kernel? Anyone with a similar problem's (comments) or an idea how to track down the bug, so I can report it would be of great help.

---

### Post by Revord on 2010-04-03
What are your symptoms and what card do you have? I'm just curious, because I have had a problem with my 64bit installation 'stuttering'. At first, I thought it was a memory problem. However, after further inquiry, it was determined to be an issue with my graphics card. Im using an ATI Radeon X1650 AGP card. Is yours that old as well? We may have a similar problem. Reference [this post]("http://ubuntuforums.org/showthread.php?t=1444571") for info based on how I came to this conclusion.

---

### Post by Doctor Mike on 2010-04-03
> **Revord said:**
> What are your symptoms and what card do you have? I'm just curious, because I have had a problem with my 64bit installation 'stuttering'. At first, I thought it was a memory problem. However, after further inquiry, it was determined to be an issue with my graphics card. Im using an ATI Radeon X1650 AGP card. Is yours that old as well? We may have a similar problem. Reference [this post]("http://ubuntuforums.org/showthread.php?t=1444571") for info based on how I came to this conclusion.I'm using the ATI Radeon 7000 VE AGP. I've suspected that support for older ATI drivers might not be provided in Luicd Lynx or final 10.10 version. Nobodies really responded to my questions about that. The way everything takes longer and longer to respond and the system eventually locks up leads me to believe that it's a video card driver issue. No indication of system resources being taxed at all. It would be nice if it were clear that this is the problem, but when I run the earlier kernel (18 ) things are more stable and don't slow down. So, I think it's the problems with the development kernel with respect to (or in combination with) problems with incomplete ATI drivers.

---

### Post by savantelite on 2010-04-03
my system also failed and would not boot up. I only recieved stars on my screen and nothing would happen.

---

### Post by grandtoubab on 2010-04-03
Hello
You can change your Kernel as well
For my Radeon Xpress 200 on AcerAspire T650 the better is
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-03-08/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-03-08/)

do your market on it!

and install it as this
[http://ubuntuforums.org/showpost.php?p=8886636&postcount=43](http://ubuntuforums.org/showpost.php?p=8886636&postcount=43)

---

### Post by grandtoubab on 2010-04-03
> **savantelite said:**
> my system also failed and would not boot up. I only recieved stars on my screen and nothing would happen.

change your plymouth theme 
[http://ubuntuforums.org/showpost.php?p=9043993&postcount=3](http://ubuntuforums.org/showpost.php?p=9043993&postcount=3)

---

### Post by savantelite on 2010-04-03
I reinstalled and wiped the hard drive. I was having issues with the 2.6.32- 17 version

I updated after inisail install and this 19 version seems to work well.

---

