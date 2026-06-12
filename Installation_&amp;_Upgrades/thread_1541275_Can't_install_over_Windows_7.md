---
title: "Can't install over Windows 7"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by truthtopower on 2010-07-28
I just bought a new lap top, and I can't get the Ubuntu install to work. I've installed Ubuntu on other computers about 6 times or so, but always over a Windows XP or Vista operating system, this is the first time I've tried to install it over Windows 7.

I tried using a CD and a boot stick, but it still boots into Windows rather than booting from the device. I've checked the boot setup and it's setup right, to boot from the USB/CD depending on which one I attempted, but no cigar, still loads up Windows instead. I'm at a loss.

The computer is an Acer Aspire 5251-1513
AMD processor V120 2.2GHz
2 G DDR3 RAM

Please help, I hate using Windows.

---

### Post by tachyon4 on 2010-07-29
this isn't a problem with ubuntu or windows 7.  it's either your computer or your CD.  here are a few things to try:

on power up, hit f2 and enable boot menu.  then hit f12 to select boot device (e.g. CD).  reboot with CD in drive.

if this doesn't work, try using eSettings Management (boot options) and alter the boot sequence.  then reboot.

if you're still having problems, perhaps your ubuntu cd is to blame.  did you check it with md5sum?  did you burn it as an image?  one way to check that everything is alright with the CD is to boot into windows 7 and find the CD in "my computer".  does wubi work (don't set it up, but check to see if the software is corrupt)?  you may need to remake your CD.

you might also experiment with other live CD's.  find a random one online.  if your computer can boot on another live CD, your ubuntu CD is the problem.  if you computer always boots into windows 7, you need to figure out your boot settings (check out the acer forums).

---

### Post by greenmax07 on 2010-07-29
I download ubuntu in win 7 then install into usb drive ....re-boot with usb and i have muti-boot for now .........it worked great   this is a hp 64 bit system

---

### Post by brokenromeo on 2010-08-03
I just installed on that same laptop, you need to go into the bios and enable the boot option menu (F12). I am dual booting, but you can install however you want. Ubuntu 10.04 64 bit is running great on mine...a few of the function keys don't work, but most do. Great deal on that laptop!

---

### Post by Gregma80 on 2010-08-04
Hi, sorry to barge in. I'm kinda new to this blogging thing and am not sure about the "unwritten code of conduct" forums. But, I have a off topic question I hope to get an answer to. Well, I have the exact same computer as the original poster (acer aspire) I just it bought yesterday and I noticed it didn't come with any sort of a recovery disk. It runs Windows 7 that came pre-installed and I would imagine they would give you a recovery disk of some sort (its been many years since I purchased a computer). But, for $298 I guess I can't complain. Any suggestions would be greatly appreciated. Sorry if I over lapped or whatever they call that on these threads or forums.  Again I apologize if my conduct was inappropriate. I just don't understand how to keep track of all these threads with that many user names and passwords every time I Google a topic and find a helpful forum? There's thousands of them!

---

### Post by dandnsmith on 2010-08-04
What you've done is hijacked the thread - something better not done, as it splits the attention and causes doubt as to which question is to be answered.

I don't understand from your posting what the question is, so just start a fresh thread with your question (I suggest you read the bits on how to post, and what to provide in the way of data), and then you can use the search (topic or author) to find the thread again.

---

### Post by brokenromeo on 2010-08-04
Acer does not ship with physical recovery disks as many manufacturers don't, you can either order them from the Acer website for $20, or generate them yourself using the included acer application that came preinstalled in your laptop, in the acer program group. I have this same laptop and it runs Ubuntu 64 bit well.

---

