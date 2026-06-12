---
title: "CD-Rom Drive Auto Closes"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lonewolf72 on 2008-10-11
After upgrading to Ibex, the cd rom drive automatically closes.  So when I burn a cd in k3b, when it finishes the burn, it ejects the cd and then before I can remove the disc from the tray, the tray closes again.  If I put in an audio cd to rip, when it finishes ripping it ejects and then closes before I can remove the cd.  It does this with data discs, when I hit the eject button, the drive opens and closes right away.  This has only happened since upgrading to Ubuntu Ibex.  Am I the only one experiencing this or is this a known problem.  Didn't have any luck searching here or google for this issue.

Thanks,

Clay S.

---

### Post by Hairy_Palms on 2008-10-11
i just noticed it today, strange, i can confirm it, it doesnt do it every time though

---

### Post by shane19174 on 2008-10-13
This is a known bug. Here it is: [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931]("https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931")
As I posted there:

> A consequence of this bug is that it is impossible to copy a CD/DVD in Brasero. After copying the contents of a disc to a temporary location, Brasero aborts with the message that it cannot eject the medium. Manually ejecting and replacing the disk is ineffectual, as the operation cannot be resumed.

Does eject work correctly for others? Or is everyone affected? Does anyone know if progress is being made here?

Shane

---

### Post by mwcrowley on 2008-10-13
yeah, it happens to me too, you got to be quick.

---

### Post by harty83 on 2008-10-25
This is a royal pain in the butt.  Any ideas on a fix?

---

### Post by pulpo69 on 2008-10-25
i can confirm the cd-rom drive problem (i have a hp internal drive).

---

### Post by Polygon on 2008-10-26
there is a fix released upstream, be patient =)

---

### Post by kansasnoob on 2008-10-26
There is a work-around here (post #25 and #27):

[http://ubuntuforums.org/showthread.php?t=942553&page=3](http://ubuntuforums.org/showthread.php?t=942553&page=3)

---

### Post by ktp on 2008-10-26
I just noticed this the other day..did think much about it.

---

