---
title: "M2N-MX SE plus (motherboard) on Intrepid?"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by botulismo on 2008-10-20
Has anyone with the M2N-MX SE Plus motherboard tried to run Intrepid Ibex beta yet? I was wondering if it worked "out of the box." I had attempted to install Gutsy and Hardy both on my PC that has this motherboard and failed miserably.

There is a workaround available on the forums but it honestly never seemed to work for me. I have been using Ubuntu since Edgy and have always liked it, but ever since building this new computer a couple of months ago I've gone back to using Windows because Ubuntu has not seemed to be an option.

---

### Post by Toet on 2008-10-20
What kind of CPU are you using? I have almost the same board, a M2NPV-MX, and never had any problems.

---

### Post by botulismo on 2008-10-20
AMD X2 5000+ Black Edition CPU. Others have had the same problem. I tried the fixes in:

[http://ubuntuforums.org/showthread.php?t=809108&highlight=M2N-MX+SE](http://ubuntuforums.org/showthread.php?t=809108&highlight=M2N-MX+SE)

BUT despite this all I have managed to do is boot from the LiveCD. After installing, the system crashes on reboot for some reason :-/

---

### Post by Toet on 2008-10-20
Where does it crash, at GRUB or when booting? There could be some logs that point in the right direction.

---

### Post by botulismo on 2008-10-20
It crashes during boot. According to one forum I read Mandriva works flawlessly with this motherboard but Ubuntu (at least, Hardy and Gutsy) does not work well, if at all, without modifying BIOS.

I really was surprised that there was a problem with the motherboard's compatibility with Linux. I hadn't thought to look that information up prior to purchase.

I don't have access to the logs anymore because I formatted the drive after unsuccessfully trying Ubuntu for a couple days after putting this PC together. I didn't really think to save them because I assumed that there would be more progress in Linux/Ubuntu and that the problem would eventually be fixed. It very well may be fixed, but since nobody has stated they have tested it yet, I may have to play guinea pig once Intrepid is officially released.

I'm fine with that, but I really would rather not destroy my current working Windows installation in the process, thus leaving me with no computer. I have a USB SD Card drive... Would it be possible to install to it and give it a test run without modifying my system permanently so that I could try Intrepid? How big of an SD Card would I need, if so?

---

### Post by Toet on 2008-10-20
If the card drive is seen as a hard disk when installing it should be possible. But make sure you install grub at the boot record of the card drive, NOT in the mbr. This is an option somewhere during the install, which used to be hidden away under a options or advanced button. But I do not know that by heart.

If you have succeeded to install Ubuntu and grub to the card drive, you can choose at boot from the pc with F8 to boot from the USB disk.

Like this, you are not messing with your other hard drives. I think Ubuntu would need somewhere between 4 and 8 GB. I do not know how much exactly.

---

