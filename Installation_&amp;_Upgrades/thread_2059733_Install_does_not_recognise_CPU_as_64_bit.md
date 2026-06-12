---
title: "Install does not recognise CPU as 64 bit"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by AnneFtl on 2012-09-18
I just downloaded Ubuntu 12 64bit and tried to install it.
Starts out ok and I select install. Then i get an error message saying my kernal is not 64 bit. 
What is wrong?  
My computer is running Win 7 64bit now.  
Thanks, Anne

---

### Post by jerrrys on 2012-09-18
What happens if you run the live CD with out installing?

---

### Post by AnneFtl on 2012-09-18
Don't know... will try it now... Anne

---

### Post by slooksterpsv on 2012-09-19
What kind of a computer is it? What kind of CPU? Also have you checked BIOS to see if 64-bit support is enabled ... maybe I dreamed that option was on a mobo... hmmm...

Also is VT-X or AMD-V enabled? (reason I ask is cause there was a bug with some CPUs and Motherboards where if VT-X or AMD-V was enabled it wouldn't detect 64-bit)

---

### Post by AnneFtl on 2012-09-19
The install process never gets that far. The Ubuntu purple background page with the two icons at the bottom appear and then the error message shows up within a second or two and thats are far as it gets.

---

### Post by AnneFtl on 2012-09-19
> **slooksterpsv said:**
> What kind of a computer is it? What kind of CPU? Also have you checked BIOS to see if 64-bit support is enabled ... maybe I dreamed that option was on a mobo... hmmm...

Also is VT-X or AMD-V enabled? (reason I ask is cause there was a bug with some CPUs and Motherboards where if VT-X or AMD-V was enabled it wouldn't detect 64-bit)

It is a Toshiba with an Intel T3400 dual core CPU and keep in mind that I now have Windows 7 64 bit OS in operation ... SO, I know it works with a 64bit OS.

---

### Post by darkod on 2012-09-19
Sounds like the ISO was corrupted during download or maybe during burning. The message that the kernel is not 64bit (note, you said kernel not CPU) is very strange since the kernel should be installed as part of the installation process.

According to the message, it is not saying the CPU is not 64bit but the kernel which makes no sense since you didn't even install yet.

You are sure you got the 64bit ISO version, right? The one that has the -amd64- in the filename?

---

