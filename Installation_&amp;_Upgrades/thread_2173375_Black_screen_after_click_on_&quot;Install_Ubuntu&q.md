---
title: "Black screen after click on &quot;Install Ubuntu&quot;"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by TWEESTY on 2013-09-09
Hello all!

I have a black screen after a click on "Install Ubuntu"... I have already tried all experimets found here : [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

I am desperate... I have a MSI GE60-OND with Windows 8. I disabled SecureBoot,FastBoot...

Thank you in advance ;)

---

### Post by TWEESTY on 2013-09-11
[COLOR=#333333][FONT=UbuntuRegular]I have a GTX 660 with Optimus.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I already tried these changes in my grub : - change "quiet splash" by nomodeset - change "quiet splash" by i915.modeset=1 - change "quiet splash" by nvdia.modeset=1 - change "quiet splash" by nvdia.modeset=0 - change "quiet splash" by nomodeset
- change "quiet splash" by xforcevesa
- change "quiet splash" by i915.modeset=0 xforcevesa
- change "quiet splash" by vga=771[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Nothing works, thanks for your help !
[/FONT][/COLOR]
:) Thanks

---

### Post by su:bhatta on 2013-09-11
hi, 

did you try with keeping both 'quiet splash' and 'nomodeset' ?

or using 'no splash' & 'nomodeset'

---

### Post by TWEESTY on 2013-09-11
Hi bhattabhishek,

Yep, I just tried and it doesn't work :(

---

### Post by su:bhatta on 2013-09-11
how about choosing from F6 acpi= off & nolapic 
also give more specs of your system, did you check for EFI? 

Just see if that helps you....

am pretty lost after that, suggest you give the GPU details in the Thread name so that if somebody is using the same GPU comes along to help.

---

### Post by TWEESTY on 2013-09-11
[SIZE=2][FONT=arial]I am on EFI boot mode ;) 

I tried "acpi=off nolapic" and even "acpi=off nolapic noapic", both don't work ;'(

My specifications :

- GPU : nVIDIA Geforce GTX660M and Intel HD 4000
- Processor : Intel Core i7-3630QM @2.40GHz 2.40GHz
- Windows 8 64 bits (fresh install)

Thanks[/FONT][/SIZE]

---

### Post by ubfan1 on 2013-09-11
Check out the suggestions in [http://ubuntuforums.org/showthread.php?t=2119580&highlight=noacpi+i915+linux](http://ubuntuforums.org/showthread.php?t=2119580&highlight=noacpi+i915+linux)
Other distributions have similar problems/solutions: [http://forums.fedoraforum.org/showthread.php?t=289685](http://forums.fedoraforum.org/showthread.php?t=289685)

---

