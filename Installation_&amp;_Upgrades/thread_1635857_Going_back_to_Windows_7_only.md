---
title: "Going back to Windows 7 only"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Paragon009 on 2010-12-02
I was able to install Lucid Lynx 64-bit. I selected manual partitioning which I completed without complication.
 
I encountered several problems after installation:
 
I could not use my Radeon HD 5870 graphics card. Whenever I enabled it in the BIOS, the monitor would go to "sleep." When it was disabled and the onboard 4200 graphics card was used, everything was normal. Of course, this meant that I could not enjoy my PC gaming. 
 
Next, I could not connect to the internet.
 
I searched for solutions and found one [[here]("http://ubuntuforums.org/showpost.php?p=9910686&postcount=2")]. After I performed this procedure, I activated the ATI proprietary driver. I also had internet! Everything seemed great. I was about to enjoy the fruits of my labor.
 
When I rebooted and went to Windows to make sure everything was good on that end, I got the...wait for it...waaait for it...blue screen of death.
 
That's where I'm at. I'm extremely hesitant to do anything else at this point for fear of not being able to use Windows altogether (I need it for school). However, during the school break, I plan to re-format the HD because I don't see any possible solution to the BSOD. Using the Windows recovery disk availed nothing whatsoever.
 
Furthermore, since I don't have an actual Windows CD, and my recovery disk is not doing jack, that means I will be buying a Windows 7 Home Premium disc for $175. I wasn't expecting that when I installed Ubuntu. =(
 
I guess what I need to know is whether I can re-format my HD to the way it was pre-Ubuntu. That means, will I be able to delete the Ubuntu partitions?
 
Next, is there somewhere where the Ubuntu gurus go to learn all "sudo" codes? I know there are quite a few books out there on Ubuntu and Linux, but where does everyone get their knowledge? With Windows, you can go to the website tutorial or Microsoft itself. The only vast field of knowledge I've seen with Ubuntu is this forum and perhaps Linux forum, in addition to the books. I guess that's relatively equivalent, but I don't know, I guess I'm just disconcerted because I find myself plugging in codes which I am not familiar with. Totally my fault though...don't get me wrong.

---

### Post by arubislander on 2010-12-02
Did you remember to re-enable your graphics card before booting into Windows again? Windows doesn't like it when you swap hardware from under it.

---

### Post by wilee-nilee on 2010-12-02
If you have a legal install of windows you can buy the OEM discs or a regular install disc from MS, you just have to have registered the setup and be legal. To be honest why would you have to spend 175$ that makes no sense.

---

### Post by uRock on 2010-12-02
> **arubislander said:**
> Did you remember to re-enable your graphics card before booting into Windows again? Windows doesn't like it when you swap hardware from under it.

+1 to this. I have the same problem with my daughter's GPU. It works with Ubuntu, but not with Windows XP. We have to use the on board graphics for Windows.

---

### Post by oldfred on 2010-12-02
You can download a windows repair CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I have Nvidia and had to do this;
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by Paragon009 on 2010-12-04
Well, I noticed during the BSOD that the missing file name had "akamai" in it. It goes by so fast, that I couldn't get the entire file name. Well, I was downloading drivers from AMD website to burn to a CD in case I needed to reformat HD. I noticed the file names of AMD's drivers have the word "akamai.net" in them. So, I decided to reinstall my AMD 5870 graphics card driver, and what do you know? It worked! No more BSOD. I got my PC back! So happy. So, mark this thread solved.

---

### Post by Quackers on 2010-12-04
Have you made the recovery dvd's yet? Have you made a Windows repair cd? It might save you some money and heartache!

---

### Post by Paragon009 on 2010-12-06
> **Quackers said:**
> Have you made the recovery dvd's yet? Have you made a Windows repair cd? It might save you some money and heartache!
I made some when I first got the PC. Problem is, they didn't work. Windows couldn't accomplish the repair using the DVD. Don't ask me why. And, well, Windows' own website and forum say that you can't get install CD's if you bought a PC that had Windows downloaded by the manufacturer (which is how most PC's are sold these days in stores). You have to use recovery CD's, and if you lose them, you have to get more recovery CD's from the PC manufacturer.
 
But, it's all good. Problem has been resolved. I had to re-install the gfx card drivers.

---

