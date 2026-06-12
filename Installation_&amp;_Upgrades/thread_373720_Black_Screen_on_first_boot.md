---
title: "Black Screen on first boot"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by Twopin on 2007-03-01
I have seen this post a few times but each one seems to have a diffent answer to the problem and I still cant seem to get it too work. I have fully installed Xubuntu and load threw the splash then it goes blank. I installed VIA the txt install. My system is a POS Pentium 133 with 98mgs of ram and an unknown video card.  I can boot into the Ctrl+Alt+F1 / F6 and can get into the Sudo Nano /boot/grub/menu.lst I read somewhere to edit 

## ## End Default Options ##

title         Ubuntu, kernel 2.6.15-26-386
root         (hd0,0)
Kernel     /vmlinuz-2.6.15-26-386 root=/devhda3 roquiet splash
initrd       /initrd.img-2.6.15-26-386
savedefault
boot

and changed it too: 

## ## End Default Options ##

title         Ubuntu, kernel 2.6.15-26-386
root         (hd0,0)
Kernel     /vmlinuz-2.6.15-26-386 root=/devhda3 roquiet splash Noapic nolapic
initrd       /initrd.img-2.6.15-26-386
savedefault
boot

with no luck then changed it too


## ## End Default Options ##

title         Ubuntu, kernel 2.6.15-26-386
root         (hd0,0)
Kernel     /vmlinuz-2.6.15-26-386 root=/devhda3 roquiet splash acpi=off noacpi
initrd       /initrd.img-2.6.15-26-386
savedefault
boot

and in changing it i somehow removed the Kernal line... now for the annoying part when i re-enter the kernal on hitting ESC durring boot i get an error saying it is an unrecoginzed kernal but every time i change it i get an unrecognized kernal error 27 i believe. but i put in exactly what the kernal says above.  /vmlinuz-2.6.15-26-386 root=/devhda3 roquiet splash

---

### Post by Twopin on 2007-03-01
well to deal with the issue of broken kernal i decided to re-install... since it'll be quicker then waiting for a response most likely. but i know i will still have to deal with the black screen after so It would be awsome if someone has a fix to this issue as I want to use this computer (using 6.06) as a team speak server ( not using server edition though as i want to see how the desktop linux works)

Thanks,
Scott

---

### Post by ImmortalGrey on 2007-03-02
> **Twopin said:**
> well to deal with the issue of broken kernal i decided to re-install... since it'll be quicker then waiting for a response most likely. but i know i will still have to deal with the black screen after so It would be awsome if someone has a fix to this issue as I want to use this computer (using 6.06) as a team speak server ( not using server edition though as i want to see how the desktop linux works)

Thanks,
Scott

I have the same exact problem that you do, and I have yet to find an answer.  My way around this right now, is to be there when your computer starts up, hit ESC to access the GRUB menu, on the first option, hit "e", go to the 2nd option (which I think is the kernal) hit "e" again, and throw in just "acpi=off", after that long line of text, hit enter, and then "b" to boot using those parameters...  It will boot into Ubunut properly.

But as far as editing the menu.lst file, I've tried so many combinations, and I'm either met with the same black screen, or I get the "unknown interrupt or fault at EIP" and it restarts.

I've started a thread asking on how to resolve it, and no responses, so I unfortunately have no other information for you apart from this temp solution.

If you do get a solution, if you could PM it to me, that'd be great. :)

---

