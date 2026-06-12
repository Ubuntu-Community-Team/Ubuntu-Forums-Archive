---
title: "Won't boot after Install"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by russ1960 on 2010-07-24
I have a ASUS CM5571 desktop with Intel E5400, 2.7 GHZ dual core processor - 6gb memory, 1 terabyte hard drive - using the on-board Intel express chip-set for video and on-board sound.   I was getting USB errors on every device so I eliminated the printer and external hard drive leaving only the keyboard and mouse - now it hangs at the keyboard:  line 2.980306 generic usb keyboard.  it gives me no error - just stops there.

Any ideas?    This is a 64 bit system with Windows 7 Home Premium as a dual boot.   There were no issues with the initial install.  Using Ubuntu 10 64 bit version.

Thanks

Russ

---

### Post by stlsaint on 2010-07-24
Try removing the mouse and keyboard and try a regular boot up.

---

### Post by Goolie on 2010-07-24
Yea, and if that works, check around for a different keyboard.

Is that keyboard / mouse going into the normal PS/2 inputs or the USB inputs?  If it's one or another, try the opposite!

Good luck...

---

### Post by russ1960 on 2010-07-24
Did not work when i took the mouse and keyboard out.  I tried the Fedora and Mint install and got the same problem.  Only one that works with no issue is Suse.  Guess I am stuck with that one.

---

### Post by russ1960 on 2010-07-25
Swapped out keyboard and mice - now I keep getting a Call Trace done over and over to the kernel - it just repeats it self - same command line comments but different line numbers. I attached a picture of the screen - kinda blurry but if you enlarge it  you can read it.

---

### Post by amarintj1986 on 2010-08-24
> **russ1960 said:**
> Swapped out keyboard and mice - now I keep getting a Call Trace done over and over to the kernel - it just repeats it self - same command line comments but different line numbers. I attached a picture of the screen - kinda blurry but if you enlarge it  you can read it.

I have exactly the same problem with Lucid Lynx, even when instaling from Live CD, I haven't found a solution yet. In that moment what I did was to install hardy heron (which worked perfectly) and upgrade to Lucid Lynx from the update manager, but the problem was that when it booted it continued giving the same error:

Call Trace:
?do_page_fault +0x4d2/
?error_code +073/0x80
do_sys_open +6x55/0+160
sys_call +07x/0xb

I read somewhere that it could be because of a problem supporting Intel integrated video and Intel graphic cards. So, you could try installing an NVIDIA or ATI graphic card in order to see if that works (I don't have any so a can't prove it, right now I'm using OpenSuse, but it's pretty good actualy)

Regards,

---

### Post by amarintj1986 on 2010-10-05
By the way, I found another thread talking about the same issue in my opinion.

Look at the final post in this link:

[http://ubuntuforums.org/showthread.php?p=9762724](http://ubuntuforums.org/showthread.php?p=9762724)

_[U]Olligobber_[/U] says that he had the same problem, but "fixed it" changing the video card.

Obviously its a bug that should be really fixed

---

