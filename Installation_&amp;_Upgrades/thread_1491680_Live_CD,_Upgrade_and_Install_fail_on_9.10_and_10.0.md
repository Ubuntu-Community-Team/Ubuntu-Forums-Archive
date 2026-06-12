---
title: "Live CD, Upgrade and Install fail on 9.10 and 10.04  - 9.04 works great"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by juanoki on 2010-05-23
My first upgrade attempt to 9.10 ruined my install - there was no return and as 9.10 would not install either, I reinstalled 9.04 and everything was as expected.
I decided to wait for 10.04 hoping the issue had been solved - unluckily it has NOT.
Neither Live CD 9.10 nor 10.04 work.  New Mint does not work either - to closely related to Ubuntu, but Suse live CD does.
Played around with findings from different threads - like taking out "quiet splash --" and adding modprob parameter to no avail.
Prime suspect is HD and HD controller (ATA/PATA) - but I could not nail it.
I'm attaching the Submission XML run on 9.04 - which works flawless.
Appreciate any help
Thank you
Hans

---

### Post by juanoki on 2010-05-26
Any hint?

---

### Post by JedMeister on 2010-06-04
I won't for a second pretend that I can help you but to give any sort of guidance a little more info is probably needed:
> My first upgrade attempt to 9.10 ruined my installIn what way? At what point did it fail? Was there a specific error or did it just freeze (or do something else such as get stuck in a reboot loop etc)?

Also have you tried installing from an 'alternative' CD? I didn't have any issues with 9.10 but I've had a number of older PCs freeze when trying to load or install from the liveCD for 10.04. Installing using the 'alternative' iso has worked flawlessly on all those machines. You don't get the option to run live, or the pretty install screens ('alternative' runs a text mode installer only) but I think the trade-off is acceptable.

It may be worth a try although if you initially tried an in-place upgrade (rather than a clean install) then perhaps it won't work. Only one way to find out!!

---

### Post by juanoki on 2010-06-04
Thank you for your response JedMeister
When I attempted the 9.04 to 9.10 upgrade all processes run, but tons of errors appeared - don´t remember the detail, but it was about being able to read / write to the HD.
As I could not suspend the upgrade, when it finished I could not boot.  HD remained readable from a 9.04 Live CD and that way I was able to save my home.  Prior to any new attempt I gparted the disk and moved home to the new partition.
9.10 Live CD would not recognize my HD - but 9.04 did, so I re-installed that.
Now wi- upgrade was not an option as I'm on 9.04.
After a few failed Live CD attempts I was able to see some improvements  using acpi=off and noapic - my VIA PCI disk controller seems to be  problematic - and now I´m getting a new error, so need to continue with  some research.
Your suggestion of using the alternate CD is well worth a try - thanks for the suggestion - I will give it shot and will let you know the results

Cheers from Argentina

---

