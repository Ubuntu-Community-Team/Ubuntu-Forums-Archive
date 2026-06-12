---
title: "Ubuntu 8.04 Installation Problem"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by DoktorMHz on 2008-05-02
Hi all,

When I boot with the 64 bit version of 8.04 LTS Desktop Edition CD I got the main menu OK. When I choose Install Ubuntu the screens goes black with the cursor blinking at the top left and nothing happens. I've tried with i386 version and alternate version but problem remains. Any idea of what is the problem?

Thanks

Dok

---

### Post by Slim Odds on 2008-05-02
Would you care to provide **ANY** details?

Why do people not even mention the type of computer? etc.

---

### Post by DoktorMHz on 2008-05-02
Sorry. I am a newbie.

Computer: AMD 64-Bit 3.2GHz
Graphic Card NVIDIA GeForce 6600 GT AGP
RAM 2G Kingston Value-RAM
Monitor ViewSonic VA2012W

I have Ubuntu Gutsy Gibson installed and performed an Upgrade that did not succeed. After that I can't boot anymore. I decided to make a fresh 8.04 installation.

---

### Post by DoktorMHz on 2008-05-03
Well....after reading some of the many problems with 8.04 installation or upgrade I feel so bad because of my decision to upgrade. Till now no one had the same problem described on this topic. There's nothing I can do to make 8.04 work. I burned again all 3 cd's (i386, 64bit and alternate version) at low speed and I have the same problem. I can see the menu with all the option and if I choose any of the option there's a bar stating "Loading Linux Kernel" and after the bar completes 100% the screen goes black and nothing more happens. I was an addicted to 7.10 version but I've lost all the previous data.

Now my hard drive is formatted with ext3 and with a 64 bit 7.04 fresh installation. It will remain OFF until the day I can install 8.04 with no errors.

I am sorry for not being a geek. Just a curious user in search of knowledge.

---

### Post by blackwell on 2008-05-03
i got this same problem on my 

AMD Athlon 64 X2 dual 5200+

any ideas to fix it?

---

### Post by DoktorMHz on 2008-05-03
It seems that nobody has the same problem. If you find something please let me know.

Thanks

---

### Post by philhughes on 2008-05-03
> **DoktorMHz said:**
> It seems that nobody has the same problem. If you find something please let me know.

Thanks

There are others with the same problem, but no answers yet:

[http://ubuntuforums.org/showthread.php?t=765038&highlight=black+screen](http://ubuntuforums.org/showthread.php?t=765038&highlight=black+screen)

I know someone who has this problem and has tried lots of stuff to get round it, but no luck yet.

---

### Post by DoktorMHz on 2008-05-03
I tried a different approach. I installed a fresh 7.10 i386 version and immediately after that a 8.04 upgrade. After about 2 hours of downloading and installing I got several errors that aborted the whole process. This upgrade has many bugs.

Avoid it for now.

---

### Post by Jammerdelray on 2008-05-03
Try the cd checker, you'll see it in the very first window before the live cd session starts. I had a similar problem and checked the cd's and found errors, I used a different cd/dvd burning app and did not do anything else while it was burning them.

---

### Post by DoktorMHz on 2008-05-03
Thanks for the tip. This last situation has nothing to do with CD's because it was an upgrade via ubuntu system update downloading. I also checked the CD's for erros and nothing was found. This is what is intriguing me. I guess we'll have to wait for the bugs to be reported and have a stable release in some weeks.

Good Luck

---

### Post by disk11 on 2008-05-04
I have a similar problem.  I am only able to upgrade via 7.10 and doing a dist-upgrade.  The install kicks me to a command line, I just get a black screen when trying to boot the live CD, and I get no errors during the error checker.

Averatec Laptop
2200 Mobile Athlon XP
512 MB RAM
Via chipset
Rt2500 wireless

---

### Post by blackwell on 2008-05-04
on my machine boot option "pci=nomsi" helped
i use alternate cd

---

### Post by DoktorMHz on 2008-05-04
tried pci=nomsi and no success.

---

### Post by disk11 on 2008-05-04
pci=nomsi helped me install, but I could not boot into Gnome.  I tried all combinations of adding and removing pci=nomsi and acpi=noirq to no avail.  I will try XFCE or KDE at some other time.

---

### Post by texastrey1836 on 2008-05-30
I'm dealing with the same problem. So it's not like no one is having a problem. Four days of working on this makes you want to curse a bit.

---

