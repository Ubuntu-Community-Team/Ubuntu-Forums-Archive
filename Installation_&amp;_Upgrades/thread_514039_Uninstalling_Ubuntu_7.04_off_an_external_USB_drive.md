---
title: "Uninstalling Ubuntu 7.04 off an external USB drive whilst keeping the Windows XP"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by spyz on 2007-07-31
I have installed Ubuntu on my home PC. I use a dual-boot setup with both Ubuntu 7.04 and Windows XP installed&#8230; I have realized that this is pretty common but with my system there is a BIG catch.

Ubuntu 7.04 is installed on my external hard drive connected over USB. And at the same time I have Windows XP running alongside in Dual-boot on my internal computer drive, but every time I start want to start Windows XP I need to go through the GRUB loader to start it.

Basically I want to get rid of or uninstall Ubuntu from the external drive and revert my system back to how it was as a single booting Windows XP system. I have looked at various online guides, and have repeated several times the use of the Repair Console on the XP disc using &#8220;fixmbr&#8221; and other boot record restoring commands, but none of these work because my external hard drive where the grub loader and Ubuntu is installed will refuse to be recognized by Window&#8217;s XP&#8217;s disc recovery module.

All I want to do is have a normal Windows XP system that boots onto the single XP OS without the grub loader, or if that isn&#8217;t possible would it be possible then to set Windows XP as the default OS in grub loader? It is a very messed up situation seeing as I have used an external drive to install Ubuntu on, for which I regret and would not recommend to anyone.

I&#8217;d really love any sort of response&#8230; Hopefully you understood all that


Edit: Id also like to note that when my external drive is not plugged in the GRUB loader which allows me to select from either Ubuntu or Xp will only load fully and properly when the external drive is plugged in at startup. When the external usb hard drive is plugged out at startup the grub loader wont load so I dont get a choice to load any operating system, but I do get an error message which i believe is "Error 21" ... basically I just want to revert my computer back to a single-booting XP system whilst keeping my internal hard rive computer content intact. For some reason the GRUB loader seems to have taken over the whole boot process for the operating systems on my computer and seems to be written onto both the external drive and internal (computer) drive, however it only loads fully and properly when the external drive is plugged in otherwise I will get an error message. Does ubuntu offer an uninstall feature? I basically would like to revert back to single XP booting without the GRUB loader interfering every time I start up my computer.

ANY Help would be appreciated as I have been baffled over what has been going on for quite some time now... so ANY assistance would be VERY VERY much appreciated...

Thankyou =D

---

### Post by peachy on 2007-07-31
Hi, you need to run fixmbr on your internal drive, not the external

---

### Post by DerHesse on 2007-07-31
You will find the list of bootable Operating Systems in /boot/grub/menue.lst
which is located on your USB-Drive. Therfore you cannot boot whilst the external drive is not connected.

fixmbr and fixboot in the Windows Recovery Console will do the job. Just to be sure donot have the USB-drive plugged in while you are doing that.

---

### Post by spyz on 2007-07-31
I already ahve tried both fixmbr and fixboot in the recovery console and neither has worked. When the external drive is plugged in windows recovery console recognises only the external drive and says that it can find no windows installations (which is obviously the case), when the external drive is plugged out it recovery console recognises not hard drives at all, it seems to be thet the GRUB loader is embedded in both drives (internal and external) and is stopping the recovery console from functioning properly and allowing for use of the fizmbr and fixboot.

---

### Post by Pumalite on 2007-07-31
Are you sure you have gone through: 'r'>FIXMBR>FIXBOOT?

---

### Post by spyz on 2007-08-01
Ok.. maybe I havent done the fixmbr and fixboot correctly... if possible could someone please explain how to do it properly, considering my hardware setup (internal & external drives) ... do you need to type 'r' in the recovery console? Im quite sure I have dont it right... but If anyone has any other ideas it would be greatly appreciated =D

---

### Post by chrisbruno on 2007-08-03
Hello glad to be of help,  I am an extreme noob but have been doing the homework on all sorts of ways to install/re-install/the best way to install/requirements  etc...etc... 

And 

I Wanted to be the first to give advice on this topic as i have been searching for days on an answer.  You'll have to do the leg work yoursel (ei - search the web) I  have  windows vista os and i used SUPER GRUB BOOT to get ride of my problem. its compatible withe most windows os's, i was worried it would'nt work on vista as it wasn'nt specified that it would at all  (not like MbrFix.exe as they post) That should solve your problem quite easely

now that we past that problem

What i'm look is how to get Ubuntu 7.04 installed  on an external hard drive without putting the grub on the main drive 

I had read on a post that using the alternate cd (advanced settings) could give you the option to install the grub on a seperate drive by ( after installing, you keep the cd in the drive , then run the cd for repair or recovery?  or even reload or fix the initial install?) But this might only work with that alternate cd 



I also have noticed that on my system Dell inspiron 9400 that past programs had difficulty with certain chipsets and drivers but mine loaded no problem - just went to start or install (first option when cd loads)

+- but then the grub loads on the main drive)-+

 instead of load in graphical mode (option 2) like youtube sudjested for my type of computer.  

Maybe you guys can look for the right way to install on external drive then somehow post it on the support pages 

This is a very good post by the way, They should make this a easy install guide for the problems we've been having as IT IS HARD to find ANYTHING relating to our noob F%$@ ups.

any help would be very very much appreciated, and i think i could speak for the all and future people searching for the same problem....... Thanking you in advance.  

And i'm glad i came accrossm this thread,  i'll be looking to figure this out and hopefully one of us will come across an answer, that is if i don't find it first ha just kidding.

---

### Post by chrisbruno on 2007-08-03
UREKA, I found it on previous posts, dont know if they'll work.  going to try it tonight will post back results.

 SUCCESS - Dapper Drake loaded on external USB drive! [taken from DaBruGo Breezy post] 

--------------------------------------------------------------------------------

This is the procedure I took for a brand new install of Dapper Drake based on the procedures from DaBruGo's Breezy post.

Disclaimer: This way worked for me, but I'm a complete noob and this was my first ever install of any flavor of Linux.

FYI, this was a clean install on a 30GB USB drive I didn't care about formatting/losing data on. I screwed up the MBR (master boot record) using the method for Breezy and completly freaked out. Fixed it using one of the MBR tools [Partition Table Doctor] on Hiren's BootCD.

** It goes w/o saying, backup all your stuff first **

( STEP 1 ) Download Ubuntu Dapper Drake 6.06 - Alternate Install CD. [Haven't tried it with the regular Desktop CD] Burn the image. Restart your computer leaving the CD in.

( STEP 2 ) Change the boot order in your BIOS to: CD, USB, Hard Drive. Press F2 or whatever your computer setup is. Plug in your USB drive and save changes. You're computer should restart.

( STEP 3 ) Your computer should now boot the CD. At the boot prompt select the first option to Run/Install Ubuntu [You may also want to come back here and try the safe graphics mode if these steps don't work].

( STEP 4 ) You should now be at the Ubuntu desktop. Click on the Install icon. 

** CAREFULLY READ DaBruGo's post steps 2 and 3 **

( STEP 5 ) Follow the prompts and complete the information. When at the Partition screen MAKE SURE TO SELECT SDA/SCSCI drive, NOT THE HDA (your hard drive on the computer). I selected Erase the entire disk option. Proceed, it should now start to install everything.

( STEP 6 ) When the Install has completed you will be prompted to either Continue or Restart. Select Restart.

** THIS IS WHERE THIS PROCEDURE IS DIFFERENT FROM DaBruGo's **

RESTART WITH CD EJECTED and leave your USB drive plugged in.

( STEP 7 ) GRUB should have loaded. Select the first (of three - others are rescue and memtest).

SUCESS! That was it. I downloaded a ton of updates and had a wonderful day!

No code editing for me!  

Shant

ps. Big ups again to DraBruGo for his original Breezy USB drive install post.

---

### Post by chrisbruno on 2007-08-05
ok,  have been trying for a couple of days and could'nt get it to install properly tryed the advanced cd and the live cd . With both versions i get the same result - grub boots up, try to select all the options even the one with my vista on it error 17 shows up in ubuntu and error 22 for the windows .  Oh by the way,  i think when i use supergrub boot cd it loaded a windows vista boot sequence, cause when i see the grub menu it shows a xp version.  got me into vista thats all that matter

 anyway the super grub cd got me to boot from my usb i booted from the mbr on the usb that was there i did'nt fix it , its the original and it works but when i go to boot from the drive nothing just the error 17 

so i'm sticking with the grub for now until theres a better alternative fix 

what i'm stuck on now is getting my dell wireless 1390 wlan mini-card supported with the right drivers and how to do it, any help feel free

---

