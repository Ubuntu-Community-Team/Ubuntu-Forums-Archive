---
title: "black screen in ubuntu 10.10 x64 installation"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by sim0s on 2010-11-26
Hello guys,

I am new to ubuntu forums and generally to linux OS.
I have a Sony Vaio VPCS13C5E with OS Windows 7 Ultimate and graphic card NVidia GeForce 310M. 
I am trying to install Ubuntu 10.10 x64 but when I boot the laptop I only see a black screen and nothing else. Everything it seems to stop.
I have read in some other threads that is a graphic card problem but I still can't solve it.

Could you please help me to solve this issue?
I 've been struggling with this problem the whole day.


Thanks,
Simos

---

### Post by Rubi1200 on 2010-11-27
Hi and welcome to the forums :)

Try this to boot the LiveCD:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop of the LiveCD and from there try installing.

---

### Post by snuffmeister on 2010-11-27
Hi, I've got a similar laptop, the Vaio VPC F12 M1E with an Nvidia Geforce 330M. The problem here is Ubuntu's open source display driver for nvidia, the 'nouveau'

If you try a couple of times you can boot into the live cd and install, but there's a mismatch resolution problem (way too big for the screen)

The problem persists after install, and I don't know how to solve it. I think I have to change the drivers to Nvidia's proprietary ones but I don't know how to do that...

---

### Post by sim0s on 2010-11-27
Hello Rubi and thanks for your help.

I 've tried something similar of what you told me and I managed to enter to ubuntu desktop home screen. I pushed f6 while booting and I chose nomodeset from the menu came up and it has booted with low resolution.

If I understand well, this is very similar, isn't?
Do you know why this is happening mainly with nVidia cards?
Also, after that I will be able to install it as usual?


Thanks,
sim0s

---

### Post by Rubi1200 on 2010-11-27
I don't use NVIDIA, but from what I understand you can now go ahead and install Ubuntu.

Either the problems will be solved with the install or you may have to install some additional drivers. In either case, we can find a solution for you.

Hope this helps.

---

### Post by timvg on 2010-12-01
Hey there guys. I have exactly the same computer with the same Nvidia graphics card and I am new to Linux too. I had exactly the same problem when I first installed Ubuntu. I used this fix and it worked, thank you. BUT... when I installed the proprietary driver for the 310m and restarted the computer, Ubuntu failed to load and all I was left with was a screen with vertical bars of different shades of grey. Maybe I should be grateful that it was slightly more interesting than the completely blank screen I had before... but it is still useless! This driver was the one that Ubuntu recommended that I use and stated that it had been approved for use.

I have seen that similar things have happened to others and there are many different ways written about to fix them. But as a newbie, they all sound pretty scary! They involve something like installing the latest driver, then disabling the x-session, then altering the script in the xorg.conf file. However, there has not been a definite solution provided.

I was wondering if anyone knew how to solve this. I am new and was looking forward to learning more, but that is dependent on it actually working in the first place!

Thanks.

---

### Post by locosway on 2010-12-01
I'm trying to install Ubuntu 10.10 on my new laptop I bought last night and I'm having the same issue. I get the first splash screen, and if I leave it alone I eventually get a black screen with nothing.

Doing the nomodeset and removing the quiet splash I see this:

[IMG]https://dl.dropbox.com/u/10998741/IMAG0064.jpg[/IMG]

Nothing further happens, it just sits here, forever...

I have a Dell M5010 which has a AMD Phenom II, and a ATI 4250 (I believe).

Sorry for the high res photo, I can't resize it from my phone.

---

### Post by stefango on 2010-12-18
Hello, 
I have the same laptop (VPCS13C5E with nvidia geforce 310m video card).

The good news is that I managed to make video card working, after following dozens of posts in internet. 
The bad is that vga output is still not working. I cannot speak about HDMI port. 

I don't remember exactly all the modifications I did, even because I tried many configurations until finding the correct one.
Anyway, you can try following the procedure described here [http://ubuntuforums.org/showthread.php?t=1481842&page=8](http://ubuntuforums.org/showthread.php?t=1481842&page=8) in post #77

As a difference between the proposed solution, note that I'm using kernel 2.6.35-22-generic, while the graphic driver is the same (nvidia 256.53).

I hope this can help you.

---

### Post by Jonners59 on 2010-12-18
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Try this to boot the LiveCD:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop of the LiveCD and from there try installing.

I have a PC that I have Ubuntu 10.4 within which I have Sun's VirtualBox running Windows 7.  It also has Vista that I do not use anymore.  The 10.04 is running badly and so I want to start from scratch, so I ordered a 10.10 CD and am trying to install.

It stops at this same point.  I have tried the instructions above and gets to line:
[299.847864] freeing initrd memory: 11144k freed

the cursers then stops on the next line.

I have run a memory and CD test, The CD test just goes to a blank screen with the curser in top corner.  I get this problem on all Ubuntu installs above 09.10.  I can't recall how I installed 10.04

The machine runs AMD 65-bit and nVIDEA

Any ideas.
------------------------------------------------------------------------------------------------------------

FOOTNOTE:
AFter submitting this reply.  I carried on playing and solved the problem.
FYI
Besides doing as below; press F6 and select nomodeset then run.....  If that does not work, try with other combinations under the F6

---

### Post by NennokraH on 2011-01-24
Hi all,

I had a problem with my desktop. I noticed there is a problem with NVIDIA 9800 GT series and that is why the black screen. I followed exactly Rubi1200's instructions and it worked perfectly. So i guess for some of us is working.

Many thanks Rubi1200

---

### Post by Rubi1200 on 2011-01-24
> **NennokraH said:**
> Hi all,

I had a problem with my desktop. I noticed there is a problem with NVIDIA 9800 GT series and that is why the black screen. I followed exactly Rubi1200's instructions and it worked perfectly. So i guess for some of us is working.

Many thanks Rubi1200
You are more than welcome :)

Glad you got things working.

---

