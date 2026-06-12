---
title: "Wubi Install in Xp"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2011-01-25
I have a WUBI installation of UBUNTU 10.04 in Xp - I upgraded this to 10:10 now I cannot get into UBUNTU. Get an error message about Grub Loader - Any ideas PLEASE.

---

### Post by nuffink666 on 2011-01-25
Hi,

Posting the error message you received might be a good start to a resolution please :D

---

### Post by coffeecat on 2011-01-25
Have a look at the first post in the Wubi megathread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

See if you can identify which problem yours is from the description there. The fix is given for each problem.

---

### Post by Dyffo on 2011-01-25
> **nuffink666 said:**
> Hi,

Posting the error message you received might be a good start to a resolution please :D
  O.K. here goes:-

NTFS35
GNU GRUB Version 1.98+20100804-5UBUNTU3

Minimal BASH -lilo line editing is supported.For the first word,TAB lists possible command completions.Anywhere else TAB lists possible or file completions.

GRUB >

---

### Post by Dyffo on 2011-01-25
> **coffeecat said:**
> Have a look at the first post in the Wubi megathread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

See if you can identify which problem yours is from the description there. The fix is given for each problem.

O.K. my problem is here but could do with some help.
When I use Ubuntu Live cd , my cursor just freezes, so cannot get into terminal. That is why I used WUBI in the first place.If I use Solution 3 and try to boot into UBUNTU from the Grub prompt, I need to know:-

insmod ntfs
set root=(hdX,Y)  # Your Windows partition. Example: set root=(hd0,1)
loopback (loop0) /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
the partition details X,Y ???  Is the disk Sda 1 ?? - where can I get this info - bearing in mind I cannot in any way get into Ubuntu or its Terminal.

---

### Post by coffeecat on 2011-01-25
I think you may possibly be looking at the wrong fix, but I could be wrong. I've sent a pm to someone who can help you better than I, so hang in there. Help is on the way! :)

---

### Post by Dyffo on 2011-01-25
> **coffeecat said:**
> I think you may possibly be looking at the wrong fix, but I could be wrong. I've sent a pm to someone who can help you better than I, so hang in there. Help is on the way! :)

Thanks - I AM HANGING on - in eager anticipation. Really don't want another re-install

---

### Post by Rubi1200 on 2011-01-25
Hi Dyffo,
I am the help coffeecat called in.

First things first, can you boot Windows normally?

Next, if you are having problems booting the LiveCD we need to sort it out because the solutions require working from the LiveCD.

So, what graphics card do you have and are you able to change and try another keyboard/mouse if these are causing issues?

---

### Post by Dyffo on 2011-01-25
> **Rubi1200 said:**
> Hi Dyffo,
I am the help coffeecat called in.

First things first, can you boot Windows normally?

Next, if you are having problems booting the LiveCD we need to sort it out because the solutions require working from the LiveCD.

So, what graphics card do you have and are you able to change and try another keyboard/mouse if these are causing issues?

Yes can start Windows normally. I don't have a special Graphics card - just the graphics on the Motherboard. My Keyboard is Portuguese, with Wireless mouse. Could change these if necessary. I do not have a USB mouse.

---

### Post by Rubi1200 on 2011-01-25
Have you tried booting the LiveCD with the nomodeset option?

All we need to do is get to the live desktop and we can take it from there.

If the Ubuntu CD does not work, try another live distro like Knoppix or Slax.

---

### Post by Dyffo on 2011-01-25
> **Rubi1200 said:**
> Have you tried booting the LiveCD with the nomodeset option?

All we need to do is get to the live desktop and we can take it from there.

If the Ubuntu CD does not work, try another live distro like Knoppix or Slax.

Can you tell me what nomodeset is ?? have got a French version of KNOPPIX or Mint 8 which I could try - if these would be O.K.

---

### Post by Rubi1200 on 2011-01-25
When you put the LiveCD in (the Ubuntu one) when you see the first screen and it asks if you want to try Ubuntu then hit F6 and you will see a menu option on the lower right.

One option is nomodeset; choose it and then Enter.

You may not have the same issues with the other CDs so it might be worth trying them too.

---

### Post by Dyffo on 2011-01-25
> **Rubi1200 said:**
> When you put the LiveCD in (the Ubuntu one) when you see the first screen and it asks if you want to try Ubuntu then hit F6 and you will see a menu option on the lower right.

One option is nomodeset; choose it and then Enter.

You may not have the same issues with the other CDs so it might be worth trying them too.

O.K. I used the F6 route and hey presto we are in  -I can get into Terminal - what do I do next ?

---

### Post by Rubi1200 on 2011-01-25
Excellent, progress is always good!

It sounds as if you have problem #2, needs solutions #1 from the Wubi Megathread.

If it works, don't forget to apply the Permanent Fix back in Ubuntu.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you need more help, let me know.

Just make sure you mount the right partition. If you are unsure, post the output of ```
sudo fdisk -lu
```

---

### Post by Dyffo on 2011-01-25
> **Rubi1200 said:**
> Excellent, progress is always good!

It sounds as if you have problem #2, needs solutions #1 from the Wubi Megathread.

If it works, don't forget to apply the Permanent Fix back in Ubuntu.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you need more help, let me know.

Just make sure you mount the right partition. If you are unsure, post the output of ```
sudo fdisk -lu
```


O.k Very difficult to copy the results across - basics are:-

Disk/dev/sda 250.1Gb
Device Boot - /dev/sda1
Disk/dev/sdb 2004 Mb
Can I assume from this that I mount to /dev/sda1
If you require more detail - please say.
I also have more detail on Disk/dev/sdb1 - if this is relevant.

---

### Post by Rubi1200 on 2011-01-26
I also assume Windows with Wubi is sda1, so use that in the instructions I linked to previously.

If, for some reason, it is not the right partition you will know pretty quickly (it just won't work).

As I said before, use solution #1 for problem #2

Good luck!

---

### Post by Dyffo on 2011-01-26
> **Rubi1200 said:**
> I also assume Windows with Wubi is sda1, so use that in the instructions I linked to previously.

If, for some reason, it is not the right partition you will know pretty quickly (it just won't work).

As I said before, use solution #1 for problem #2

Good luck!

ALL DONE and WORKING thank you so much for your help

---

### Post by Rubi1200 on 2011-01-26
No problem, you are more than welcome :-)

Don't forget to apply the Permanent Fix as well as locking the grub-pc and grub-common packages.

Enjoy!

---

