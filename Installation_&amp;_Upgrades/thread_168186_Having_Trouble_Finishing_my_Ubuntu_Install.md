---
title: "Having Trouble Finishing my Ubuntu Install"
date: 2006-04-30
forum: Installation &amp; Upgrades
---

### Post by Avenue on 2006-04-30
Hello Everyone, 

I feel very stupid here, but I don't know what else to do.  I ordered new CD's of Breezy Badger 5.10 directly from Canonical so I am not burning my own ISO images.  Here's what happened:

1)  I put the CD's into my system and started a normal install, this included language, time, etc.  

2)  After about 20 minutes (or thereabouts), it told me that I needed to reboot in order to finish installing the packages, then my CD tray opened automatically and I took my CD out.  I should also mention that I was able to create my root user and user name at this stage.  

3)  After rebooting, I get the message "INVALID DISKETTE.  PLEASE INSERT A DISKETTE INTO THE A:" - looks like a DOS prompt to me...

4)  I shut down and tried rearranging my BIOS so that my hard drive would boot before my A drive, but that did not help.

5)  Next, I put the Ubuntu CD back in the CD tray and rebooted.  It ended up taking me all the way through setup and install all over again.  

I cannot find any workaround in the documentation, or at least not any that jump out at me.  I'm just really now learning more about computers and other operating systems, so I feel like i'm really stuck.  

Can someone help????

Thanks so much for any help any of you can give!!!

'til then...

Ave

---

### Post by chriscando on 2006-04-30
Did you recall installing the grub bootloader during your installation?  To me, sounds like your system is trying to boot the wrong partition.  If this is the case, I have heard of people hitting 'Esc' when the installer comes to the user setup and being taken to a menu that can skip straight to the grub installer first.

---

### Post by Kethinov on 2006-04-30
That is very strange. My first guess would be that the BIOS is looking for a bootloader on the wrong hard drive. Do you have multiple hard drives?

If not, then I'm forced to wonder if your disk is correctly partitioned, but even then...

---

### Post by Sef on 2006-04-30
> I ordered new CD's of Breezy Badger 5.10 directly from Canonical

Just because the disks are from Canonical doesn't mean that they are good.  They do at times ship out bad disks.

> 2) After about 20 minutes (or thereabouts), it told me that I needed to reboot in order to finish installing the packages

That is too short of time to do correctly.

> I should also mention that I was able to create my root user and user name at this stage. 

If you created a root user during install, that is a problem.   Ubuntu don't set up root; it uses sudo - a fake root.

---

### Post by Avenue on 2006-04-30
I forgot to mention that I am not using multiple hard drives.

Also, I thought that the bootloader is indeed loaded, and that's why the CD ejects.  It mentions something about rebooting to finish the package install...strange to me.  Once again, I did re-order my BIOS but that doesn't seem to do anything, just keeps asking for a diskette in the A:.  

Now, quick question here regarding the "ESC" key when the installer comes to the user setup:  Will I have to go through the installation process again in order to get to this step?  

Thanks Everyone!!!

Ave

---

### Post by Avenue on 2006-04-30
I'm not exactly sure what your point is, Sef.  Are you here to give criticism or to possibly help?  I believe that I said that I do not know much about computers in general right now, much less Linux.  

If you have any information that I can use, I'd certainly appreciate it.  

Thanks!!

Ave

---

### Post by Kethinov on 2006-04-30
Okay, maybe GRUB installed its bootloader to the wrong hard drive. Go into the BIOS and reverse their boot order. See if that helps.

---

### Post by Avenue on 2006-04-30
Thanks for the help, Kethinov.  Going back into the BIOS didn't seem to work either, i'm going to try re-installing and then hit the "ESC" key after everything is done.  

I am still not 100% sure that the bootloader installed, so i'm going to try this all again...

Thanks!!

Ave

---

### Post by chriscando on 2006-04-30
Reguarding the Esc key.  This is what worked for me.  The problem I was having was after setting up the username and password the installer would hang, the only way I could get around it was to hit Esc key and install the grub bootloader first.  After that was installed it would prompt me to reboot without the cd. When it came back up it prompted me for the CD and I was then able to setup the user account and finish the installation with no more problems. Hopefully this can work for you, let us know how it goes.

chris

---

### Post by Avenue on 2006-04-30
Hello Everyone, 

I had to bump this post as I am still having problems with my installation.  Since last night I tried using another CD, but the same thing keeps happening.  I watched the install process this time and it looked like the bootloader was installed, then before I rebooted I hit the "ESC" key and went back and loaded the bootloader again to be sure.  I chose the "continue" option to reboot and....I get what looks like a DOS prompt again which displays the message "invalid diskette in the A:"...frustrating.  

I really think that everything is loaded correctly, I just can't seem to get to the bootloader from my hard drive.  Putting the CD back in does not fix it, as it only wants to take me back through the install again.  

**Does anyone have a work-around for this?????**

Once again, i'm only running one hard drive and i'm using one big partition.  I've also rearranged my BIOS several times to no avail.  

Thanks!!!!!!!!!!

Ave

---

### Post by chriscando on 2006-05-02
Did you install the grub loader to the MBR? This is what has always worked for me. Cause it sounds like your system is not finding anything to boot.

---

### Post by dion on 2006-05-02
I know this might sound like an absolutely stupid answer, I am also rather new at this.  Okay, I know that the installation media reads your CD rom drive as drive A in order to boot correctly.  However if your CD Rom is empty, the installation has completed sucessfully, and none of these other suggestions work, you may want to check that you do not have a disk in the stiffy drive if your PC has one.  DOS also refers to this drive as A.  Hope you find a solution.

---

### Post by Bartender on 2006-05-03
I'm assuming A: drive is the floppy.  What happens if you open up the PC and disconnect the floppy data cable?

---

