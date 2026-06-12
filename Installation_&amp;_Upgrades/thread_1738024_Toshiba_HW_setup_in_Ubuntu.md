---
title: "Toshiba HW setup in Ubuntu??"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by sangi on 2011-04-24
Hi

I use a Toshiba Satellite L655. It came with a Win7. The first thing I  did after buying it was to wipe out Win7 and install ubuntu 10.10 on the  entire hard disk (not a dual boot or Wubi install). Now I want to try  out ubuntu 11.04 beta from a live usb and I am trying to change the boot  order. The laptop doesn't boot from the usb drive. I am unable to enter  the BIOS. I have tried pressing ESC, F2 etc while switching on the  laptop. So far, I have not been able to access the BIOS setup.

I have tried googling and I read about Toshiba's "legacy-free" laptops.  But am not sure if mine is such a one. Now, I don't have Win at all in  my laptop. I have only ubuntu 10.10. I need to access the BIOS setup and  change the boot order so that my laptop boots from the USB drive. How  do I do this?

Toshiba has a hwsetup for Win. Is there a similar one for Ubuntu?

Any guidance would be welcome.

---

### Post by Paddy Landau on 2011-04-24
My Toshiba machine uses F12 to enter boot order, or F2 to enter BIOS setup.

Good luck finding it; have you phoned Toshiba support? It costs (a little), but should save you hours of searching.

---

### Post by dbombtek on 2012-04-08
I have the 775 but I am expecting a similar issue. I haven't installed ubuntu yet because I was unable to get the usb to run because of the same issue. What happens if there is a bios update? Good luck and I will keep checking to find the answer.

---

### Post by sangi on 2012-04-09
After my initial post, I managed to solve it myself by doing as follows:
- remove the hard disk
- press F12 and start the laptop
It took me directly to the BIOS setup.

I put the hard disk back and restarted (while pressing F12). It took me back to BIOS setup again.

The second time I restarted (while pressing F12, it did not take me to BIOS setup.

Every time I need to get to the BIOS setup, I take out the  hard disk and put it back.

Strange!!! but it works.

---

### Post by Bucky Ball on 2012-04-09
Just one thing. Did you mean you want to install 12.04 LTS beta?

---

### Post by sangi on 2012-04-09
No. I meant 11.04. It is an old post. Please see the date of the original post

---

### Post by dbombtek on 2012-04-21
I recently picked up the p775-S7100 and am trying to install ubuntu on it dual boot with win7. I created the usb boot using pendrivelinux but after creating the drive and restart I am unable to boot from usb. I have changed the settings in toshibaHWsetup to look at usb first. Any workarouds out there that anyone has heard of would be appreciated.

---

### Post by sangi on 2012-04-23
@dbombtek
Sorry. Can't think of any workaround. Would suggest that you talk to Toshiba guys on how to boot from USB. (Only hope they haven't blocked such an option). If you manage to do it, let us know here. Tks

---

### Post by dbombtek on 2012-04-23
Thanks for the reply but I tried and finally gave up on the usb boot option. I was able to install with CD and now I am happy to respond using 11.10.

---

### Post by Orion13622 on 2012-09-09
Guys and Gals,

Here's your answer in regards to getting to the toshiba setup.  First, make note of this, when you turn on your toshiba, do you see a Toshiba screen, or does it jump straight to the Windows 7 start up animation?  If it's the latter of the 2, then here's what you need to do (as no matter what you do, the function keys will not work unless you do this...).

1.  Let Windows 7 load.
2.  In Windows 7's Programs, under the Toshiba section, find HWSETUP, and open it.
3.  Change the startup from fast to normal.
4.  Save and reboot.  Voila!

Now you should see a Toshiba Screen Logo on power up, which enables everything from accessing the bios, to changing boot order, etc.

Hope this helps.

Orion

PS.  Now if someone would be kind enough to explain how to enable the multifunction lightup bar next to the power button on the P775-S7100 to turn on in Ubuntu, I'd be very happy.  :)  (On that enables and disables wireless adjusts sound vol., enables and disables eco-mode,).

---

### Post by Bucky Ball on 2012-09-11
@Orion: While it is thoughtful of you to add a solution, this thread was marked as solved nearly five months ago and has been inactive for that long.

As you intimate at the end of your post, if you have a problem please post a new thread with a descriptive title and giving as much info as possible about your issue. You've a lot more chance of help and attention than buried here. 

***Thread Closed.***
Reason: Solved and inactive for nearly five months.

---

