---
title: "Machine not responding!"
date: 2015-04-19
forum: Installation &amp; Upgrades
---

### Post by Yezinki on 2015-04-19
Hi,

I was trying to install Ubuntu 64 bit on my laptop running W7.

All was going fine till I reached the partitioning step, there clicked on Guided (the last down) and next it showed 3 ntfs W7 partitions, I highlighted each set name, value and checked format.

Accidentally typed an extra zero for MB of each......after that system crashed.

Started the machine again it displayed several errors each time Missing System,  Memory Failure etc.

Now it wont even power up........and the DVD is stuck in the optical drive.

Any ideas,suggestion to fix it?

Thanks.

---

### Post by Bucky Ball on 2015-04-19
Firstly, if you look closely there is a small hole on the front of the DVD drive. Straighten a paperclip and push that in there to eject the disk. 

Try booting from the live media again, Try Ubuntu, at a desktop launch Gparted and see what you're left with on the drive. Are there partitions there and is Windows still there? If so, boot the machine with nothing in the drive and no USBs attached. Go straight to the BIOS on boot and set the machine to boot from the hard drive. How far do you get when you save that BIOS setting and reboot? Let us know. 

If you discover it is a mess in there when you look in Gparted and you have partitions missing that have valuable data on them you would like to retrieve, stop everything and switch the machine off and don't use that drive for the moment. Let us know.

Best to choose 'Something Else' at the partitioning section of the install if you're intending to dual-boot. ;)

Secondly, did you intend to completely remove Windows, because by highlighting the Windows NTFS partitions and setting to format, that sounds like what you were attempting to do.

---

### Post by Yezinki on 2015-04-19
Thanks for your expert reply.

1. DVD is out.

2. In setup when HDD is checked it boots up and shows a blank screen " Missing Operating System"??

3. I was not trying to dual boot.

4. Choose Something else.......when was trying to format the 3 W7 ntfs partitions, Bootloader, C and D and type values for Ubuntu/, /home and /swap......instead of 4000 MB typed 40000 for swap.

5. have a backup of all my data on that machine.

Thanks again.

---

### Post by Yezinki on 2015-04-19
After checking HDD in BIOS can only go far as after Dell Logo.......than dark screen displaying Missing Operating System.

---

### Post by Yezinki on 2015-04-19
Thats one reason I left Linux, I feel again that its not my cup of tea.......Windows is crap but doesn't give me headaches at this age.

Probably was a bad idea to try it.

Shall take the laptop to a local store to fix it.

Thanks again.

---

### Post by Yezinki on 2015-04-19
> **Bucky Ball said:**
> 
Secondly, did you intend to completely remove Windows, because by highlighting the Windows NTFS partitions and setting to format, that sounds like what you were attempting to do.

Correct......I intended to completely remove W7 32 bit and install Ubuntu Only on it.

Thanks again.

---

### Post by Yezinki on 2015-04-19
Now when I power it on see 2 lights blinking a box with A and another next to it with down arrow..

In between the BT icon and another box with 9.

These 2 blink for a few mins and than it shuts down automatically.

Hope this added info is helpful.

Thanks.

---

### Post by yancek on 2015-04-19
> In setup when HDD is checked it boots up and shows a blank screen " Missing Operating System"??

In your earlier post, you indicated while trying to install Ubuntu you had selected your windows (ntfs) partitions and selected to format them.  If that is correct, the message is what one would expect.

I don't know what icons you are referring to in your last post.  Are you not able to enter the BIOS setup on the computer to set it to boot from the DVD again?

---

### Post by Yezinki on 2015-04-19
> **yancek said:**
> In your earlier post, you indicated while trying to install Ubuntu you had selected your windows (ntfs) partitions and selected to format them.  If that is correct, the message is what one would expect.

I don't know what icons you are referring to in your last post.  Are you not able to enter the BIOS setup on the computer to set it to boot from the DVD again?


1. Correct.

2. Icons next to power button of the laptop.
, 
3. I did mange to enter the BIOS but now the machine wont even boot up as before bit starts and hangs even before Dell Logo......these icons on it blink for a mins or so and than it shuts down.

Thanks.

---

### Post by Yezinki on 2015-04-20
Issue resolved, took my laptop to a local pc repair shop, the tech took out the RAMs from slots and inserted them again........

Thanks for all your expert assistance.

---

