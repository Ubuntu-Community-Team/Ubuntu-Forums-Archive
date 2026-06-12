---
title: "Can't access Rescue mode"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by Singee15 on 2006-06-23
I put the live cd in, i tell my bios to boot to it.

it loads up with the normal graphical menu. I press exit to get to the "boot: " prompt.

i type: "rescue" so the while line looks like this: "boot: rescue". I press enter and it says: "could not find the kernel image: rescue"

what in the world am i doing wrong? i need to repair grub but i can't even get back into linux now.

any ideas? thanks

---

### Post by FredB on 2006-06-23
This thread could help you : [http://ubuntuforums.org/showthread.php?t=2689]("http://ubuntuforums.org/showthread.php?t=2689")

---

### Post by Chribu on 2006-06-24
Yep, I have the same problem:

I put the live cd in, i tell my bios to boot to it.
it loads up with the normal graphical menu. I press exit to get to the "boot: " prompt.
i type: "rescue" so the while line looks like this: "boot: rescue". I press enter and it says: "could not find the kernel image: rescue"

So why doesn't rescue work as it's supposed to?
I was following the instructions here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Herman on 2006-06-24
If you have the 'Alternate Install CD' (as opposed to the 'Desktop live/install CD', there is an option called 'Rescue a Broken System' at the start screen and it works great for re-installing GRUB. Re-installing GRUB has never been so easy! Try the 'Alternate Install CD' if you have one or can beg/borrow one.
Regarsd, Herman :D

---

### Post by Singee15 on 2006-06-24
I did that, tried to install to the mbr and it failed with error status 20.

---

### Post by rcarring on 2006-06-24
The Live Cd doesn't have the rescue or recoverymode kernel included.

Use the alternate cd as Herman suggested.

---

### Post by Singee15 on 2006-06-24
I did that, tried to install to the mbr and it failed with error status 20.

---

### Post by Singee15 on 2006-06-24
I did, didn't work.

More deatils here
[http://www.ubuntuforums.org/showthread.php?p=1178642#post1178642](http://www.ubuntuforums.org/showthread.php?p=1178642#post1178642)

please Help!

---

### Post by Herman on 2006-06-25
Okay, try this method, [*click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub"), and scroll down to see where the illustrations begin. I have just finished testing this and it works for me.
I don't know why the previous method didn't work for you, it should also be okay to do it that way, but I haven't tried that method lately. Sorry it didn't work for you.
Good luck, Regrads, Herman

---

