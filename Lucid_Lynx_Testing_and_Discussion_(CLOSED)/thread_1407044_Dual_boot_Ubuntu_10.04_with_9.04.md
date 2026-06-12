---
title: "Dual boot Ubuntu 10.04 with 9.04"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Steel-Bunz on 2010-02-14
An year back I wiped out Vista from a HP laptop and installed Intrepid. System was rock solid. Then I upgraded to Jaunty without reading the known bugs list and Intel graphics issues taught me a good lession. I then went through many fixes and got it reasonably working. For the past 2 months, even those graphics issues are gone and the only issue I now have is the rare sound skipping (while playing videos). System is rock solid again and I am afraid to upgrade to Karmic as I use my laptop for my work and it is heavily customized.

Now, I want to dual boot 10.04 alpha with 9.04 so that I could do some testing (mainly graphics and sound) and report bugs. My conern is Grub2. Jaunty has legacy grub and should I expect any issues while installing 10.04 alpha in dual boot? I have installed Ubuntu as dual boot on Windows computers, but, this is something new for me.  I would appreciate you help. Thanks much for reading...

---

### Post by Mencarta on 2010-02-14
I would back up Ubuntu 9.04 and then try it. If not restore Ubuntu 9.04 and file a bug report. It would help the Ubuntu Development Team.

---

### Post by Steel-Bunz on 2010-02-14
Thank you Mencarta...

Do you mean data back up? Yes, I am doing it already. However, my 9.04 is heavily customized and I have installed quite some work related packages.

Is there a way to back up the current image of the system and restore it? I am not sure how to do that. If yes, that would be great. I can even do dist-upgrade safely after backing up the current image.

---

### Post by Steel-Bunz on 2010-02-14
Well... I found some options for System restore... Partimage and "tar"  being two of them.. It would really be great if the default Ubuntu can  provide a solution via System -> Adminstration.. Will really be easy  for the newbies like me.... And we won't have many threads asking how to  downgrade to a older version.. :)

Any comments on Grub2? Thanks again.

---

### Post by Mencarta on 2010-02-14
If you have a second hard drive or extremely big usb you could just replace the main one with that and try it on that. If it doesn't work just swap them back, clear the other one, and file a bug report.

---

### Post by crazyavery4444 on 2010-02-14
Does anybody know if 9.10 has grub 2? Im pretty sure but Im to lazy to go downstairs to check

---

### Post by Mencarta on 2010-02-14
Yep, it has an option to download grub 2 instead of grub legacy.

---

### Post by Steel-Bunz on 2010-02-14
Thank you Mencarta... External Drive install is definitely an option...

_[crazyavery4444]("http://ubuntuforums.org/member.php?u=1000303")._.. I am pretty sure that grub2 is the default in Karmic..

---

### Post by Mencarta on 2010-02-14
It gives you the option.

---

