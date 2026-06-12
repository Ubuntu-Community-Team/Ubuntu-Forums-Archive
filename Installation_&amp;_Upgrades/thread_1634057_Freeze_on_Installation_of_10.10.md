---
title: "Freeze on Installation of 10.10"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by ianhoolihan on 2010-11-30
Hi there, I am completely new to Ubuntu as I'm trying to get away from Windows! I have an ASUS F50GL, and I've tried installing Ubuntu 10.10 off the USB and the CD version. Neither worked (well, the way I did things anyway...).

Firstly with the USB, even when I changed the BIOS so it should boot from USB first, it wouldn't. So forcing it to do this, then I got the black screen with the options to run it, install it, do memory test etc. However there was a separate white text over-top of this that was not part of the Ubuntu screen. It gave me 5 seconds to choose, or it loaded automatically. Anyway I selected the install option, and it got so far as the red screen with the Ubuntu word and the 5 dots going red to white etc. Then basically it just froze. So I restarted it by holding down the off button, and tried again. I did this repeatedly, but basically it kept freezing at this stage, or slightly further (different screen, sometimes the black menu-bar came up at the top), and then kept freezing.

Anyway today I tried to make a CD, and similar things happened. It looked like it might work (although it was still extremely slow), and I got to the stage of choosing advanced options (to choose how to partition hard-drive etc) and then it froze again. Again, I restarted, but it kept freezing, and never got that far again.

Could anyone give me some advice on how to resolve this issue and install Ubuntu? I read somewhere that there are ASUS motherboards which are completely incompatible with Ubuntu...I hope mine isn't the one (I've tried figuring it out, but to no avail).

Thanks for your time everyone!

---

### Post by mörgæs on 2010-11-30
Hi, welcome to the forum.

Have you tried the alternate installer?
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

If you use a USB stick, best is to create it with the latest Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ianhoolihan on 2010-11-30
Thanks. I haven't tried the alternative image - would that possibly help? Unfortunately downloading it may be a problem, and I don't have any more CDs to burn to, so an I'm hoping there is some fix with the current ubuntu-10.10-desktop-i386.iso I have.  Cheers

---

### Post by sikander3786 on 2010-11-30
I would be interested in checking the integrity of downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or it just might be a bad burn, check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If defected, burn a new one at the lowest possible speed.

Or burn a Live USB.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

If neither of them works, you might need to put in some additional boot parameters like nomodeset or acpi=off or noapic etc.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Anyway, my first recommendation would be to just check the image for defects and if ok, burn a Live USB again and see if it boots this time. Which program did you use to burn it last time?

This time I would recommend the one that is recommended by **morgaes **above.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by ianhoolihan on 2010-11-30
Thanks.  I've done MD5SUM, and checked the CD for defects, and tested the memory (well at least for a couple of hours...there were no errors detected, and it said it was finished, but it was still running, so maybe it was repeating itself?).   I hit SPACE when it got to the page with the little man, and things seemed to be going better. However trying to reinstall again, now it consistently gets to the "Install" page...first image here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions) ... except there is only the languages down the side. As soon as I click the "Forward" button, it freezes. Well I can still move the mouse, but it's unresponsive. The CD stops making the "reading" noises as well.  I managed to use the "Try Ubuntu" option, but as soon as I tried to put in my password for accessing wireless internet, it became unresponsive again. Using the install option from the live version also got to the same install screen and became unresponsive again.  So I then tried your Live USB option. The last one I tried I just followed the Ubuntu instructions and used Universal USB Installer. As you suggested I used unetbootin. The first thing I noticed is that the Ubuntu menu page did not come up, but these menu items were in a different form under the title "Unetbootin". Anyway trying to install or just run Ubuntu resulted in it freezing at the Ubuntu loading page, with all the five dots red.  I hope I've provided enough information.  Thanks

---

### Post by sikander3786 on 2010-12-01
> Anyway trying to install or just run Ubuntu resulted in it freezing at the Ubuntu loading page, with all the five dots red

Did you try putting in some boot parameters as I mentioned in my above post. nomodest, noapic, acpi=off or any of them just works magically and sorts the issues on some specific special hardware.

Try all of them and any of them might help.

If it doesn't, please provide us details regarding your hardware.

---

### Post by ianhoolihan on 2010-12-01
Yay!! Guess what? I am posting this not from Windows Vista, but Ubuntu!! Thank you so much sikander3786, and I tried what you said, and it turns out that the install worked fine with "nomodest".

Actually after clicking "reboot" to complete install, it went to a screen of text and said it was going to "reboot NOW!" but never did it. It was also frozen, so I had to manually restart. Also the first time I logged in, it was just normal, and it got to the desktop, and I could move the mouse, but everything else was frozen. So I manually restarted it. But then I restarted in Recovery Mode, and the screen said something about graphics or something not being determined, but now everything is working fine...in recovery mode. I should have tried it out in normal mode first, but I'm so excited I thought I'd post it now!

Thanks a bunch once again, and if I have trouble with the graphics etc, I think the rules say I should start a new post?

---

### Post by sikander3786 on 2010-12-01
Glad to know that it worked for you :-)

Regarding graphics, you can navigate to System > Administration > Additional Drivers and if any drivers are available, activate the current/recommended drivers from there.

If not, you can definitely start a new thread.

If you are satisfied, you can mark the Thread using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

> **guillend said:**
> Hi all,
I'm experiencing the same problem trying to install Ubuntu Desktop 10.10 into an MSI U200 Netbook. Same thing happens with Ubuntu Netbook 10.10. 

Initially I tried installing through the USB installer created via System/Administrator/Startup Disk Creator. Burned the ISO image, booted the netbook with it, then you see the colored dots for a while, and then it freezes. 

Since it didn't work, I purchased an external DVD/CD drive to boot from CD. And the same problem occurs. It freezes at the same place, with no feedback of what's wrong.

So I downloaded Linux Mint 10, which was recently released, and seems to be popular, burned the ISO into a CD, and tried it. It freezes too, but it gives some feedback (I guess it is the same problem as Ubuntu Desktop and Netbook): it says:

rt2800pci_mcu_status: Error - MCU request failed, no response from hardware.

I remember having other problems before with Ubuntu Netbook 10.04, [related to wireless] but at least that one installed from USB. 

I'm going to try now with Ubuntu Mini Remix [[http://www.ubuntu-mini-remix.org/]](http://www.ubuntu-mini-remix.org/]), to see if I can pass the freezing point.

Cheers,

As the issue for OP is solved here and the thread might be marked Solved, there will not be many people looking at this one. I have requested the mods to move your post to a new thread, if it doesn't get moved, you can definitely start a new thread yourself.

Good Luck!

---

### Post by mörgæs on 2010-12-01
> **guillend said:**
> 
Hope someone at Ubuntu is listening. 


If this means that you believe that you have found a bug and want it to be fixed, the answer is no. The developers seldom read this forum.

Before creating a bug report, a few more tests would be good to have. Again: Does it work with Unetbootin?

---

