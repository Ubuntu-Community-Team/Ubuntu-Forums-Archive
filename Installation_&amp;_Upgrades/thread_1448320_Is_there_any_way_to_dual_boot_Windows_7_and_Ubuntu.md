---
title: "Is there any way to dual boot Windows 7 and Ubuntu 10.04?"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by MasterMac on 2010-04-06
Question in title. I just wanted to know if anyone has tried it and if they were successful. And, if successful, any tips to make it easier.:p

---

### Post by recluce on 2010-04-07
> **MasterMac said:**
> Question in title. I just wanted to know if anyone has tried it and if they were successful. And, if successful, any tips to make it easier.:p

When you install Ubuntu, GRUB2 gets written to the MBR, Ubuntu detects you Windows 7 installation and you can just choose between the two from the GRUB boot screen. Nothing to it - and I cannot see "easier" than "automatic".

I quadruple boot Win XP, Win 7, Ubuntu 9.04 and 10.04 - so I can confirm it works...

---

### Post by gfinlay on 2010-04-07
> **MasterMac said:**
> Question in title. I just wanted to know if anyone has tried it and if they were successful. And, if successful, any tips to make it easier.:p

Just a note of caution.  Whilst it can be straightforward, it can also go wrong and you can end up with a non-booting pc.  Make sure you understand MBR recovery before you commit any important pc to it.  

I would also respectfully suggest waiting until 10.04 is on general release and has had some settling in time.

---

### Post by Herman on 2010-04-07
The main thin with Windows 7 or Vista is to avoid moving the boot sector because Windows doesn't have a very sophisticated boot loader and if you move it, it isn't able to find parts of itself without the repair CD.

Either the 'Disk Manager' in Vista or Windows 7 can be used to shrink Vista or the inbuilt partitioner in the Ubuntu installer. 
A lot of people like to use GParted in the Live CD so they can see what they're doing better, but some people are not aware they should remove the check mark from the 'align to cylinders' checkbox when they use GParted on Vista or 7. Failure to remove the tick mark causes GParted to move the entire partition slightly. That not only takes a long time, it also usually means Vista or 7 needs the repair CD. 

[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

So, if you decide to use GParted, ** don't forget to remove the check mark.**

That's probably the main source of complaints from Windows users at the moment, I am guessing, failure to remove the checkmark in GParted.

Only move the right-hand end of Vista, never the start point of the partition on the left, where the boot sector is. If you do it's easy to fix, but inconvenient.

The other thing is, I think it's a good idea to run a file system check first in Windows before resizing it. If you're planning on resizing with Windows Disk Management, you should defrag first as well. 

You should always make a backup of your files and know how to re-install your old operating system and software before using any partition editor.

I have never had anything go wrong resizing Windows Vista or 7  except when I was deliberately trying to bork Windows just to learn what goes wrong and  how to fix it again. :)

---

### Post by seenthelite on 2010-04-07
> **MasterMac said:**
> Question in title. I just wanted to know if anyone has tried it and if they were successful. And, if successful, any tips to make it easier.:p

I have tried it and I was successful, Tip, just the same as any other version of Ubuntu.

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

