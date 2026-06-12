---
title: "Cant Install Linux on New PC keep getting this error message"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Azerial on 2007-08-30
kay Im wanting to Dual boot linux and XP Pro

I have XP pro no problem

Linux Ubuntu 6.06 however.... not so smooth.

I start it in, I click install Linux, and I get this message 

Uncompressing Linux... ok, booting the kernel.
[17179589.684000] .. MP-BIOS 8254 timer not connected* to IO-APIC
[17179589.684000] kernal panic - no syncing : IO-APIC + timer doesn't work!
Boot with apr**=debug and send a report then try booting with the 'nopic' option [17179589.684000]





*I think thats what it says my handwriteing is sloppy when I was scribbling that down and I could barely read it

**again sloppy handwriting made that hard to read



Soooo whats going on? how do I fix it?

---

### Post by Azerial on 2007-08-30
Also Its on a 320gb harddrive I set up 2 partitions one 100gb for XP and the rest would be for linux  IN my computer on Xp its not showing 2 HDs like it should with a partition

---

### Post by merlinus on 2007-08-30
You might try this:

At the opening menu, press F6 and add the following to the boot line --

noapic apic=off

Then press Enter.

-merlin

---

### Post by Azerial on 2007-08-30
> **merlinus said:**
> You might try this:

At the opening menu, press F6 and add the following to the boot line --

noapic apic=off

Then press Enter.

-merlin

Okay I tried that and I got to the first part of start up, and it just stopped, it showed the Ubuntu Logo and the loading bar, and the first two lines of text (cant remember what they say) showed up at the bottom, then NOTHING I waited for a few minutes, still nothing... Soo that didnt work.

---

### Post by Azerial on 2007-08-30
Hmm been a while and no replies.

right now on the advice of a friend im downloading the latest version of Ubuntu and Im gonna burn it to a DVD and try again.

But in the meantime I would like to know whats going on here with this problem.

---

### Post by Pumalite on 2007-08-30
Whatever you are trying to install doesn't like your hardware, so, post your specs.

---

### Post by Azerial on 2007-08-30
CPU - Athlon 64 X2 2.6ghz
HD - Seagate Barracuda, 320gb SATA
CD/DVD - Lite On CD/DVD Burner combo drive
Video - Geforce 7600GT 256mb

---

### Post by Pumalite on 2007-08-30
Strange. Try Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Mark box below 'Start Download'

---

### Post by linux noooob on 2007-08-30
Maybe you should try the 7.04 it works much better then 6.06 and has less errors. I know how you feel i hate the damn errors like that i had one almost lie that but when i reinstalled it was not there.

---

### Post by Azerial on 2007-08-31
> **linux noooob said:**
> Maybe you should try the 7.04 it works much better then 6.06 and has less errors. I know how you feel i hate the damn errors like that i had one almost lie that but when i reinstalled it was not there.

I did that.  AND I encountered this issue.

I Got 7.04 live cd and burned a Live DVD

It started up okay then It got to a screen where it displayed

[Bunch of random numbers] something I/O error, something

over and over until it filled up my screen then it went black and stayed black for like several minutes doing nothing and I restarted my computer

Guess that failed too

Im getting the alternate that isnt live and gonna try it next... god why is it so hard to install this operating system its starting to make me want to give up on having linux if I have to go though THIS much trouble just to make an effing dual boot with xp and linux

---

### Post by gtdaqua on 2007-08-31
Is this a Dell Vostro? There could be some sort of video problems. See the HOW TO on Dell Vostro in the installation section.

---

### Post by Azerial on 2007-08-31
> **gtdaqua said:**
> Is this a Dell Vostro? There could be some sort of video problems. See the HOW TO on Dell Vostro in the installation section.

No way, I don't buy pre-built systems.

This is a custom build I made 2 nights ago.

---

### Post by linux noooob on 2007-09-06
maybe it is a problem with the drivers since you made a custom computer maybe you have conflicting hardware or a driver that has not been properly installed on the BIOS.

---

