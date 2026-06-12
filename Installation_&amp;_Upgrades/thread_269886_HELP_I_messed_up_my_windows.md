---
title: "HELP I messed up my windows"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by nosaj97 on 2006-10-02
OK so here is the story as best as i can explain it. SO i have my windows all nice and peachy, and for some reason i decide to install linux to see if i can use it, or if i like it.  Anyways, so windows is on d: and i install ununtu on a blank c:  (both seperate 40 gig hds)  so like an idiot i didnt read anything about dual booting etc b4 i installed linux and i couldnt get back to windows.  SO, i check around the site afterwards and see that to fix this i should go to recovery console and do fixmbr command...(i should have read more but i was in a rush)  so i do this fixmbr and it says it has written a new one.  now i cant get into linux OR windows, so i got angry and uninstalled linux.

SO, i have windows on my D still... which i cannot get onto(it gives the ntldr error restart etc. 

so i try the fixboot and fixmbr and i still get this message

SO i give up and go and reinstall windows again on freshly formated C:  i go to activate it and it gives me the message"you have used this activation key too many times please use another key" ](*,)  

so now i am using windows that has 30 days to activate

all my files from the D: are intact etc i just f'd my ntldr apparently, im pretty desperate to get back to my windows thats activated and all set up the way i like it

PLEASE can anyone help me... i feel like a moron  
thanks sooo much if anyone even trys to attempt to help me
jay

---

### Post by Jussi Kukkonen on 2006-10-02
grub doesn't need ntldr to boot your windows installation, as far as I know. So, if you still intend to install linux on that first hard disk, you should be able to get everything working -- just don't rush head-long into it... Post a note if you want to do this, I'm sure someone will help.

Another choice is of course getting your current ntldr to recognise the Windows install on  the second hard disk -- questions on that might get better answers on a Windows forum?

---

### Post by nosaj97 on 2006-10-02
> **Jussi Kukkonen said:**
> grub doesn't need ntldr to boot your windows installation, as far as I know. So, if you still intend to install linux on that first hard disk, you should be able to get everything working -- just don't rush head-long into it... Post a note if you want to do this, I'm sure someone will help.

Another choice is of course getting your current ntldr to recognise the Windows install on  the second hard disk -- questions on that might get better answers on a Windows forum?

thank you for the reply i was getting desperate.... um 
if you or anyone could gimme a detailed explanation of what to do and what not to do to get this dealy set up i would b grateful... i like the linux thing, but i couldnt get to some of the windows stuff i needed to do+ its hard to go off windows cold turkey....and i was kinda scared to go into grub because i figured id just mess it up even worse.. so if someone reads this and understands the problem and what to do could you please  pm or email or something me? thanks
jay

---

### Post by crokett on 2006-10-02
I can help fix Windows.  After you run the fixmbr and fixboot commands and you try and reboot the machine, exactly what error messages do you get?  Does the machine tell you it could not find a bootable disk?  Does Windows try to load and then fail?

---

### Post by Fatjoint on 2006-10-02
> **nosaj97 said:**
> OK so here is the story as best as i can explain it. SO i have my windows all nice and peachy, and for some reason i decide to install linux to see if i can use it, or if i like it.  Anyways, so windows is on d: and i install ununtu on a blank c:  (both seperate 40 gig hds)  so like an idiot i didnt read anything about dual booting etc b4 i installed linux and i couldnt get back to windows.  SO, i check around the site afterwards and see that to fix this i should go to recovery console and do fixmbr command...(i should have read more but i was in a rush)  so i do this fixmbr and it says it has written a new one.  now i cant get into linux OR windows, so i got angry and uninstalled linux.

SO, i have windows on my D still... which i cannot get onto(it gives the ntldr error restart etc. 

so i try the fixboot and fixmbr and i still get this message

SO i give up and go and reinstall windows again on freshly formated C:  i go to activate it and it gives me the message"you have used this activation key too many times please use another key" ](*,)  

so now i am using windows that has 30 days to activate

all my files from the D: are intact etc i just f'd my ntldr apparently, im pretty desperate to get back to my windows thats activated and all set up the way i like it

PLEASE can anyone help me... i feel like a moron  
thanks sooo much if anyone even trys to attempt to help me
jay

Sounds like your boot.ini file on your 2nd disk isn't correct.

Essentially, depending on if your Windows HDD is the second or first drive in the IDE chain, you probably need to change the line in boot.ini to reflect this.

A great site for an explanation on boot.ini is: [http://www.geocities.com/thestarman3/asm/mbr/bootini.htm](http://www.geocities.com/thestarman3/asm/mbr/bootini.htm)

```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

This is my boot.ini, under the header [operating systems] I'm taking a guess and thinking the first IDE drive in the chain is the drive in which Ubuntu has been installed.  So, you'd probably change the portion in where it tells Windows to find the Windows partition:

multi(0)disk(0)rdisk**(1)partition(1)\WINDOWS**="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

note it could be partition(0) so if it doesn't work, try again with that one.

multi(x) = drive controller (Primary or Secondary IDE channel)
disk(x) = always set to disk(0) unless you are using SCSI drives.
rdisk(x) = the drive in which windows is installed (0=master drive, 1=slave drive)
partition(x) = the partition in which Windows exists.
\WINDOWS = the actual directory to which Windows is installed.  Be careful here, I ran into a drive where Windows 2000 was installed originally, then upgraded to XP.  The default directory for Windows 2000 installations is \WINNT.  If XP wasn't upgraded, or if it was a fresh install, the default directory should exist as \WINDOWS.

**MAKE SURE TO WRITE THE INFORMATION DOWN EXACTLY AS IT APPEARS SO THAT IN CASE ALL YOUR EFFORTS PROVE FRUITLESS WE'RE AT LEAST STARTING BACK AT THE POINT IN WHICH IT'S BROKEN.  NOTHING IS MORE FRUSTRATING THAN GUESSING LIKE CRAZY AFTER FILES HAVE BEEN CHANGED.  KEEP A NOTEPAD OF WHAT YOU'RE DOING FOR EVERYONE'S SANITY.**

---

