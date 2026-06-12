---
title: "Extremely odd boot problems - 8.10 beta with encrypted root LVM"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by teddks on 2008-10-20
I upgraded to the Intrepid beta two days ago. Most things went fairly smoothly, but there was one very odd thing that happened to my boot process.

I have an encrypted LVM that houses my root and home filesystems. Every time I boot up I have to enter the password to this LVM. When booting into Intrepid, the loading bar in the splash was moving up to a point, when it stopped. I typed in my password, and noticed that typing a character caused the bar to move for a short time (while I was holding the character down) and then stop again. After hitting enter, the process stopped again. However, it would start again if I pressed any key. I completed the boot by holding down the left alt key, though control and probably all other keys would have worked.

This happens in every boot. However, if I boot without the splash screen, it only happens during the early booting process, and stops once the system starts running init scripts. If I'm using the splash screen, I can halt the boot at any time during the process by releasing a key -- even in the middle of a script run, such as in between dkms points.

Anyone have any feedback on this? Has it been reported, or should I file a bug (and against update-initramfs or usplash)? Is there anything else I should provide in the way of information?

I'm running kernel 2.6.27-7-generic x86_64, and cryptsetup 1.0.6. The module used to decrypt / is twofish_x86_64.

---

