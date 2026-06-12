---
title: "Black screen with blinking cursor after installation"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by mfrp9 on 2015-08-12
It seems to be a somewhat common problem, but sadly, I don't believe the solutions have helped me. I have attempted to install Ubuntu 14.04.3 LTS via Live CD. While the installation claimed to be successful, after booting the computer, I am greeted with a black screen and a blinking underscore ( _ ). Ubuntu runs fine via the Live CD, but booting it from the hard drive I encounter the above problem.

I followed this guide: 
[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)
I believe my problem closely resembles the "black/purple screen after you boot ubuntu for the first time" I tried to follow but I could not access the grub menu, via Shift key or Esc key.
Has there been any well known fixes that came to light since that article was written? I noticed that it also may be due to the graphics card, as I am running a AMD Radeon video card.

---

### Post by Geoffrey_Arndt on 2015-08-12
The key is going to be accessing Grub so you can manually edit it and add the nomodeset parameter . . . the link you provided does have the right info, but not the top part.   Scroll down to the place where immediately after starting the PC, you press the right shift key to get the grub2 menu, and then press "e" to edit the Grub2 file.   After adding the nomodeset option, save and reboot  (be sure to add nomodeset to the right line - - see the example in your link).  That will get you a semi-ugly, sluggish  version of Ubuntu  - - but will allow you to navigate to Settings>Software Update>Additional Drivers tab.  From there you can install the proper drivers, reboot, and you'll have Ubuntu Unity in all it's glory (my favorite desktop).

The alternative or other solution is to install another flavor of Ubuntu that doesn't require 3d acceleration graphics.   Xubuntu would be a good choice, . . . another would be Ubuntu-Mate.   With either of these, you won't have to worry about or mess with alternate boot options like nomodeset.

A third option is LinuxMint Mate . . in my opinion, it's a bit more user friendly and polished than Ubuntu-Mate is at this point (and has other user helper apps that are unique to LinuxMint).

---

### Post by mfrp9 on 2015-08-18
Thank you for the advice... while I was not able to get to the Grub boot menu, I did continue looking for a solution...and found it in the Boot-Repair boot program...was able to repair it and ubunut boots fine now.

---

### Post by Bashing-om on 2015-08-19
mfrp9; Great !

You do good work .

> **mfrp9 said:**
> Thank you for the advice... while I was not able to get to the Grub boot menu, I did continue looking for a solution...and found it in the Boot-Repair boot program...was able to repair it and ubunut boots fine now.

Pleased you are up and running.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by nandagopal2 on 2016-01-30
I face the same problem. Could you please help me on how you solved it using the boot-repair boot program? 
My Ubuntu is installed on a external HDD. The installation went fine. On booting, only the black screen with the blinking cursor appears.Right shift key is not getting me into the Grub menu. My pc has an Nvidia card.

---

