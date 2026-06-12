---
title: "help,i'm stuck here(install 11.04) for serval hours"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by kingwrcy on 2011-08-15
hi,i try to install 11.04 on my computer,when i start install,it's stuck here 

can anyone tell me what's the matter ?

when i click the forward button ,it's stuck ,i try to change version to 11.04,10.10,10.04 ,

the same error,help me,plz!

---

### Post by Rubi1200 on 2011-08-15
Hi and welcome to the forums :-)

According to the screenshot you are not connected to the Internet.

What do you normally do to connect? Wireless, wired modem, dial-up?

Please provide us with more information.

Thanks.

---

### Post by varunendra on 2011-08-15
> **Rubi1200 said:**
> 
According to the screenshot you are not connected to the Internet.
Should it be a reason for the installation to hang? I don't think so. In fact, I intentionally disconnect whenever I want to finish an installation quickly (avoiding download of unnecessary font packages and similar other stuff)

I doubt the integrity/compatibility of OP's hardware- especially, the integrity of his hard drive.

---

### Post by kingwrcy on 2011-08-15
hi all,thanks for all your's reply.

yes,i want to finish the installation quickly,so i intentionally disconnect 

the internet,but whether i connect/disconnect ,the same situation at last.

[FONT="Arial Black"]I doubt the integrity/compatibility of OP's hardware- especially, the integrity of his hard drive.[/FONT]

can u tell me how to check this? if so,how can i deal with this problem?

i just want to install it on my hard drive,plz help!!

---

### Post by Dutch70 on 2011-08-15
Have you tried running Ubuntu from the LiveCD or usb stick? You should try that first to determine if it will run to your satisfaction on your hardware. 
If it works, you will actually be running from the cd or usb stick as opposed to your hard drive. You should then be able to use Disk Utility to check your hard drive.

I recommend being connected to the Internet whether or not it's necessary.

Also, knowing your computer specs may help.

Edit: Just so you know, it will be much slower from the live cd or usb stick than it is from your hdd.

---

### Post by varunendra on 2011-08-15
> **kingwrcy said:**
> 

[FONT=Arial Black]I doubt the integrity/compatibility of OP's hardware- especially, the integrity of his hard drive.[/FONT]

can u tell me how to check this? if so,how can i deal with this problem?
Of many possible ways, one is to try with a replaced hard drive. If it's not possible, try disconnect it and plug in a USB flash key or a memory card as a destination for installation, and see if the installation starts and completes successfully.

If doing any of this makes the installation proceed, it'll be an indication that the hard drive is on fault. We may then try to repair it if possible.

If the system is a desktop, some pci card may also be causing trouble while ubuntu tries to probe/configure it. Although it is less likely if it boots into live session without glitches.

A general way to determine a hardware problem is to start with minimum possible hardware, then start adding one-by-one until the problem reoccurs. Then the one which brings the problem back is the hw in question.

One more thing, besides the hard drive thing, you should also run memory-test for as long as possible (at least 2-4 hours) to make sure it is not a memory-leakage problem.

---

### Post by kingwrcy on 2011-08-16
Thanks very much for replies.

OK,i will have a try(install it from USB),and do some test for my memory-card 

and hardware.

thks.


wish me good luck!!!

---

### Post by varunendra on 2011-08-16
> **kingwrcy said:**
> Thanks very much for replies.

OK,i will have a try(install it from USB),and do some test for my memory-card 

and hardware.

thks.


wish me good luck!!!
When I said 'memory test', I meant RAM test. It's an option in the boot menu which comes up when you press any key while booting from the CD. (if you don't press a key, it gets straight to the 'try or install' options' screen)

And yeah, Good Luck with your attempts!! :)

---

