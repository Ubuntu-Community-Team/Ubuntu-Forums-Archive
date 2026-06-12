---
title: "Grub broken + black screen on boot"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by LucienL on 2010-06-15
Hello Ubuntu forums. I'm sorry to add another newbie thread to the pile but I can't figure this one out on my own.

PC specs: i7 920, Ati HD5870, 4GB ram
Installing Ubuntu 10.04 from a USB stick. The stick is fine as I installed Ubuntu on my laptop with it no problem.

Problem #1: The grub boot manager is missing. The first time I installed Ubuntu it appeared as usual and let me choose between windows 7 and ubuntu. Due to the black screen issues I uninstalled Ubuntu. Since then, every time I've tried reinstalling it I don't get the grub boot manager, instead my PC goes straight to windows. I have formatted the partition I installed Ubuntu on, as well as installing it on another drive, to no effect.

Problem #2: After the Ubuntu splash screen, I'm greeted by a black screen. After a few seconds my monitor goes into standby. Ctrl+alt+f1 does nothing, and removing quiet and splash from the command line didn't help either. I hear I need to use vesa drivers but I have no idea how to go about this when I can't even get the OS to start in the first place.

Again, sorry for the bother

---

### Post by dino99 on 2010-06-15
[http://www.google.com/search?as_q=grub%2Bblack%2Bscreen&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=grub%2Bblack%2Bscreen&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by LucienL on 2010-06-15
Did I say something wrong? Why are you giving me such an unhelpful reply? The first search result is **this thread** and the rest are hardly relevant.

I have spent hours googling how to fix the black screen problem for the radeon 5000 series, but due to my inexperience with linux I haven't been able to get it working. Which is why I'm asking for your help.

---

### Post by stumay on 2010-06-15
> **LucienL said:**
> Did I say something wrong? Why are you giving me such an unhelpful reply? The first search result is **this thread** and the rest are hardly relevant.
 
I have spent hours googling how to fix the black screen problem for the radeon 5000 series, but due to my inexperience with linux I haven't been able to get it working. Which is why I'm asking for your help.
 
 
Here's the fix for Black Screen
 
PRess F6 during CD cycling -- starts to print to your screen this should bring up choose your language and English should be highlighted if you're using English version.
 
I had the same problem, I would run the CD installer and after the splash screen be met with Black screen, so I tossed the CD in the trash.  Problem is the ATI Graphics card, there's no support for it on the current CD from the install onwards.  But there is a workaround and it works.
 
I have ATI 5670 Graphics Card I read a thread concerning this problem with and NVIDIA card and applied the fix workaround and then when I booted into Ubuntu after the initial install, the Hardward Finder Utility (don't recall the proper name) popups and says, Your Video Card Is Not Activated, so I activated it by installing the ATI Proprietary driver which is in a Repository.  Then I went directly TO ATI Website and Downloaded the 10.5 driver uninstalled the Hardware Finder Utility by pressing Remove, installed the New Driver by following the instructions on the ATI website in small print, and wella My Ubuntu x64 is kicking butt. 
 
But to get to that point you must follow explicit instructions.  I prefer a separate dedicated hardrive for this install.  Do you have one?
 
Because dual boot scenario leaves messes.  Always.  Too much extra B.S. If you know what I mean if not, too bad, you'll experience it first hand. To avoid such disasters in the future I suggest dedicated HDD. One for each OS.  Why? It's easier to select from the BIOS Boot Option then meddling with Second, Third party software that you have to someday update and uninstall due to Guess What? New OS Revisions.  Learn from the Wise and avoid periodic mishaps.   This way when lets say, Windows Vista gets a new Brother called Windows 7, You can just buy a 200GB hdd for 50 Bucks af FRY's and added it to your system.  Pay now or pay later.  That's the defining line.  Pay later: I just described software nightmares as many have experienced AND you read them on posts through this forum and others.  IT sounds really cool to have a Dual boot machine using One HDD but in the overall scheme of things, this is called a Shortcut that leaves little to be desired by older people.  Don't have countless hours to read and countless hours to 'fix'.  Lets say it's ok to reformat your drive thousands of times, but how many times do you have to recreated the scenario before you say? Hell with this?  Have a dedicated Hardrive for each OS that way, you have that drive intact when something goes wrong, you wipe that drive and that OS not the others.
 
Oh, if people were a bit wiser instead of cheap!
 
Now on to your fix:
 
After in install the CD to the Drive, boot into Ubuntu pressing F6 key or shift or space bar.  I used F6  this brings up the Ubuntu Install Screen, Highlight "Install Ubuntu"
then press F6 to bring up the Options.  Then, don't select anything on the list, press Escape key,
 
Place your mouse on the Letter H of 'splash' backspace key to delete that word and 'quiet'.
 
It should look similar to this:
 
bunch of boot options and then 'intrid.gz -- |'
 
after the intrid.gz type 'nomodest xforcevesa'
 
it should look like this after typing:
 
Boot options bunch of lines inbetween intrid.gz nomodest xforcevesa -- | 
 
now after the Boot options there's a string of options don't type in there leave them be,
the part you need to worry about is after intrid.gz.  that's it press enter and on your way to selecting your install options.

---

### Post by stumay on 2010-06-15
Also, you may want to add:
 
acpi=off
 
this should keep the time sync issue for Windows boot.  I haven't tested that yet, but when I boot into Windows Vista, I get the time difference to the next day in Windows while, in Ubuntu, the time is correct.
 
For instance in Windows it will be 36 hrs ahead from the present time.
 
That's the problem I have at the moment.
 
If you have second thoughts about my simple and complicate method of Blackscreen find the [Solved] for this issue. It is under a post about a few days back, for Ubuntu Alternate CD method but all the same.  It works for regular method as well, for I am living proof.
 
Then you should edit your Grub, but I did not, because I did not encounter other problems.

The shift key doens't work though, it momemtarily seems to do something and then boots into Ubuntu. This is no doubt a bug, but right now I'm customizing and understanding Ubuntu, ---my first time.

---

### Post by LucienL on 2010-06-15
The uninstaller that was made with the USB stick didn't work, I got the latest version which properly uninstalled ubuntu, letting me do a proper reinstall, which let me use the options stumay just told me about, which let me boot up ubuntu, which let me fix it all.

Works fine now, thanks.

---

### Post by stumay on 2010-06-15
Hey good work!
 
Did you get to install ATI 10.5?  this fixes a bunch issues.

---

