---
title: "2nd OS Reversed 'Default' Menu"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by ChrisNZ on 2010-06-06
I had installed Ubu 10.4, I installed a 2nd OS (Xubuntu in this case) and I must have ticked a installation box somewhere so the end result (after Xubuntu installed) was the the Grub2 Menu Reversed the default listing table, so Ubuntu is now 5 or 6th down the list and Xubu is now _1st_ on the list and becomes default startup.

I hope this makes sense? :)

So what i'm looking for is a 'edit' control for the menu so I can change the default list to tell the system to 'pick' line 5 or 6 and that becomes the new default or I 'cut and paste somewhere' LOL

I loaded a Terminal program called Startupmanager, but did not seem to get the desired result, you may know this program and can understand why?

Can you help?

Thanks in Advance.

---

### Post by Revolutionary101 on 2010-06-06
To edit my GRUB 2 config I use startup-manager, but its not terminal based. Check to see if there is a GUI for startup-manager in System>Administration>StartUp-Manager.

You might have made a mistake with the terminal based version. By using the GUI it may make it easier for you to change the GRUB config.

---

### Post by ChrisNZ on 2010-06-08
Hi Rev'101

Yes I have tried that thanks, however I'm lead to believe that since Xubuntu hold 1st place for menu listing then I need to change it's grub menu and not Ubuntu's. So tonight I tried that, however in the /boot folder I did not have a "Menu.lst" file at all, and I was unsure of touching anything else so I left it. I intend to ask on the Xubuntu forum list to see what they say the file is or might be and then try again.

Thanks

---

### Post by darkod on 2010-06-08
If you wanted Ubuntu grub2 to run the show, you needed to click on the Advanced button during the Xubuntu installation and select not to install a bootloader (grub2). You need only one grub for linux. No need to install new one with every installation.

If you want Ubuntu grub2 to be main, boot into Ubuntu and in terminal do:

sudo grub-install /dev/sda

I am assuming you have one hdd, /dev/sda, if the ubuntu is installed on another hdd, just change the name. If you are unsure, ask.

That will install Ubuntu's grub2 back to the MBR of the disk.

---

### Post by ChrisNZ on 2010-06-20
Thanks folks, however due to another update issue 10.04 started a loop at login and the system became unusable. I ended up removing Xubuntu, reinstalled ubu 10.04 in it's place and then successfully lost 25% of files during a copy past from the old one! ](*,)

Now looking at data recovery software for the HDD :(

This thread is now closed - hope it helps others though.


"Remember - a backup a day keeps you sane"!

---

