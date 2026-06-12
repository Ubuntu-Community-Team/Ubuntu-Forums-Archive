---
title: "I think I broke my Ubuntu"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by greblando3 on 2015-04-27
I am going to preface this with the fact that I am extremely new to Ubuntu, so I don't know much. Anyway, when I start up my computer it takes me to "GNU GRUB version 2.02~beta2-9ubuntu1" not knowing what I should do I press "*Ubuntu" It gives me a bunch of lines that say "[FAILED]" "[ OK ]" or "[DEPEND]" then it just stops and says"Ubuntu 14.04.2 LTS Elitebook tty1

Elitebook login: [   49.438486] systemd-readahead[206]: Failed to open pack file: Read-only file system"

What do I do?

---

### Post by Bashing-om on 2015-04-27
greblando3; Hi ! Welcome o the forum.


.Might be a number of different issues . I do suggest as  1st approximation to run a file system check/repair .

Do you have the liveDVD(USB) on hand that you used to install ubuntu ? 
We need that medium to run the test as it must be run on the file system while the file system in not in-use .

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-04-28
What are the specs for your machine that you're trying to install Ubuntu on? it helps knowing what were working with. How did you create your media disk also.

---

### Post by greblando3 on 2015-04-28
I have an Elitebook 2540p and I used UNetbootin on my Mac to create a bootable USB of Ubuntu 14.04.2 desktop

---

### Post by greblando3 on 2015-04-28
Thanks so much for your help! But would you mind explaining how this is done Bashing-om?

---

### Post by greblando3 on 2015-04-28
If I need to completely wipe my hard drive I can.

---

### Post by Bashing-om on 2015-04-28
greblando3; Hey ...

Small steps, all my little mind can cope with .

1st is to know what the partitions are on the hard drive(s), so we can point the file system checker to these partitions.
So, fire up the liveDVD to "try ubuntu" mode and to terminal:
post back the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

``` and I will provide the explict commands to check/repair the ubuntu file system.

[INDENT][INDENT]longest journey begins
[INDENT][INDENT][INDENT]with this 1st step
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by greblando3 on 2015-04-28
Um. I don't know if this turned into a bigger problem but when I turned my laptop on again it said "The HP BIOS application selected is corrupt or missing. Please install the application and try again. 

BIOS Application Error (501)

ENTER-continue

For more information, please visit: www.hp.com/go/techcenter/startup"

I press enter, then press f9 to go to boot options. I then select my flash drive with the Ubuntu installed, but it just takes me back to the same "GNU GRUB version 2.02~beta2-9ubuntu1"

---

### Post by Bashing-om on 2015-05-01
greblando3; Hey !

How is it going now ? Still with hardware problems ?

You are not forgotten or ignored just that ->
I regret I can not advise in this situation of reverting your laptop back to bios defaults.
It is bad form to respond with a "I do not know" but perhaps giving a hint will suffice ?

[INDENT][INDENT]bios unhappy
[INDENT][INDENT][INDENT]nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by alpage2 on 2015-05-01
> **greblando3 said:**
> I press enter, then press f9 to go to boot options. I then select my flash drive with the Ubuntu installed...

Are you saying that you have installed ubuntu on a USB stick?

Or on the hard drive? - and if on the hard drive, is it the sole occupant of the hard drive, or did you try to keep windows in a dual boot arrangement?

Are you still getting the exact same BIOS message? And is this machine still in its warranty period?

Regards
Alan

---

