---
title: "help with a 10.10 install over 9.04, what Mount Point?"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2011-01-29
I am trying to install 10.10 from a Live CD over my 9.04 (it would not do the upgrade automatically due to apparently lack of disk space.)

at the end of the my best guess at the process (alas, Linux is pretty much a plug and pray operation for me.), on rebooting, I get the message:

"the disk drive for / is not ready yet or not yet present"

I must have messed up at the Allocate Drive SPace / Edit Partition step.

I have three existing partitions:
7Gb for OS previously 9.04
35GB for data (which I clearly don't want to mess with)
a a bit for Swap.

So, I have clicked on the 7GB partition /dev/sda1 and have another window, Edit Partition, which is asking me:

New partition size (I would just leave it at 7007)

Use As (I presume I can leave it as EXT4?)

Format the Partition (NO unchecked?)

and 

Mount Point. ??

Now here is where I don't have a clue. The pull down options are:
/, /home, /boot, /tmp, /usr, /var, etc.

not knowing any better, my first time through I just picked "/"
and that is what got me to the message

"the disk drive for / is not ready yet or not yet present"

So what should I be specifying at this point?


Peter

---

### Post by Quackers on 2011-01-29
The mount point should be "/"
Use partitions as ext4 is fine
Format partition should be yes, really
redo swap, if necessary
That should be good.

---

### Post by pjstock on 2011-01-29
> **Quackers said:**
> The mount point should be "/"

thanks
But "/" was what I picked initially and what I thought caused the reboot error message.
could it be the failure to reformat the OS Partition?

---

### Post by Quackers on 2011-01-29
I honestly don't know, but if you are installing over the top of an existing file system, it is good practise to format.
This will also give the partition a new UUID, which may be beneficial during boot (and maybe not :-) )
Try it and see how it goes.

---

### Post by pjstock on 2011-01-29
ummm, we'll see what happens I guess.
though my last question (which I forgot to include in the original post) is this:
the final choice here is:

Boot Loader
Device for boot loader installation:

and the choices are:
/dev/sda ( which seems to be the entire HDD)
/dev/sda1 (which should be just the OS partition = 7GB)
/dev/sda6 (which is the data partition - which I don't really want to touch I don't think)

what is the Boot Loader?

---

### Post by kansasnoob on 2011-01-29
> **pjstock said:**
> ummm, we'll see what happens I guess.
though my last question (which I forgot to include in the original post) is this:
the final choice here is:

Boot Loader
Device for boot loader installation:

and the choices are:
/dev/sda ( which seems to be the entire HDD)
/dev/sda1 (which should be just the OS partition = 7GB)
/dev/sda6 (which is the data partition - which I don't really want to touch I don't think)

what is the Boot Loader?

Grub, leave it on the default: /dev/sda

Maybe some of the notes I made here will be helpful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Quackers on 2011-01-30
As you are replacing one file system with a new one it would make sense to format, so that nothing is left over (which shouldn't happen anyway, really). 
Regarding grub installing to sda, you are not actually designating the whole drive, as such. A part of grub will be installed to the mbr of the drive. The rest of grub will go in your root partition automatically. If you don't install grub to sda it won't boot, in your circumstances.

---

### Post by pjstock on 2011-01-30
alright, what the heck. here we go.

aiming at /dev/sda1 with "/" as the mount point and a reformat and /dev/sda as the Boot Loader location.

I'll report what happens!

---

### Post by dino99 on 2011-01-30
a standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by pjstock on 2011-01-30
> **pjstock said:**
> alright, what the heck. here we go.

aiming at /dev/sda1 with "/" as the mount point and a reformat and /dev/sda as the Boot Loader location.

I'll report what happens!

Bloody useless basically.
(though thanks anyway to those who took the time to talk me through this.)

But somebody has to call the Emperor on his new clothes.

It hangs at the "Choose your Keyboard Layout step" (offering such helpful combinations as "Canada" on the Left and "Cambodia" on the RH panel.
meanwhile, the install progress below chugs along "Copying Files" until it shows an optimistic sounding but ultimately unhelpful "Ready When You Are" message.

and then the whole thing hangs.

Brilliant.
once again Linux manages to make Windows look good (about 6 months ago I had an "upgrade" fail and wipe out my entire system).
no wonder Linux remains a marginal OS with a cult following.

alright, having written this rant in a fit of frustration I will wait 30 minutes and see if by some miracle this resolves itself.
Then Submit!

OK, searching "Ready when you are" and "Hangs" it appears that using a capital letter in the name or computer name causes a problem.
who knew?

however, now, on rerunning the install, I do not get prompted for Computer Name and user name etc.

it goes straight to the Preparing to Install and then Allocate Drive Space, at which point it starts copying files and then hangs.

How do I correct the naming problem that is causing the hang?

---

### Post by kansasnoob on 2011-01-30
Have you been able to run the Live CD successfully?

Did you check the CD for errors? To do so boot and as soon as the purple screen appears press any key. After that you'll need to select language and then just select "Check CD for errors". That will take a few minutes to complete.

If that passes select Try Ubuntu without changes and then post some basic info:

```
lspci | grep VGA
```

```
cat /proc/cpuinfo
```

```
free -m
```

```
sudo parted -l
```

---

### Post by kansasnoob on 2011-01-30
> **pjstock said:**
> OK, searching "Ready when you are" and "Hangs" it appears that using a capital letter in the name or computer name causes a problem.
who knew?

however, now, on rerunning the install, I do not get prompted for Computer Name and user name etc.

it goes straight to the Preparing to Install and then Allocate Drive Space, at which point it starts copying files and then hangs.

How do I correct the naming problem that is causing the hang?

You gave no indication of that earlier!

Look:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I discuss the problems with the new installer there ;)

---

### Post by kansasnoob on 2011-01-30
I did specifically say there that:

> NOTE: The user name must not include CAPS!

---

### Post by pjstock on 2011-01-30
for anyone else having this same problem (i.e. you aren't in the US) on re-re-running the install, I found that if I hurry at the Keyboard layout prompt and just quickly FORWARD on using the default "USA" prompt instead of picking Canada, then I manage to get to the naming page where maybe by using lower case this hang problem will resolve.

bizarre bug though.

---

### Post by kansasnoob on 2011-01-30
Bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555896](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555896)

And it should be fixed in Natty. I'll know when I iso-test in the next couple of days.

---

### Post by pjstock on 2011-01-30
alright, it finally seems to have installed.
what an ordeal though.

my data from before seems to still be there.
though all the applications I installed under 9.04 (Skype, Audacity, etc.) have been obliterated (might there be a warning about this?)

thank you anyway.

---

### Post by kansasnoob on 2011-01-30
I hope things work out for you. I happen to just love Ubuntu, but I've disagreed with many of their recent decisions. For instance the idea of "hiding" the boot options.

And the new live installer (ubiquity) is a total mess! If I didn't love Ubuntu I'd just jump ship ;)

---

### Post by pjstock on 2011-01-31
OK,  the day after my weekend 10.10 installation fiasco and I should report that the upside of all this is that under 10.10 (for some inexplicable reason) two applications that hadn't worked well previously (Skype and Audacity) now seem to work fine.

Audacity now shows the Input Selector that was missing under 9.04 (though the fix might be from a newer version of Audacity). That means I can now record streaming audio in Audacity, which for a radio person is pretty essential.

second, my mic (on this Dell Latitude X300) finally works, so Skype is useable. Is this a result of 10.10 having recognizing HW like my mic while 9.04 didn't? who knows.

Go figure. but these are good things.

---

### Post by Quackers on 2011-01-31
Aha! All in all a good result then :-)
10.10 may have different hardware support that wasn't present before - possibly.

---

