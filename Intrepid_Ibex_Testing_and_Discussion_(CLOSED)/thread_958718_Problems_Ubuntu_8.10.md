---
title: "Problems Ubuntu 8.10"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ozbolt on 2008-10-25
Although everyone tend to update version on release date or couple of days later this time I went for 8.10 5 days earlier. 
Well in Update manager everything went correct until my brother stopped everything. After reboot everything went wrong. So I went for second choice in boot menu and fixed everything, but then started not to normali start my ubuntu. When it came to the end of starting up process, where everything should go to Gnome stuff the screen went black and monitor literatury lost signal. So my little blue light on monitor started going on and off (As you can see I suck in English :D).
Well, I thought something went wrong in updating so first I went to shout on my brother and then went backing-up some files in WinXP (normally used only for CoD2) and downloaded RC 8.10, booted it and the same thing happened. But my LiveCD from Mint still works and also 8.04, so I think there is a problem in kernel. BTW: I tried:
- Load defauld BIOS
- Load 8.10 on second computer - works
- Went through memtest and CD check
- close computer for 15 minutes (you wouldn't mention how often this works)
And also this: Ubuntu 8.04 ran on this computer for 6 months flawlessly.

My comp specifications
- Q6600
- p5k pro
- ATI 3870
- 4GB Ram
- 550W power supply

---

### Post by falstaff on 2008-10-25
> 
Well in Update manager everything went correct until my brother stopped everything.


So your brother stopped the upgrading process?

> ...downloaded RC 8.10, booted it and the same thing happened.

What exactly happens? Does the boot screen with the Ubuntu logo becomes visible? When does it disappears, at the end of the progress bar?

You can also try to disable the Splash screen. Press e in the boot menu and then go to the second record. There press e again and delete "quiet splash".

Press Enter and b. No you should see how the kernel boots. What is the last line of the boot progress?

bye
falstaff

---

### Post by ozbolt on 2008-10-25
Sorry, I see I didn't use appropriate words.
Yes my brother stopped it becouse he didn't want to wait for system to update till end (he should just press that forward) so he pressed cancel correctly.
And second, when I boot up the CD there is no usual GRUB menu so "e" and splash screen I can't find. Well, now I have installed Mint (playing around) and not ubuntu to update it and test problems.
And third, my Ubuntu (so I think) boots up correctly (the line comes to the end) but then like driver would be inpropriate there is nothing on screen but I believe it runs correctly other stuff in backround.

So how can I get rid of splash screen with bootable CD?

---

### Post by falstaff on 2008-10-26
You can press F6 and then you can type kernel parameters...

So you think the graphic driver doesnt work? Try to press F4 at bootscreen, then save graphic mode... This should work on nearly every graphic card... You can later, when you've installed ubuntu sucessful, try to use the right graphic driver again...

bye
falstaff

---

### Post by ozbolt on 2008-10-26
Should I try Alternate and then in recover mode install envyng and then install Ati drivers?
First of all I'll wait this few days and then try again.
Thenks for help and I'll ask you again if that fails.

---

