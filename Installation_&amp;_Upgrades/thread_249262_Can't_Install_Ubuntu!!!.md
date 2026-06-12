---
title: "Can't Install Ubuntu!!!"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by Apoorv on 2006-09-02
I got the ubuntu 6.06 iso image from a pc world (magazine) dvd. i burned it to a cd and booted from the live cd. but when i started installing ubuntu and reached step 5, that is partitioning, the system gets hanged and i am forced to reboot. my system configuration is - pentium 4 - 3.00Ghz, intel D101ggc motherboard, sony DVD+RW drive, 256 MB DDR ram, and seagate 80gb sata hard disk. could anybody please help me with this problem?


(P.S. - i installed xubuntu from the same DVD which is working fine)

---

### Post by whizbaby on 2006-09-02
Try:
downloading the alternate install-cd and burning it at slow speed (4x or 8x).
Any change?

---

### Post by Apoorv on 2006-09-03
ive recieved the shipit cd's of ubuntu.....and i still have the same problem.........

id like to tell you that earlier when i tried to install ubuntu, the live cd itself took 10 mins to reach the desktop......and it hanged when i clicked on the install icon. but when i installed xubuntu, the ubuntu live cd booted up quite faster but this time got stuck on the partitioning step.

pls help....

---

### Post by sharperguy on 2006-09-03
how long did you leave it to make sure it was hagning and not just beings slow for lack of ram?

Also the alternate cd would be an idea (text only)

---

### Post by Apoorv on 2006-09-03
i left it for about 10 mins......and did a thorough checking......i tried to move the mouse for abt 5 mins.......i also tried to take out the cd.....but nothing seemed to work.........and as i have 10 ubuntu cd's , i tried 5 of them.....all of them get hanged at the same instant.

---

### Post by Apoorv on 2006-09-03
also as i have a 400 mb download limited internet connection.....i can't download the alternate cd.....can i order the alternate cd from ship it?

---

### Post by ri60 on 2006-09-05
i have de same proble... i have a dell optiplex 9150 and SATA (250gb)... i cant see my sata .. the installer program cant find any hd on my pc... the installation hung up on step 5 of 6..i can run ubuntu but only live version.
i tried with gnome partition editor and it couldnt find my hd
'no devices detected'

I see many posts about this issue  but nodoby has the solution

i tried too make partitions (ext3 y swap) with partition magic and nothing happen... the problem still there... help me plz!!

---

### Post by jose2k72 on 2006-09-14
I have the same problem too, i have a D865GBF or D865GLC (i'm not sure) Celeron D, 256MB RAM, IDE 80GB, CD-48x. The installer hung up in some step. I wait for this 30 minutes more or less.

Also I have a D101GGC Celeron D, 512MB RAM, SATA 80GB, CD-48x. The installer detect all very well except the graphic card and only show the livecd in VGA (640x480) i try to select all de options, inclusive in the partitioning process. But here i can not continue because I can't see the buttons and i try to continue with the return key (like i do in the previous steps) and nothing happen.

The CD is a copy from one shipit cd that was installed in an asus motherboard whitout problem.

The instalation is in a PC with WinXP too.

---

### Post by realtenchi on 2006-09-15
me too..... ive got a Asus P5V800-MX motherboard, 40gb [COLOR="Red"]SATA[/COLOR]Maxtor HDD, 512mb of RAM but, like all of you posted earlier it hang up at Step 5 while installing Ubuntu..

Ubuntu Masters!! Help Us!!!

thanks
Realtenchi

---

### Post by tmcahow on 2006-09-15
I also have the same problem as noted in my previous post, see Linux installation problems.

Here are my specs again

AMD 64+ 3400 @ 2400mHz
1.5Gb memory
1st hdd 160Mb
2nd hdd 300 Mb
Nvidia GeForce 5200
On board sound card is AC97
Windows XP running on first partition (100Mb) works like a champ (as much as i hate to say that).

Hopefully these thread offers more help than the previous one!

---

### Post by whizbaby on 2006-09-15
Stop me if I say something stupid, but can this whole SATA issue have anything to do with the windows installation? This came to my mind reading the *dell optiplex* post from ri60. We bought 30 of them a couple of months ago and had no problems to install (x)ubuntu on them from (the same) CD (we tried five and synced the rest). So on identical hardware the installation is possible on the comp not having XPensive installed to it? (However, who could say how *identical* the hardware from dell really is...(different cd/dvd-rw's?)). Has any of you guys a spare HD (or could lend a blank one), and is willing to plug it in and remove the XP-HD and see if there's any difference?

---

### Post by 4Foot on 2006-09-15
In response to the request to try and emulate this installation problem with a separate drive I offer the following info which I had been preparing for a separate post. I sure hope someone has an answer.


I have been trying to install Linux on my PC without success, I would appreciate a little guidance as to what I may be doing wrong.
System:

Asus KV8SE Deluxe
AMD64 2.2 GHZ
1.5 Gigs Ram
ATI AIW 9800 video/TV card

I have an extra drive, an SATA 70 Gig Raptor which I have been using to test Vista and just hook up as C: when I want to play, otherwise I have XP on a different drive, I am not interrested in dual booting.

I have DL'd both the 64 and 32 bit versions of 6.0.6 Ubuntu, burned the ISO to a boot disk and the both boot fine from my optical drive. After a couple of pages of install log data scrolls by, all of which looks OK to me the system says to wait and then just goes dark and stays that way until I quit.

Thinking it might be an incompatability with Ubuntu and my system I DL'd a Knoppix Live CD distro and experienced the exact same problem.

I stongly suspect that both of these distro's have a problem with my ATI All in Wonder card which has always been a problem keeping up to date with drivers in XP as well. ATI are very poor at support. They seem to think that everything else should change to accommodate their hardware. I do like to capture TV progs however so I am reluctant to just move to a stand alone vid card just to test Linux.

I have abandoned any attempt to try Linux a number of times but keep coming back thinking I can figure it out. I would hate to quit on it if I am doing something stupid or missing something that can be easily fixed.

Any suggestions would be very welcome.

Thank you 

4Foot

---

### Post by dkartik on 2006-09-15
I had the same problem when I tried installing on one of my computers at home.  I've had it working at work for months now, so I was baffled that the installation didn't work again.  However I did get the installation to work finally!  You need to download the alternate cd iso file.  Browsing through the forums,  I've noticed a lot of people who have had the same problems, but using the alternate cd, which runs a text-based installer, should work in all cases.  I remember one of you had mentioned that you have a limit on how much you can download in a month, I'd encourage you to either get a friend who might have a different type of connection to download and burn the alternate cd for you.  It'd be a great opportunity to share linux with that said person as well.  If you don't have someone who can download it for you, PM me and I'll see what I can do to get you a copy.  Anyways, good luck to all.

---

### Post by Veso on 2006-09-15
> **whizbaby said:**
> Try:
downloading the alternate install-cd and burning it at slow speed (4x or 8x).
Any change?

**[COLOR="Blue"]No change ](*,) [/COLOR]**

---

### Post by GSMD on 2006-09-16
That's the kernel problem. You can try to fix it as described [http://www.geocities.com/rajahuroman/main.html](http://www.geocities.com/rajahuroman/main.html)

---

### Post by Apoorv on 2007-02-19
Ok, now I've returned to this forum, after 4 months. I've emerged as a stronger, and more experienced Ubuntu user. I'm now using Edgy Eft. But still I have so many problems, to which I was unable to find a solution.

---

### Post by SimonG on 2007-02-19
> **jose2k72 said:**
> Also I have a D101GGC Celeron D, 512MB RAM, SATA 80GB, CD-48x. The installer detect all very well except the graphic card and only show the livecd in VGA (640x480) i try to select all de options, inclusive in the partitioning process. But here i can not continue because I can't see the buttons and i try to continue with the return key (like i do in the previous steps) and nothing happen.

I too had this problem when installing Ubuntu. I discovered if you press Alt+F7, then move the dialog with the cursor keys, then press Enter, you are able to interact with the parts of the dialog previously off-screen.

I'm surprised the installation dialogs are so large if the installer would default to 640x480.

---

### Post by floke on 2007-02-19
Not sure if this would work as a workaround (let me know if it does since I have a friend who can't run the LiveCD, though xubuntu works, and they are a bit leery of installing ubuntu if they can;t see it work first) - could you install xubuntu and then use this to download the ubuntu desktop - ie sudo apt-get install ubuntu-desktop - wouldn';t this then pull in ubuntu on top of xubuntu? You would then be able to select ubuntu from the login menu and viola!

That's the theory anyway. Will it work?

---

### Post by whizbaby on 2007-02-20
On a Dell Optiplex 745 I had to pass a kernel option to make it install correctly:
after the 1st graphical menu pops up (start/install menu) hit F6 and add
noapic 
right before the final -- of the line that pops up. I think this is due to the sata dvd burner that is built in that machine.

---

### Post by patlew on 2007-02-20
I had the same problem and tried everything.
The answer is 7.04
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Apoorv on 2007-02-20
What is this minimal CD?

---

### Post by patlew on 2007-02-20
Only 8 mb.
Burn it and test.

---

### Post by Apoorv on 2007-02-21
Ok...thanks.

---

### Post by ri60 on 2007-03-09
nobody has the solution :(
what´s is the problem?? ubuntu dont support well SATA??? what i do wrong?
i will try with openSuse 10.2 and Mandriva 2007....

---

### Post by Markus72 on 2007-03-09
Hi,

although I know it's of no use for solving you problems:

I had problems installing Ubuntu on a machine with sata disk, too.
It tried it with two motherboards (msi k8t, asrock something I've forgotten).
I even had problems with a unused sata disk only attached. say: on a system with two drives (one ata, one sata) I had problems to install Ubuntu on the ata disk.
It only worked with the sata controller switched off!!

I experienced hang ups during live cd boot and at every stage of the installation procedure (and in fact, I tried really often) and also during partitioning.

So, I started - since I desperately wanted to get rid of windows - to switch of the sata controller permanently when working with ubuntu and installed it on a ata disk.

Funny: after a while (I can't even tell if after the first update or already from the very beginning) I found out, that my current installation (booting from the ata drive) now perfectly accepts the sata disk. Don't ask me why.

Markus

---

