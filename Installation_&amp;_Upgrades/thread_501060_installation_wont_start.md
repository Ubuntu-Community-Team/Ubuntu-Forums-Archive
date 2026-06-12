---
title: "installation wont start"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by drewsmug on 2007-07-14
i installed unbuntu [fiesty] on one computer of mine and everything went smooth.  i liked it and wanted to install it on another one of my computers.

it is a compaq presario.  intel celeron D processor.

i restart the computer and get the start menu selection screen thing.  i select install and then right there i get a black screen with some text at the bottom. this is what it says

int 14: cr2 cf800000 err 00000000 eip c020c384 cs0000060 flags 0010007
stack: c00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 00000000

and then it stops and doesnt continue.

i read some other peoples post and think maybe it needs a bios undate or something.  but i really have no clue.  these error messages arent helping me at all.  any help is very much needed.

thanks in advance

---

### Post by merlinus on 2007-07-14
Try the text-based Alternate Desktop install cd.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

If you have less than 256MB RAM, then install xubuntu.

-merlin

---

### Post by drewsmug on 2007-07-15
i tried the text installation.
i get the same error messages.
is there anything else i can try.
im thinking the computer just sucks.

---

### Post by kmclar on 2007-07-15
You might try using "acpi=off maxcpus=0".
I got that from some thread in an openSuse forum a year ago when they made the smp kernel their default kernel.  I don't know if Ubuntu did the same thing, but using the combination above on the boot line worked for me, and I have the Compaq Presario with the Celeron.

---

### Post by drewsmug on 2007-07-16
i dont fully understand the "acpi=off maxcpus=0"

i dont know where i can be changing things before the actuall installation.
unless it has to do with the bios but them im just confused by what these parameters are

can anyone just point me in the right direction here please.
how do i change these things?

---

### Post by merlinus on 2007-07-16
Press F6 at the opening menu and add those parameters to the boot line.

-merlin

---

### Post by drewsmug on 2007-07-16
i used "acpi=off maxcpus=0" and got really excited because something started to happen.
and it doesnt really go through the normal process.
it doesnt ask any questions or format or partition or nothing really.
and then im at a desktop looking environment.
the thing is i cant actually do anythihng and if i pull the cd and reboot it boots to windows
i dont know what those parameters do but it didnt actually start installing anything

---

### Post by merlinus on 2007-07-16
There should be an Install icon at the top left of the live cd desktop, once it loads.

-merlin

---

### Post by theongreyjoy256 on 2007-07-24
Thank You for your help. I was looking on the forums and this solved my problem. My question is what exactly is the acpi=o maxcpus=0 command doing? Is it limiting the system at all? or just telling it what to expect?

---

