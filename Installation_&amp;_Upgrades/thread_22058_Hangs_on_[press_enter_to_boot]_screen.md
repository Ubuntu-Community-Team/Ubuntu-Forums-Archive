---
title: "Hangs on [press enter to boot] screen"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by Alex4R on 2005-03-25
I searched the forums, and couldn't find anything that would help me.

I have an install CD that was mailed to me, and I am about to attempt a dual boot with Windows XP Professional SP2. I resized my partition using Partition Magic, and left the free space unformatted. Now, I put in the Ubuntu install CD, and restart. It boots onto the screen that says "Press F1 for help or Enter to boot", but here it hangs up. It wont do anything when you press enter, or F1. At first I thought maybe it was just a bad CD, so I put in another one...same problem. So I downloaded it and burned the image to my own cd using Alcohol 120%...same problem.

I have installed Ubuntu on this box before, but it wasn't dual boot. Any help will be appreciated!

---

### Post by Alex4R on 2005-03-26
Okay, for some reason after I unplugged my network cable it magically worked  :?: So if anyone else has this problem, here is a possible solution.

Now, I have Ubuntu installed on a seperate partition than Windows, and I can boot Ubuntu just fine, but Windows will not. Using GRUB boot loader, this is what Windows' configuration is:

[php]
root (hdd0,0)
       file system type unknown, partition type 0x7
save default
make active
chainloader +1
 _
[/php]

It doesn't throw an error at me, just sits on that screen. Any ideas? Thanks!!  8)

---

