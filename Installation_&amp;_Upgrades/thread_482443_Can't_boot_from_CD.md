---
title: "Can't boot from CD"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by BlastOButter42 on 2007-06-23
Hi. I'm new to Linux and I'm trying to install it on an old laptop. I downloaded the ISO file and burned it to a CD. When I try to boot from the CD on the laptop, after I click "Start or install Ubuntu" and wait for about 3 minutes, a message box says "Error reading boot CD," and on the top of the screen it says "Loading isolinux: Disk error 01, AX = 4200, drive 9F". 

The CD is fine (I tested it on my other computer), and the CD drive on the laptop is fine too. Is there any way to fix this? If not, is there a way to get around it, or install Linux some other way? I have nothing of value on the laptop, and it's Windows ME, so I don't care what happens to it as long as Linux works on it.

Thanks.

---

### Post by eapache on 2007-06-23
Please post the specs of your laptop.

Also, press F6 to edit boot options, and remove 'quiet' and 'splash'. This should give you a more detailed error message, which might be useful.

---

### Post by logos34 on 2007-06-23
If you're sure the lappy cdrom is not having trouble with the media format (+rw or -rw, ultra-speed vs. high-speed, etc.), and md5sums and cd intregrity check out (different machines can react differently disc errors and corrupted files),

Try the network install method on this link:
**[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29)**

---

### Post by BlastOButter42 on 2007-06-23
The laptop is a Gateway Solo 9500 with Windows ME, 256 MB RAM and a 209 MHz Pentium III processor.
I was using a 52x CD-R, and all I know about the drive is that it is a Matshita DVD-ROM SR-8175, if that means anything. I actually tried the CD on 2 computers, and it worked on both. When I removed "quiet" and "splash",  I just got the same error message, and each time I restarted they were back again.

---

### Post by logos34 on 2007-06-23
You might have to jump through hoops to get this old thing to run the live cd--you meet the RAM minimum, buy I've seen people have trouble despite this.  Who knows what's the problem,  Save youself time and just download the text-mode alternate install cd and try that.  And if that doesn't work, forget cd's and use my link above to get a network install going.

---

### Post by BlastOButter42 on 2007-06-23
Well, I don't much care *how* I get Linux on there, just as long as I do. Which of the network install files should I download?

---

### Post by BlastOButter42 on 2007-06-23
Sorry, the processor is 1000 MHz, I was looking at the wrong thing.

---

### Post by merlinus on 2007-06-23
I used the text-based Alternate Desktop install cd for a 5-year-old Compaq with 256 RAM and a 1.09 processor.

Download and burn it, and it should work for you.

Much easier than the network install.

-merlin

---

