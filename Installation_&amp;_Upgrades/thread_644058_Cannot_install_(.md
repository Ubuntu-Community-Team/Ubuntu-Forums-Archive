---
title: "Cannot install :("
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by auschameleon on 2007-12-18
I got my new pc today. And when I boot it up it hangs on the pretty linux mint splash screen.
Now i've never used Linux so have NO clue about any of this.
But when it boots there are 3 options.
Linux mint kernal 2.6.22-14-generic
Linux mint kernal 2.6.22-14-generic (recovery mode)
Linux mint kernal memtest 86+

Now if I boot in recovery mode, it goes to root.. I have no idea what to do in root, but I thought it might mean something to you guys :) lol

So, given there was more support for Ubuntu, I d/l the cd, and put it in the PC.
It brings up the pretty UBUNTU screen with the orange scrolly thing.
Then stops!
It says:
Busybox V 1.1.1.3 (Debian1:1.1.1.3-5ubuntu7) Built in shell (ash) 
Enter 'help' for a list of build in commands
(initramfs)

No idea what any of that means.... So why can't I install the Ubuntu ?? It looks easy enough to use once it's installed and there is a user interface..  but then there is also a lot of gobble de gook going on here lol maybe I should get myself windows ??

Any advice is greatly appreciated, am looking forward to being able to use my new pc :)
Thanks in advance :)
Cham.

---

### Post by auschameleon on 2007-12-18
Not having much luck.. 
When I can finally get it to read the cd to check for errors, I've had a segment error and a disc with 2 errors.. the other 3 discs i've made I can't test cos it just keeps hanging when I try.
This is seriously really depressing.

---

### Post by Pumalite on 2007-12-18
What are the specs of your new PC?

---

### Post by auschameleon on 2007-12-18
Product Specs

System configuration

    * MSI Motherboard 
    * Socket 775 for Intel® Core 2 Duo, P4 5XX, 6XX, Pentium D 8XX, 9XX and Celeron D processors.
    * Supports FSB 800/533MHz.
    * Supports EIST technology.
    * Supports Intel® Hyper-Threading technology.
    * Supports Intel® Dual Core Technology to 800MHz and up 

 

msi

 

 

 

MSI Web site Click HERE...

 

*

    * Intel E6550 C2D CPU
    * 2 GB Memory
    * 400GB SATAII Hard Drive
    * Dual Layer DVD Rewriter
    * Auriga CAS2100BD Desktop/Mini Tower Case
    * Intel/AMD Approved MPT-400W PSU
    * Auriga PS/2 Keyboard and Mouse: Free with every computer!

      It's just a really comfortable, really portable, really sturdy and really inexpensive PS/2 keyboard and mouse set.

 
Add-on options:

Your choice of Ubuntu Linux (included in the price) or upgrade to Windows XP Home for only $138 more.

Ubuntu is a community developed, linux-based operating system that is perfect for laptops, desktops and servers. It contains all the applications you need - a web browser, presentation, document and spreadsheet software, instant messaging and much more.

---

### Post by Pumalite on 2007-12-18
Graphics?

---

### Post by auschameleon on 2007-12-18
no idea of graphics.. just onboard graphics I assume ?!?! it doesn't say does it.. and how can I find out when I can't get into my pc??

---

### Post by auschameleon on 2007-12-18
Intel® 945GC Chipset
- Integrated Intel® GMA 950 graphics core

is what it says on the misi website.

---

### Post by Pumalite on 2007-12-18
Use the Alternate CD to install. You probably will need to configure your xserver at the end of the install (blank screen). Post back then.

---

### Post by PhatKat on 2008-04-02
> **Pumalite said:**
> Use the Alternate CD to install. You probably will need to configure your xserver at the end of the install (blank screen). Post back then.

Aha i have the exact same problem as one of the forumite: unable to install on a 945GC chipset motherboard! Hmm i am really new with this so what do you mean by 'configure xserver at the end of the install'??

---

### Post by Pumalite on 2008-04-02
You ens up staring at a blank screen:
Ctrl+Alt+F1 to get command line:
sudo dpkg-reconfigure xserver-org
Accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by PhatKat on 2008-04-02
Sweet - shall try reinstalling and doing your recommended steps when i get home :P

---

