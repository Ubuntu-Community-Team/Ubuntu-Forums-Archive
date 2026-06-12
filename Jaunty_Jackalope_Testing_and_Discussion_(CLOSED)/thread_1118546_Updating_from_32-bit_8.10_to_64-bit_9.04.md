---
title: "Updating from 32-bit 8.10 to 64-bit 9.04"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Scubdup on 2009-04-07
I want to try out 64-bit ubuntu and was advised that the release of Jaunty would be a good juncture at which to do it.

I also want to try out the Ext4 filesystem if I can (am I right in thinking pretty much any computer can use ext4? I already know my machine can handle a 64-bit OS)

Can anyone offer some advice on:-

[B][LIST]
[*]Will my current (presumably ext3) files be fine to run on the new ext4 system? I intend to back them up on an external hard drive prior to the installation.

[*]Is there an easy way to catalogue all the applications, Compiz settings etc that I have installed prior to the reinstall so that it’s relatively easy to re-implement them after?

[*]Is there anything else I should be worried about?
[/LIST][/B]

Thanks for any help.

---

### Post by frodon on 2009-04-07
Since just few CPU are real 64bits i am one of those not convinced by the interest of having 64bit OS except for those having more than 3Go of RAM.

There should be tools to convert ext3 to ext4 without data loss but as always backing up things is the way to go.

---

### Post by Scubdup on 2009-04-07
Thanks Frodon,

I haven't heard any views about "CPUs that aren't real 64bits" before.

Mine is a P4 which I have found will run 64-bit ubuntu (loaded 64-bit Ubuntu 8.10 off a live CD). I have 5gb of RAM.

Also - re ext3/ext4 I'm hoping I can drag'n'drop the files from the HDD to an external HDD, reinstall using 64bit 9.04 and ext4and then drag'n'drop all the files back. Is this realistic?

---

### Post by frodon on 2009-04-07
If you are interested you can find many useful info about x86-64 architecture (the most widely use for so called 64bits CPUs) there :
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by 3Miro on 2009-04-07
If you currently have 32-bit Linux, then there is no way to "upgrade". To move to 64-bit you will have to make a clean install.

1. Backup all data
2. Install the new 64-bit system
3. Restore data

For savinf the list of installed apps, you can save the list of installed packages (dpkg -something, not sure what).

I am not sure about the "full" 64 bit vs "half" 64 bit, but there are some advantages and unless you have a driver issue and/or don't want to mess with the already installed version that you have, you should  install 64-bit.

---

### Post by frodon on 2009-04-07
> **3Miro said:**
> I am not sure about the "full" 64 bit vs "half" 64 bit, but there are some advantages and unless you have a driver issue and/or don't want to mess with the already installed version that you have, you should  install 64-bit.Yep there're some disadvantages too, 64bit OS use more RAM than 32 bit one.
The feedback i got from core 2 duo 64bit users who made a performance comparison between 32 and 64 bit ubuntu is in general no performance improvement and larger amount of RAM used.

Could be useful to compare with other processor too. I beleive i saw more info about this in some thread in the forum.

---

### Post by 3Miro on 2009-04-07
The increase in the RAM usage is very small. Ubuntu in general takes so little RAM that it makes no real difference.

There was a difference on my AMD CPU between 32 and 64-bit. It wasn't really faster, but is was "smoother", switcing between tasks and such was definitely easier.

---

