---
title: "Ubuntu 12.04.03 dual boot with Windows 8.1 issues"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by s.boone35223 on 2013-12-13
I read your post about [Ubuntu Secured 64 bits CD]("http://ubuntuforums.org/showpost.php?p=10084551&postcount=1")[COLOR=#000000] .  I have been fighting with my Ubuntu installation for several days with no luck.  My issue is that my Toshiba Satellite computer boots directly to Windows 8.1.  To get to Ubuntu, I have to hold the F12 key during boot to get to a Windows menu that allows me to select my boot media.  I can boot Ubuntu but it is not clean (Ubuntu hangs up during boot and restarts only after I press the enter key).

I have run Disk Repair a couple of times.  My latest BootInfo paste is located at [http://paste.ubuntu.com/6554481](http://paste.ubuntu.com/6554481).

I plan to delete my Ubuntu partitions through Windows, restart Windows using my Recovery USB to restore the grub, and then reinstall Ubunutu.  I will try the Secured 64 bit version you mentioned.  Am I on the right track or not?  Any help you can offer will be appreciated.

Thanks.[/COLOR]

---

### Post by ubfan1 on 2013-12-13
Take a look at bug #1091464  -- some machines cannot seem to successfully boot windows from grub with secure boot enabled.  I have  Toshiba Satellite S855 with this "problem", but just use F12 when I want to select the non-default OS.

---

### Post by oldfred on 2013-12-13
The 32 bit version that you have, does not have any UEFI support. You can only install in BIOS/CSM mode and boot in that mode from UEFI menu.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by s.boone35223 on 2013-12-13
I disabled Secure Boot before my initial UB 12.04.03 installation.  I have a 64 bit Toshiba and verified that it is set to UEFI boot.  It appears that UB boots in Legacy mode.  I followed the instructions outlined in the article [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).  

Is removing the UB partitions, restoring the Win 8.1 boot system, and reinstalling UB worth pursuing?  I hate to go through all of that effort and wind up in the same place.  I am afraid eventually I will lock up both my Windows and UB boot.

---

### Post by s.boone35223 on 2013-12-15
I am a beginner with respect to Ubuntu. For practice, I installed Ubuntu 12.04 initially on a 8-10 year DellInspiron.  It took two attempts to get it right.  I used Ubuntu for2-3 weeks until I was sure I wanted to install it on a new computer. I bought a Toshiba Satellite C50-ABT3N11 with Windows 8.1, 64 bit.  Iinitially installed Ubuntu 12.04.03, 64 bit.  While it “worked”,the computer booted directly to Windows 8.1.  The only way I couldget to Ubuntu was to hold the F12 key down during boot to get to theWindows BIOS boot option menu, select HDD, then select Ubuntu.  Eventhen, Ubuntu would hang up and load only after pressing the Enter keyat the point Ubuntulocked-up.


I spent the better part of 2-3 daysresearching how to repair the issue.  The moderators on the Ubuntuforum were helpful, however, they explained way more about theirrecommendations than I could comprehend.  If I understood everythingthey were explaining, I would not have needed assistance on the forumin the first place.  I kept searching, then finally held my breathand took the leap knowing I could always restore my new computer tofactory condition with my recovery media.  Following are the steps Itook to correct my Ubuntu installation issues:


1.  Download Linux-Secure-Remix 13.04(suggested by Yannbuntu).
[http://sourceforge.net/projects/linux-secure/](http://sourceforge.net/projects/linux-secure/)
Notes:  I never got Unetbootin tocreate my bootable Ubuntu USB.  I burned Ubuntu to DVD, then copiedthe DVD to USB using Windows Explorer.  I would have installed Ubuntudirectly from DVD except my Toshiba would not boot from DVD evenafter changing the boot media order in EUFI.  Rather than fight thatbattle, I took the easy way out.


2. Rebuilt the Windows Master Boot Record (MBR) using Easy BCD and then removed Ubuntu partitions (worked like acharm-Windows booted correctly immediately after this exercise)
[http://www.youtube.com/watch?v=TcE3gkzwQSY&list=PLEQyftEw4KYlFl6eQdkHV1wQaRM0z6Vv0](http://www.youtube.com/watch?v=TcE3gkzwQSY&list=PLEQyftEw4KYlFl6eQdkHV1wQaRM0z6Vv0)


3.  [Re]installed Ubuntu (13.04)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Notes:
a.  I am not 100% certain I set up myUbuntu partitions as LOGICAL the first time.  I am certain the secondtime.
b.  I set-up Logical “/” Ext 4,Logical “/home” Ext 4, and “Swap” the second installation
c.  Like the first time, once thesecond installation was complete, the computer booted directly toWindows.  I then ran Boot Repair.  The first time I ran Boot Repair,I used the default “Rename Windows UEFI” (or something to thateffect).  OldFred suggested not renaming so I made sure I did not thesecond go round.
d.  After running Boot Repair, mycomputer booted to the Grub perfectly (except for too manyunrecognizable Grub options some of which seemed to do the samething.)


4. How to customize Grub2 (boot menu)
[http://www.youtube.com/watch?v=pmFrEO-kBz8](http://www.youtube.com/watch?v=pmFrEO-kBz8)
Note:  I did not attempt to change thedelay setting-only the descriptions and Grub order.


Don't ask me any questions (I am abeginner, remember).  All I know is that my computer works exactly asI envisioned when I started the Ubuntu installation.

---

