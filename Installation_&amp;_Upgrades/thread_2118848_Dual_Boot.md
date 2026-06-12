---
title: "Dual Boot"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by Tanavar on 2013-02-22
Hi guys,

Just wiped my tower and upgraded parts, i have reinstalled Windows XP.

I used to have dual boot with Ubunto 10 (i think it was 10 anyway). i had installed it on one HDD that was partitioned 50/50.

I have now got 2x 500gb HDD's in my computer so i was wondering is it worth putting linux on one and Windows on the other but not to O/S dual boot instead i would select the boot drive from the M/B prompt screen that is enabled in BOIS or would it be better if i just to install linux so that a O/S prompt (GRUB Loader) comes up saying which O/S to load?

only thing i'm thinking of is Installing it so that i have to choose what drive to load from using the M/B menu would leave the windows copy untouched as Linux will make changes to windows for dual boot to work otherwise

---

### Post by dave2001 on 2013-02-22
My first thought is that Windows XP will soon be a dead operating system. MS is ending their extended security support in less than a year (iirc). With that in mind.. you might want to make the switch to full Linux on that computer.

However if you do want to have both WinXP and Ubuntu, I'd stick them on one drive for simplicity and configurability (if that's even a word). 

With windows and linux in separate partitions on the same drive, you can use either grub or the windows boot manager as your primary boot manager. Either way you'll probably need to do a little configuration to get things booting up just the way you want.

---

### Post by oldfred on 2013-02-22
I prefer to have at least one operating system on every drive and keep Windows on its own drive.
Hard drives fail and if you have both systems (or parts of) on one drive  and that is the drive that fails you cannot boot. But if two drives you should be able to boot the other drive.

Just keep Windows as sda as XP is hard coded in boot.ini to be the first drive. You would have to change boot.ini if not sda or drive0 in Windows.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Tanavar on 2013-02-22
Thanks all, just installed ubunto on the 2nd HDD,  oldfred that was also my thinking about if the HDD fails so have do it that way.

The only reason i still have XP on my tower is due to the software i use (eg dreamweaver) i also have a laptop which runs Windows 7 but i really can't be bothered to buy Windows 7 for the tower as well due to not needing it, 

I like to keep my web programming (Tower) and game, music etc (laptop) separate as the laptop get used by family member and sometimes taken to other people's houses for me to do repairs on their PC's also the config i have on my tower is 3 screens (had 2 one for the coding and the other for preview but was given another for free so its got a KVM switch on it for laptop as well as tower :P) 
 
Unless there is a way to run Dreamwaver inside ubunto (without a program like wine) i think i will be keeping XP :P

---

### Post by pfeiffep on 2013-02-23
> **Tanavar said:**
> Thanks all, just installed ubunto on the 2nd HDD,  oldfred that was also my thinking about if the HDD fails so have do it that way.

The only reason i still have XP on my tower is due to the software i use (eg dreamweaver) i also have a laptop which runs Windows 7 but i really can't be bothered to buy Windows 7 for the tower as well due to not needing it, 

I like to keep my web programming (Tower) and game, music etc (laptop) separate as the laptop get used by family member and sometimes taken to other people's houses for me to do repairs on their PC's also the config i have on my tower is 3 screens (had 2 one for the coding and the other for preview but was given another for free so its got a KVM switch on it for laptop as well as tower :P) 
 
Unless there is a way to run Dreamwaver inside ubunto (without a program like wine) i think i will be keeping XP :P

I followed oldfred's advice and left my win7 installation on ssd alone, and installed 12.10 on my second internal hdd. 
One advantage of this is grub provides the ability to boot either win7 or ubuntu as long as I have bios configured to boot sdb 1st;)

---

### Post by oldfred on 2013-02-24
You may eventually have issues with a SSD & XP. It is my understanding that you have to have AHCI on for trim to work. And XP does not normally have the AHCI drivers. I ended up shutting down my XP install when I got my SSD last year. Of course I had said for 5 years prior that I was going to stop using XP, but that one application kept me on it. I was have to turn AHCI off in BIOS and reboot into XP, but that was too much hassle.

And you need to look at the alternatives to Dreamweaver. None will be the same, and if you have learned certain ways to do things it can be a lot to change to a new way. 

       Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

   Best Free Software for Linux
[http://www.techsupportalert.com/content/best-free-software-linux.htm](http://www.techsupportalert.com/content/best-free-software-linux.htm)

---

