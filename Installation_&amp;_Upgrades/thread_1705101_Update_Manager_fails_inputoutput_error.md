---
title: "Update Manager fails: input/output error"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by BKossmann on 2011-03-11
Greetings, Linux gurus:

I am running 10.04 Lucid and have had no problems with executing Update Manager until just a few days ago.  Now, when I run UM it returns the error dialog that I have attached to this message.  (Yes, I have run 'sudo apt-get clean all'.)

I have listed the contents of sources.list in the attached text file, as requested in a similar thread.

Any suggestions are welcome; in spite of having used Linux for a number of years I have yet to progress much beyond the 'newbie' stage.

Thank you!

Bill

---

### Post by matt_symes on 2011-03-11
Hi

I just had a look through your sources.list file and i could find noting wrong with it so i think the problem might be with  the dpkg status file and we can test that.

Make sure Synaptic, Update manager and software center is closed. Open a terminal and type

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bak
```

Enter your password. It will not be echoed to the screen.

```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

See how that goes.

Kind regards

---

### Post by BKossmann on 2011-03-11
Hi Matt,

Thanks but that didn't solve the problem (see attached screen shot of the terminal).

Bill

---

### Post by matt_symes on 2011-03-11
Hi

Quick test. Open a terminal and type

```
dpkg -l
```

That's a small L above. Post back the results if failure. Respond if good.

Kind regards

---

### Post by matt_symes on 2011-03-11
Hi

It's getting a bit late here so i will go with my hunch.

Open a termminal and type

```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.bak
sudo mv /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo apt-get update
```

Any luck ?

Kind regards

---

### Post by BKossmann on 2011-03-12
Hi again,

Sorry for the tardy response, I thought it appropriate to take my long-suffering wife to dinner last night.

At any rate, I've run the commands as you suggested: first I ran dpkg -l and redirected the output to text (output too large to attach here).  I tried apt-get update and as before, it got to the part where it said, "Reading package lists... 1%" and then it seems to hang up, and after a while it returns the error message you see in the file.

I then moved the "available" files as you suggested and retried without success (results attached).

Is there a way to rebuild the package list?  Do I need to reinstall the Update Manager?  

Regards,

Bill

---

### Post by codejammer on 2011-03-12
Did you manage to fix your problem?  I have exactly the same issue.  Running apt-get update thrashes the disk for a while and then throws a "Bus Error".  I have tried all of the suggestions above with no success.

---

### Post by BKossmann on 2011-03-12
No, unfortunately I'm still unable to use Update Manager, either from the command line or via the desktop menu.  I don't get the bus error you mention, though I have noticed that once in a while my system slows right down, as if there were a process that's hogging all the resources - unfortunately it's a Catch-22 because I can't even start System Monitor to see what's going on.  

Maybe I'll try Computer Janitor out of desperation.

---

### Post by BKossmann on 2011-03-12
Well, this is interesting: I started the Disk Utility and it tells me that there are two bad sectors (see attached screen shot).  Coincidence?  Maybe, but I don't like coincidences.  

I'm beginning to wonder if I shouldn't reformat my hard drive and reinstall Lucid from scratch.

Also, when I did backups today I noticed the following message:

[INDENT]tar /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_lists_lucid_main_binary-i386_Packages: File shrank by 610910 bytes; padding with zeros[/INDENT]

Not sure if that means anything or not.

---

### Post by codejammer on 2011-03-13
I thought that it might be a disk problem so I tried running fsck on the boot drive (When booted using a live CD) but it didn't show any problems.  I'll try the disk utility and see if I get a simillar result.

I also tried backing up the Dpkg directory but it failed as well.  I have one file that I can't even open with vi.  I moved it out of the dpkg directory but it made no difference.

My system is almost completely unusable so I'm going to rebuild it today...

---

### Post by codejammer on 2011-03-13
Finally got the Disk Utility to run.  I've got simillar results except I have 766 pending and 256 reallocated sectors, this is probably why mine is much worse than yours.  Definately going for a rebuild.

---

### Post by BKossmann on 2011-03-13
Unless Matt pulls a rabbit out of a hat I'm leaning towards a total reinstall as well.

Bill

---

### Post by codejammer on 2011-03-14
Tried the rebuild but things got worse.  I think that I have a failing disk.  It's limping along but had to add a ROOTDELAY=120 to get it to boot and when I'm logged in the system periodically goes slow.  When I checked the Disk Utility again I now have over 1000 bad sectors :(  I think I need a new disk!

---

### Post by matt_symes on 2011-03-16
Hi

Sounds like it might be a hardware issue. As much as i hate to say it i would reinstall and see if the problem persists.

You could try to run fsck from the live CD as a last resort.

Kind regards

---

