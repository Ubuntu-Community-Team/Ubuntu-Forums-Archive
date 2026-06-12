---
title: "XP not recognised by Ubuntu 11.10 Live CD (nor install)"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-11-19
I am starting with an XP laptop and aim to install Ubuntu 11.10 dual boot. However, the live CD 11.10 does not recognise the existing XP. 

In Ubuntu live session, XP and its files are not indicated, and when I proceed to the install process, the option is offered as 'This computer has no detected operating system, what would you like to do' (then, erase?, or something else?)

Maybe there is something about this XP installation which is odd (or something about ubuntu 11.10??)

I am using only XP and no other OS on the machine initially because previous installs of ubuntu 11.10 on this machine have led to problems with the grub menu (XP missing.....) as used from the ubuntu 11.10 in what was at that time a multiboot machine, this xp and also ubuntu 10.04.3 (and then also 11.10, when problems were seen). No grub menu or xp recognition problems were seen when using Ubuntu 10.04.3 on this machine. Only with Ubuntu 11.10

Lubuntu live CD 11.10 does the same thing, does not see the XP os.

Ubuntu 11.04 live CD works ok, the live session mounts XP with no apparent problem and the install process offers to install alongside 'XP' so it is evidently recognised.

Has anyone installed 11.10 on an XP machine and found that XP is recognised for them? 

I can find little about this apparent issue. I find it hard to believe that there are possibly so few XP-Ubuntu 11.10 situations or alternatively so few 11.10 installs on machines with XP existing that nobody has bumped into this. Or is something odd about my own machine or XP whatever?

tia

---

### Post by zvacet on 2011-11-19
During install when you choose **something else** do you see your Windows partition(s)?

---

### Post by candtalan on 2011-11-19
> **zvacet said:**
> During install when you choose **something else** do you see your Windows partition(s)?
yes (I believe) the ntfs partition is shown, it is certainly shown ok in gparted for example too,  however after an apparently normal install like that - advanced, manual, then the XP is not picked up in grub no matter what. I became aware of this whole thing when originally attempting to fit ubuntu 11.10 into an existing partition using  the 'something else' method, and it seemed that grub lost my XP (it is a test machine).
This was in another thread in fact
windows entry removed from grub after upgrade to 11.10
[http://ubuntuforums.org/showthread.php?t=1868036](http://ubuntuforums.org/showthread.php?t=1868036)

And I continued experimenting as you might see in that thread.
I eventually found a reduced situation in the same machine, same xp, using live CDs, which seemed to make sense. If XP was not recognised in the live session as an 'OS' then the same anomaly might be  implicit in the grub action.
tia

edit:
I am just also now installing a new XP into another machine as a single OS, then I will see how an ubuntu 11.10 live session  works - different xp installation (few, if any updates) and different machine.

edit2:
The new xp (non updated) installation is recognised by 11.10 live session in the second machine.Mmm need to sleep on this. 
Any ideas?

edit3: In the problem xp I notice a fleeting message before xp starts 'invalid boot.ini file' also I see that in the new install xp (where xp is recognised ok by ubuntu 11.10) there is no such message, also, checking out, it has a boot.ini file in place, whereas the problem xp I now see does not, it only has a boot.bak.
I copied this bak file to elsewhere, renamed, and pasted boot.ini file back into c:\ 
And yay! the xp is now recognised by live session ubuntu 11.10.
However the Ubuntu 11.10 installer does not offer here to install 'alongside' (resize implied) but it does know xp exists and offers only to 'overwrite xp' or 'something else'
So I conclude that for some reason, unknown, this xp lost its boot.ini and that ubuntu 11.10 live session was affected by its lack. I note that earlier versions of ubuntu do not seem to be affected.

I now aim to resize xp, create partitions, and use the something else option to install 11.10

edit 4: Gparted in 11.10 live session could not check the ntfs partition, indicating a number of errors, which it could not fix. I had been resizing a lot yesterday so perhaps some damage was done. I used XP and ran chkdsk and some errors were found and fixed. I ran or thought I ran, chkdsk more than once and the log showed at least some errors fixed in the final run, so maybe a multiple run is useful, not sure, windows novice here. Subsequently 11.10 live session not only indicated xp but now offered 'alongside'. And gparted  also indicates no ntfs errors.

edit 5:
The install alongside xp of 11.10 went normally :-) and xp does appear in the grub menu following install.  :-)

I note that when I first got these problems, I had used the 'something else' manual partition option and although I trust that the install option would not cause these problems, I have not yet proved that. I still do not know how the boot.ini file got lost.

---

