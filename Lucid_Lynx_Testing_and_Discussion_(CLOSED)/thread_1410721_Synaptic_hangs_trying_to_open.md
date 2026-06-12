---
title: "Synaptic hangs trying to open"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by robert shearer on 2010-02-19
When I try to open Synaptic it greys out, the progress bar bottom right gets about 3/4 across, at bottom left it says 'building dependency tree, cpu hits 100%, and then it hangs.
Have to kill it or it it continues at 100%cpu usage with no result.

Update manager works fine.
Apt-get etc from the command line works fine.
Ubuntu software centre works fine.

Starting synaptic in a terminal brings about the same behaviour and no text to help.
Eventually killing synaptic returns the unhelpful "terminated" message in the terminal and that is all.

Started today. Maybe some update caused this ? though as I can't open synaptic I can't view the 'history' to see what it may have been.:confused:

---

### Post by jppr on 2010-02-19
just uptadet system in synaptic without any problem. synaptic work fine and system works fine :popcorn:

---

### Post by robert shearer on 2010-02-19
> **jppr said:**
> just uptadet system in synaptic without any problem. synaptic work fine and system works fine :popcorn:

Well done.

---

### Post by cimh on 2010-02-23
I have the same problem as you. It started on sunday immediately after I did an upgrade of packages via synaptic. It seems to be a crash as its not possible to close synaptic down.

apt-get works fine

cimh
901 lucid alpha

---

### Post by philinux on 2010-02-23
> **robert shearer said:**
> When I try to open Synaptic it greys out, the progress bar bottom right gets about 3/4 across, at bottom left it says 'building dependency tree, cpu hits 100%, and then it hangs.
Have to kill it or it it continues at 100%cpu usage with no result.

Update manager works fine.
Apt-get etc from the command line works fine.
Ubuntu software centre works fine.

Starting synaptic in a terminal brings about the same behaviour and no text to help.
Eventually killing synaptic returns the unhelpful "terminated" message in the terminal and that is all.

Started today. Maybe some update caused this ? though as I can't open synaptic I can't view the 'history' to see what it may have been.:confused:

Have a look at the file /var/log/apt/term.log

It contains the apt terminal log. I don't think it logs updates via the terminal but it logs update manager and synaptic.

---

### Post by lonniehenry on 2010-02-23
I am getting this on my 32 bit machine (desktop pentium 4) but not getting it with my 64 bit laptop.  Other methods of upgrades work fine.  Have to force quit to stop it. Will check logs when I get to that machine.

---

### Post by robert shearer on 2010-02-23
Yes, you can kill synaptic from the terminal.
For interest I left it to run while I went out to feed the livestock.
20 minutes later it was just opening on my return.

Once opened it performed fine on searches.
If I selected a package it installed it but if i viewed the 'details' terminal the terminal would flash on and off as if the graphics were under extreme load. The rest of the desktop was fine.

However, once the installation had completed and the terminal closed and synaptic does that reload thing then it faltered again whilst 'building dependency tree'.

I have replaced my Lucid install and am discovering Antix.
Once the Lucid alpha3 arrives on the 26th I will reinstall and see if this synaptic loony-ness is gone.

---

### Post by lonniehenry on 2010-02-23
I did a "sudo dpkg --configure -a", followed by "sudo aptitude update" and then "sudo aptitude safe-upgrade".  After that the synaptic worked properly.  I don't know what exactly changed it to working.

---

### Post by robert shearer on 2010-02-24
> **lonniehenry said:**
> I did a "sudo dpkg --configure -a", followed by "sudo aptitude update" and then "sudo aptitude safe-upgrade".  After that the synaptic worked properly.  I don't know what exactly changed it to working.

Thanks for that !:)
 I am not bothered with what fixed it as long as it works.("I don't care where as long as I'm Mayor" (hint-ask a Kiwi)

Will try your fix if it appears in alpha3.

---

### Post by cimh on 2010-02-24
I fixed it in a similar but probably much less safe way.

in the terminal
sudo apt-get update
sudo apt-get upgrade

cimh

---

### Post by robert shearer on 2010-02-24
> **cimh said:**
> I fixed it in a similar but probably much less safe way.

in the terminal
sudo apt-get update
sudo apt-get upgrade

cimh

I had tried that for 4 days and no joy so I guess a fix came with a recent update.

Seems like it is no longer a problem so I am looking forward to a reinstall. :D

---

