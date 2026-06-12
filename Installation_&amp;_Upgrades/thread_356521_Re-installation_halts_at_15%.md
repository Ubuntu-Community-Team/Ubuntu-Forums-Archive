---
title: "Re-installation halts at 15%"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by H0SS on 2007-02-08
Okay, so I have 1 hard drive.  4 partitions as follows -

1st 30 gig ext3
2nd 2 gig Linux swap
3rd 100 gig Ntfs
4th 2 gig Ntfs - for page file

I originally had this installed once dual booting in everything, no probs.  I messed around with ubuntu pretty bad as it was my first time messing with it and decided to re-install.  I deleted the first two partitions and put the live cd in.  Everything went well.  I created the first two partions as I had them the last time, and at 15% installation it just hangs.  Now my Grub is messed up and I cant seem to get it to boot at all.  I think I messed the MBR up when I deleted the partitions the first time.  

If I can get a sucessful re-install wont it just re-install Grub into the  MBR?  Is there reason why it hangs at 15% during the installation?  Do I need to completely slick my hard drive?  Any help is greatly appreciated.

---

### Post by housam on 2007-02-08
Fix your MBR first using windows cd. then try to reinstall again.

---

### Post by H0SS on 2007-02-08
> **housam said:**
> Fix your MBR first using windows cd. then try to reinstall again.


Do you have a link with detailed infomation on how to do this?

---

### Post by go2dell on 2007-02-08
[LIST=1]
[*] Boot from the Windows (I'm assuming XP here) installation CD.
[*] Use the Recovery Console option, which is "R" I think.
[*] Fix the MBR like this:
```
FIXMBR [press Enter]
```
Confirm the fix with "Y" when it asks.
[*] Reboot and let us know how the install goes.
[/LIST]

---

### Post by H0SS on 2007-02-08
nm, I googled it and found the answer.  Though this will fix my MBR, will it allow me to re-install Ububtu without it hanging at 15%?

---

### Post by H0SS on 2007-02-08
> **go2dell said:**
> [LIST=1]
[*] Boot from the Windows (I'm assuming XP here) installation CD.
[*] Use the Recovery Console option, which is "R" I think.
[*] Fix the MBR like this:
```
FIXMBR [press Enter]
```
Confirm the fix with "Y" when it asks.
[*] Reboot and let us know how the install goes.
[/LIST]

Thank you for the instructions.

---

### Post by go2dell on 2007-02-08
> **H0SS said:**
> nm, I googled it and found the answer.  Though this will fix my MBR, will it allow me to re-install Ububtu without it hanging at 15%?

I'm not certain we really have enough information to give you a good answer there.  You could always try either manually partitioning before beginning the install or trying to install from one of the Alternate Install CDs.  YMMV.

EDIT:  I just remembered that Windows has a huge bug in it that may stop you in your tracks (surprise, surprise!).  If you set a password for the Administrator account (the one named "Administrator" that you normally only see if you're in Safe Mode) *and* if you've applied either or both Service Packs to the system, you cannot use the Recovery Console from the original installation CD.  If so, there are ways around it but it's annoying.

---

### Post by H0SS on 2007-02-08
Right on, I will try once I get home and than you again.

---

### Post by H0SS on 2007-02-08
> **go2dell said:**
> I'm not certain we really have enough information to give you a good answer there.  You could always try either manually partitioning before beginning the install or trying to install from one of the Alternate Install CDs.  YMMV.

EDIT:  I just remembered that Windows has a huge bug in it that may stop you in your tracks (surprise, surprise!).  If you set a password for the Administrator account (the one named "Administrator" that you normally only see if you're in Safe Mode) *and* if you've applied either or both Service Packs to the system, you cannot use the Recovery Console from the original installation CD.  If so, there are ways around it but it's annoying.

Bummer, I did not know that.  But then again, who doesnt at least have SP1 installed?  Wasnt that released like 2 years ago?

---

### Post by go2dell on 2007-02-08
Yes, it was released years ago, and yes the problem has been annoying since then.

Note that if your install CD is one with either Service Pack included, or if you have created a slipstreamed install CD with SP2 on it, then this issue won't affect you.  It's just something to keep in mind when you try to log in and can't... before you begin to beat your head against the desk.

---

### Post by H0SS on 2007-02-08
Looks like this might be promising.  

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by H0SS on 2007-02-08
> **go2dell said:**
> Yes, it was released years ago, and yes the problem has been annoying since then.

Note that if your install CD is one with either Service Pack included, or if you have created a slipstreamed install CD with SP2 on it, then this issue won't affect you.  It's just something to keep in mind when you try to log in and can't... before you begin to beat your head against the desk.


Yeah, I have a completely custom XP install cd that I made.  Slipstreamed SP2, with an answer file for all the install questions.  It also installs a crap ton of thrid party apps for me to include NAV, Zone Alarm, DVD ripping utils, Nero, Spyware utils, Registry Mechanic, DX9, Java...... The list goes on and on, with a ton of registry tweaks.  Took me about 2 weeks to write the (scripts) for it and about 30 cd's lol.  It is a nice disk, but I am getting tired of m$.  That is why I really want to get a grasp on Linux and run with it.

---

