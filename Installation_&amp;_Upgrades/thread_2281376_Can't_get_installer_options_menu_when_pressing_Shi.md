---
title: "Can't get installer options menu when pressing Shift key"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by randominion on 2015-06-06
Hi. I'm trying to follow the [instructions to do an OEM install of Ubuntu]("http://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") and I just want to check I'm doing the right thing. 

I have a computer with Windows XP on which I'm selling, so I want to install Ubuntu OEM, so that the next owner can set it up for themselves. 

I'm using the Ubuntu 14.04 live CD, and holding the Shift key as it boots - right from the bios, but I don't get the installer mode option menu - just the normal Try Ubuntu / Install Ubuntu menu.

Is there some tip or trick for getting the right menu?

---

### Post by Bashing-om on 2015-06-06
randominion; Hi !


Considering:
> 
Is there some tip or trick for getting the right menu?

And ->
> 
I have a computer with Windows XP on

Nope, you are doing the only trick there is to it.
We can 'assume' that the partitioning scheme on the hard drive(s) is the legacy MBR, and as such, holding a shift key as soon as the "purple" splash screen with the stick figure/keyboard at the bottom appears will result in the boot options screen.

Else; well, maybe a keyboard issue ? Maybe only  a remote maybe, we are dealing with the newer firmware interface UEFI  ?

These 2 other possibilities are all I can come up with . Try try again to display the boot options menu. There is but a small window of opportunity for grub to recognize a key has been depressed.

[INDENT][INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by randominion on 2015-06-06
Many thanks for your reply. I tried again and this time unpressed and pressed the Shift key when I saw the stick man, and this time the menu appeared straightaway!

---

### Post by Bashing-om on 2015-06-06
randominion; Good deal !

If that original query is answered :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we move on to
[INDENT][INDENT][INDENT]our next adventure
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

