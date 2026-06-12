---
title: "upgrading Ubuntu to Ultra Edition 1.5 on Vista System"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by howardavatar on 2007-10-06
I have Ubuntu 7.04 installed on my Duel boot system(Vista/Ubuntu usiung Wubi). I wish to upgrade to the Ultimate Edition 1.5(I have the DVD). What is the best way of doing this without effecting Vista?
My system is:
E6750 Duel core CPU
1 gig ram
ATI Radeon X1900 Video
Winfast DVT 1000 TV Digital TV card.
Gigabyte GA-G33M-DS2R/S2
2*2GIG SATA Hard discs
LG DVD Burner
Philips 66CM LCD TV/Monitor
TIA:)

---

### Post by PmDematagoda on 2007-10-06
The only differences between normal Ubuntu 7.04 and Ubuntu Ultimate 1.5 are that UUE contains more preloaded programs, is more updated and has a nice theme:). Since there is no difference concerning the system cores I do not think you can upgrade 7.04 to UUE 1.5 unless of course you install the exact same programs, settings, updates and themes as given by UUE on your existing Ubuntu installation. Another thing is that an upgrade using the CD is something that doesn't seem to have been attempted or for whatever attempt has been made was a failure.

So all in all you would be better off installing UUE 1.5 as a clean installation if you want to use it.:)

---

### Post by howardavatar on 2007-10-06
So how can I do that without touching Vista on the 1s HD?  Can Wubi be used to install UUE 1.5 instead of basic Ubuntu?  If so how?  So I can duel boot betwwen Vista & UUE 1.5?
TIA :)

---

### Post by PmDematagoda on 2007-10-06
Is this right?

> 2*2GIG SATA Hard discs

Now you run Ubuntu virtually right? So you want to use UUE separately? If so it would be easy as long as you have two hard drives.

---

### Post by howardavatar on 2007-10-06
that 2*200 gig Hard drives (sorry).  I just used Wubi to install Ubuntu on the 2nd 200GIG HD.  Then just Duel boot between the 2 OS.   So is there a guide that can show how to install UUE 1.5 on my 2nd HD in the same duel boot mode with Vista?
TIA:)

---

### Post by PmDematagoda on 2007-10-06
I believe it to be more safer for you if you install UUE 1.5 by booting it.

You can use this guide:-

[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)

---

### Post by PmDematagoda on 2007-10-06
Though I think you should be able to install Ubuntu just as normal.

I installed Ubuntu on one hard drive and XP on the other, one thing to remember is that you should first install Vista then Ubuntu since if you do it the other way then Vista's bootloader will overwrite that of Ubuntu's which prevents you from accessing Ubuntu.

---

### Post by howardavatar on 2007-10-06
Thanks for that :)
I have noticed 1 problem when booting for the UUE 1.5 DVD.  I get to the first screen where I choose start/install UE 1.5 but 1 minute or so after I choose that opor or the safe video option I loose video sync (there is no video signal to my 66cm LCD screen) form my ATI X1900 video card.  What can I do to stop this?
TIA :)

---

### Post by PmDematagoda on 2007-10-07
As I use an Nvidia VGA card I'm afraid I can't help, sorry:(. But most probably you will get help concerning this matter so stick around for a little.

---

### Post by howardavatar on 2007-10-07
I fixed the Video problem.  But from all the guids you gave me links to I am confused which one to use.  I have Vista (I want to keep) on my 1st hard drive (master boot) and the 2nd I have Ubuntu.  I wish to install UUE 1.5 on this 2nd drive.  Keeping the current ability to duel boot betwwen Vista & Ubuntu.  So which guide should I use to achieve this?

---

### Post by PmDematagoda on 2007-10-07
I'm afraid there may not be any guide to help you achieve what you want.

Now the thing is that there is no way you can upgrade your Ubuntu 7.04 to UUE 1.5 since the base OS is the same. So your best bet is to do a clean re-install of Ubuntu. I do not think there may be any problems concerning Grub since Ubuntu will update it when it is being re-installed.

---

### Post by howardavatar on 2007-10-07
So Grub will replacce Vista's current bootloade(Which ATM lets me choose betweeen Vista & Ubuntu). 
So I take it my 1st step would be to uninstall Wubi/Ubuntu from 2nd hard disk?
Then boot of the UUE 1.5 dvd?
Then install UUE 1.5.  I take it I should choose under"prepare disk space" I should choose 2nd option I should choose use "Guided - use entire disk" and select the 2nd hard disk?
If I do it this way will it correctly import Vista into Grub and allow duel booting with grub?
TIA:)

---

### Post by d_iane1954 on 2007-10-07
> **howardavatar said:**
> So Grub will replacce Vista's current bootloade(Which ATM lets me choose betweeen Vista & Ubuntu). 
So I take it my 1st step would be to uninstall Wubi/Ubuntu from 2nd hard disk?
Then boot of the UUE 1.5 dvd?
Then install UUE 1.5.  I take it I should choose under"prepare disk space" I should choose 2nd option I should choose use "Guided - use entire disk" and select the 2nd hard disk?
If I do it this way will it correctly import Vista into Grub and allow duel booting with grub?
TIA:)

i  do believe as stated earlier that a fresh install is needed to run uue,currently am running windows xp 2000 and ubuntu ug off one drive.when installing over your ubuntu 7.04 if you use the manual format option you will be able to chose your second hard drive as the place you want to install your new uue. then just chose format complete drive as your option.hope this helps!!!!

---

### Post by howardavatar on 2007-10-07
Ok I did a fresh install of UUE 1.5 on 2nd drive.  Then on reboot after I chose Ubuntu on Grub boot menu I get the blue Kubuntu screen then  a blinking white underline cursor top left corner of the screen.  Also is it normal for vista not to see 2nd hard drive at all?
TIA:)

---

