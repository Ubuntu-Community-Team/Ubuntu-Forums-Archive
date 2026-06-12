---
title: "Monitor shuts off when I boot from Live CD"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by zeldagamer96 on 2011-02-11
Why and how do I fix it?
I have a NVIDIA Geforce 6150 LE video card and it is on the motherboard.
I vaguely remember something on some site about nvidia cards, but can't remember what.
It gets to the part where it says something like 
"Boot Ubuntu from the CD." blah blah blah
I hit enter and it shuts my moniter off.
:confused::confused::confused::confused::confused::confused:

---

### Post by uRock on 2011-02-11
Hello and welcome to the forums.

When the disk first starts and you get the first purple screen, hit any key, select your language, then when the next menu comes up select the option to test the disk.

Regards,
uRock

---

### Post by zeldagamer96 on 2011-02-11
I did this and it still shut the monitor off like it went to sleep and it wont come back on...
it did it instantly and did not test the disk.

---

### Post by uRock on 2011-02-11
Is there a chance that you are trying the 64bit Ubuntu on a 32bit system?

I have the exact same on board graphics, so nVidia isn't be the problem.

---

### Post by zeldagamer96 on 2011-02-11
No. I think it is a 32-bit.

But just to be for sure, how can I tell

---

### Post by uRock on 2011-02-11
The only thing I can think of is reburning the image at 4x. You can also try putting the image on a thumb drive by following the instructions here, [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) Go to step two, select USB and OS in use, then click the Show me how button.

---

### Post by zeldagamer96 on 2011-02-11
k.  i will try it tomorrow thanks.

---

### Post by zeldagamer96 on 2011-02-13
So I was not able to redownload the disk, but I found a setting that  will make it appear to work. Or at least it did yesterday...:sad:
 
 At the CD Menu where it lets me boot from the CD and I tried some of the  options and when I press F6 and used nomodeset, it worked yesterday,  today it just says
 
 
 "No init found. Try passing init= bootarg"
Then below it says "(initramfs) and allows me to type commands... Can someone help me and try to tell me what is wrong

---

### Post by zeldagamer96 on 2011-02-13
Is it possible my drivers are not the correct ones??


Also the disk is fine because it worked on my dad's computer

---

### Post by jetaddict on 2011-02-13
I had the same issue, resolved this morning. Check out the thread:
[http://ubuntuforums.org/showthread.php?t=1686838](http://ubuntuforums.org/showthread.php?t=1686838)
just hold shift down as you go into reboot after the install to edit the grub menu. Then, once you're on Ubuntu running off the hard drive, install the Nvidia driver through the menu system. It will be good to go on next reboot.

---

### Post by zeldagamer96 on 2011-02-13
Thank You. I will need to try that when I can..:P

---

### Post by zeldagamer96 on 2011-02-18
Thank YOU!!!!! It worked and I am SO happy !! sORRY i DID NOT REPLY!!

---

