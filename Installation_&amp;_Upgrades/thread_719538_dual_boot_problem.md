---
title: "dual boot problem"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by astd on 2008-03-09
I have installed vista and now i am trying to install ubuntu but i always get an error with xserver that i can use only low settings for now thats fine for the install , But when i continue with the install i have 4 lines and then its stack.
How can i solve it?

Thanks for helpers.

---

### Post by Pumalite on 2008-03-09
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by astd on 2008-03-09
I have tried but still not working.

---

### Post by Pumalite on 2008-03-09
Did you get the piece where it says that partition has to be made with Vista Partitioner? You cannot partition with Ubuntu Live CD

---

### Post by astd on 2008-03-09
> **Pumalite said:**
> Did you get the piece where it says that partition has to be made with Vista Partitioner? You cannot partition with Ubuntu Live CD
Yes i get that and i have a partition that have been made with vista patitioner.

---

### Post by Pumalite on 2008-03-09
Be explicit in detailing your problem to me then, so I can help you.

---

### Post by astd on 2008-03-09
When i select the option to install ubuntu from the cd i get a black screen and then those 4 lines:
* Starting deferred execution scheduler atd [OK]
* Starting periodic command scheduler crond [OK]
* Checking battery state… [OK]
* Running local boot scripts (/etc/rc.local) [OK]

and stock doesn't do anything.

---

### Post by Pumalite on 2008-03-09
Start from scratch. Download the Alternate CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less, check for CD integrity after burn and be3fore install. Clean your burners lens, just in case.Check your CD's in a different computer.

---

### Post by astd on 2008-03-09
I have tried 2 versions one a copy of a cd that i get on mail from ubuntu and one i have download and burn both works on other computers but not on mine.

---

### Post by Pumalite on 2008-03-09
Are they the Alternate CD? Clean the lens in your burner or change it. How is the check for integrity of CD after burn?

---

### Post by astd on 2008-03-09
> **Pumalite said:**
> Are they the Alternate CD? Clean the lens in your burner or change it. How is the check for integrity of CD after burn?
I dont think its the cd's because they are works on other computer's , But on mine are not.
I will try to download another copy just to check.

---

### Post by astd on 2008-03-10
Still doesn't work.
Could this be a failure with my hardware?
Maybe ubuntu is not supported with my screen or with my graphical card?

---

### Post by Pumalite on 2008-03-10
Did you download the ALternate CD iso?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by astd on 2008-03-10
> **Pumalite said:**
> Did you download the ALternate CD iso?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
 I used the altenate cd.

---

### Post by Pumalite on 2008-03-10
Check the Ubuntu site and check for hardware incompatibility. If you give me brand and model of the computer plus graphics, maybe I could help you with some boot parameters that you could use

---

### Post by astd on 2008-03-10
> **Pumalite said:**
> Check the Ubuntu site and check for hardware incompatibility. If you give me brand and model of the computer plus graphics, maybe I could help you with some boot parameters that you could use

I cant find at Ubuntu site the hardware incompatibility section.
My pc hardware is:
Mother Board: GA-K8NF-9 - Gigabyte
CPU: Amd Athlon 3500+
HDD: Western Digital 160GB X2
Graphical card: Nvidia GeForce 8600GT
Monitor: LG L226WTQ 22 inch widescreen

Tnx for you big help!

---

### Post by Pumalite on 2008-03-10
How far do you get in the installation? What are the exact error messages? Can you explain to me this better:
'now i am trying to install ubuntu but i always get an error with xserver that i can use only low settings for now thats fine for the install , But when i continue with the install i have 4 lines and then its stack.'?

---

### Post by astd on 2008-03-10
I am selecting the "start or install ubuntu" its making the progress untill its blink my screen couple times ask settings for monitor I already tryied many options from generic to low settings.
After this the installion continue and i see 4 lines:
* Starting deferred execution scheduler atd [OK]
* Starting periodic command scheduler crond [OK]
* Checking battery state&#8230; [OK]
* Running local boot scripts (/etc/rc.local) [OK]
And here it is stuck.

---

### Post by Pumalite on 2008-03-10
Try editing boot and adding vga=791 at the end of the line. (your widescreen monitor is definitely the culprit.)

---

### Post by astd on 2008-03-11
> **Pumalite said:**
> Try editing boot and adding vga=791 at the end of the line. (your widescreen monitor is definitely the culprit.)
 I need edit it at some files or something?

---

### Post by rillip on 2008-03-11
What he means is when you boot the cd, it has that list of options, like boot from first hard drive, start or install, etc.  If you hit F6 you'll get the option to edit the flags it's using. Just put vga=791 at the end after you see something like 

..... kernel (with some numbers)....  quiet noslpash --

Make it 

..... kernel (with some numbers)....  quiet nosplash -- vga=791

edit: corrected spelling

---

### Post by astd on 2008-03-13
Well, I have installed ubuntu but the xserver always crashed.
Can i fix it?

---

### Post by Pumalite on 2008-03-13
What do you mean? You finish the installation and you end up with a blank screen?
If so:
sudo dpkg-reconfigure xserver-xorg

---

### Post by astd on 2008-03-14
I have been finish the installation, Restart my pc and load ubuntu.
It is passed me right away to the command line and no xserver, When i try this command
sudo dpkg-reconfigure xserver-xorg
The command line says " command not found ".

---

### Post by Pumalite on 2008-03-14
Are 'root' at the command prompt?

---

