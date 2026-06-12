---
title: "Installation on old ThinkPad hangs with &quot;System V initialisation compatibiity [OK]&quot;"
date: 2015-06-08
forum: Installation &amp; Upgrades
---

### Post by ziegler-g on 2015-06-08
I am desperately trying to install Lubuntu 14.04 on an old IBM Thinkpad T60p. The processor is an Intel T2600 with 2 GHz (according to the BIOS).
I use a Lubuntu USB Live Stick.

It took me already 2 days to discover that I have to give the "forcepae" option for the machine to to anything at all.

In the installation menu, when I select "Check disc for errors" and remove the "quiet" and "splash" option and add "forcepae", the disc is checked, and the tests says that it is ok.

When I then select "Try without installing" and also enable/disable the above options, booting begins, a LOT of messages are printed, and it stops with 

"System V initialisation compatibiiity [OK]"

Sometimes it stops with

"Starting ntpd [OK]" (or something similar, concerning NTP)

or

"Stopping early crypto disks [OK]" (Or "starting crypto..."? I do not remember.)

What can I do now?

I have tested the machine's hardware with nearly every tool from the UBCD (Universal Boot CD). Nothing of them reported any error.
Unfortunately, even while running PC-Config from the UBCD, the ASCII-screen freezes :smile:
Maybe there is something wrong with the input devices  and it is not the   screen that is frozen? I wonder how tests such as computing Pi zo   1,000,000 digits and solving huge systems of linear equations can pass   through...

I am stubborn. I do not want to throw away this laptop, but donate it to   a poor school kid of mine.  Lubuntu is exactly made for this.[TABLE="class: tborder, align: center"]
[TR]

[/TR]
[TR]
[TD="class: alt1"][/TD]
[/TR]
[/TABLE]
Thank  you in advance,

PS: What is the meaning of the 2 "--" in the kernel parameter list?

PS2: I have burnt "Hiren's Boot CD"  with unetbootin to an USB stick because I read so often that this were the best tool to do hardware disgnostics. The booting process stops with "Setting up system devices..." Is there somewhere a step-by-step tutorial for how to completely test all hardware components of a laptop or PC?

---

### Post by tgalati4 on 2015-06-09
Try 12.04.  That is an older machine.  At least try to get something on it.  The T60p was a good machine it its day.  Tough and ugly.  I got my T43p because the seller's daughter wanted a pink Sony and not an ugly, black, Thinkpad.

---

### Post by sudodus on 2015-06-09
For me "Try 12.04" means that you should try a light community re-spin  linux distro based on Ubuntu 12.04 LTS, for example LXLE or Bodhi Linux.

I have an IBM Thinkpad T42, which needs forcepae. I'm not sure, but I don't think the T60 needs it, because it has a more modern processor, I think it is a core duo. However, forcepae does not do any harm to a computer, that does not need it.

-- is a separator. Boot options entered before affect the live session. Boot options entered after are transferred to the installed system.

I think there might be problems with the graphics, or some hardware that is damaged, because these old Thinkpads usually work well with linux. (Maybe someone knows, if there is an exeption for your particular model.)

One link talked about ATI Fire GL graphics, which might have problems with new versions of linux. After trying 12.04, you might try Wary Puppy or TahrPup, which a ultra-light distros for old hardware.

---

### Post by tgalati4 on 2015-06-09
The "p" means problematic graphics on most Thinkpads.  Mine has a FireGL chip and delamination is a common problem which results in strange graphics and lockups.  So it's possible that the OP's T60p has developed such a problem.  No real fix.  Some have used a small torch and a foil shield to resolder the BGA chip, but repair success is quite small.  Motherboard replacement or just find another model without the "p" that boots correctly with a LiveUSB of any of the lighter flavors of Ubuntu.

---

### Post by ziegler-g on 2015-06-12
For all of you who tried to help me: Thank you very much!

I have started a new thread and switched over to it in LinuxQuestions.org [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/is-there-a-step-by-step-instruction-to-test-a-laptop-or-pc-for-hardware-failures-4175544834]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/is-there-a-step-by-step-instruction-to-test-a-laptop-or-pc-for-hardware-failures-4175544834/"), because it turned out that this is not a (L)Ubuntu specific problem, but rather a hardware one. I will stop this thread now here (should I mark it as [solved]? It is is not yet solved).

You may want to follow the thread there if you want to help poor children. Let me cite myself from the thread there:

>  Let me please first tell you why you are doing something very good for poor people by your efforts:

I am working for a German elementary school with 441 school kids, more  of 80 percent of them with "migration background" (Bulgarian, Romanian,  Russian, Arabian, ...). Many of them are too poor to buy a laptop or PC  of their own. So we plan to ask the "richer" parents and all our other  contacts to donate us their old, unused laptops and PCs (mostly machines  on which once ran Windows XP, but which are too slow now for  MS-products or too filled with garbage now so that the owner thinks  she/he has to throw it away and buy the latest bleeding-edge laptop with  Windows 9), and apart from that, I do not want to teach school kids that they are dependent on  a certain company for their whole lifetime, and install some Linux  distro on it. 

I am first in the testing phase of this project, and the ThinkPad T60p  that we talk about here is one of these machines already donated.  Windows XP was installed, but the screen constantly froze and the owner  bought himself a new laptop. 

I have started to experiment with Lubuntu because the GUI is similar to  what children know from MS-products and because it is designed for  running on old hardware. And, if possible, I would even like to install  Edubuntu because it has so many good education software, but I do not  know yet whether it is too resource consuming for old hardware.

The final challenge for me will be: How do I install, fighting alone,  Linux on 441 laptops all of a different manufacturer and all differing  in model without spending too much time of my own? (I plan to start a  new thread for that as soon as we know what distro we will use and what  software should be pre-installed.)

Thank you again, and greetings from Germany!

---

### Post by sudodus on 2015-06-12
Post #5 is a good way to finish this thread. Do not mark it as SOLVED.

Maybe you can engage local computer enthusiasts. Is there a computer club? - And don't fight too much with bad hardware - try to get things that work without too much effort! See this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

Good luck with your project :KS

---

