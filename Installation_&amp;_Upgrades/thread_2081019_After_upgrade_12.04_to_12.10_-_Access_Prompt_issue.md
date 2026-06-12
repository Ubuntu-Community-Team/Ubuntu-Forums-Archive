---
title: "After upgrade 12.04 to 12.10 - Access Prompt issue"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by RobHam06 on 2012-11-05
Help required to track down the cause of an issue after upgrading.


The upgrade from 64bit 12.04 to 12.10 seemed to complete with out any major problems.  But unfortunately when I now boot,  quite early on in the boot sequence an Access prompt will appear (it never use to appear before applying the upgrade).

The access prompt requests the password to my gmail account and there is a tick box to add the password to my keyring.  If I enter the password and click accept,  the machine will virtually freeze up and appears seriously ill,  I think because at this stage in the boot sequence my login keyrings are not unlocked and hence the password cannot be added to the keyring hence the freeze.
If I re-boot, I can just cancel this access prompt and immediately I do this the boot sequence progresses and I get the normal 'unlock login keyrings' prompt and the machine will work just fine.


I think that the underlying problem is a boot sequence issue,  where the 'unlock login keyrings' dialogue should happen first,  and then what ever program needs my email password would just go and get it from the keyring. Unfortunately after the upgrade and because my keyring is not unlocked,  it brings up this access prompt.  
I actually upgraded the machine over a week ago and have waited in the hope that the various bug fixes may fix this issue but to date I still the problem.


So Question.....
How can I track down what program is requesting this Access Prompt ??.  Is there a log file somewhere that I can open and explore ??

---

### Post by dino99 on 2012-11-05
as its gmail asking for password, then you might need to remove the mail service (evolution or thunderbird or the mail server you are using) from the starting list:

Applications ->  System Tools -> Preferences -> Startup Apps

---

### Post by RobHam06 on 2012-11-05
> **dino99 said:**
> as its gmail asking for password, then you might need to remove the mail service (evolution or thunderbird or the mail server you are using) from the starting list:

Applications ->  System Tools -> Preferences -> Startup Apps

I have just disabled all of the startup options, but I still have the problem.  Unfortunately none of the startup items have anything to do with email, mostly are some screenlets that I use.

But I do think this must be something to do with email.
My next plan is to look in /etc/init.d and perhaps try and disable some of these startup things.

---

### Post by RobHam06 on 2012-11-13
Just updating my own thread.

My password prompt problem has decided to fix it's self,  unsure by what mechanism - perhaps it was fixed by a package update.

---

