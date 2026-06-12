---
title: "A-2 not installable"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by randiroo76073 on 2009-07-02
I've tried both desktop and alternate installs. Desktop-ubiquity failure at partitoning, Alternate-fails at grub install, both legacy & g-2. Both downloads md5 = good, slow burn = 4x, disk self-check = good on both.
Where to now???

---

### Post by douham on 2009-07-02
randiroo76

To install Alpha2, chase up on the release notes for A2 and follow up on the bug report re;Grub2 in launchpad. I think there is a solution.

---

### Post by graaant on 2009-07-02
This doesn't sound like the Grub2 bug though?

Maybe try a daily image?
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by randiroo76073 on 2009-07-03
Thanks for replies
@-douham: I think if it were that then grub legacy would install ???
@-graaant: Will give that a try, thanks for link.

---

### Post by tad1073 on 2009-07-03
> **randiroo76073 said:**
> I've tried both desktop and alternate installs. Desktop-ubiquity failure at partitoning, Alternate-fails at grub install, both legacy & g-2. Both downloads md5 = good, slow burn = 4x, disk self-check = good on both.
Where to now???

I also got ubiquity errors during partitioning but I ignored them, install went fine and every thing is working great.

Linux thomthom 2.6.31-1-generic #14-Ubuntu SMP Thu Jul 2 16:02:38 UTC 2009 x86_64 GNU/Linux w/ nvidia driver 185.18.14 + patch

---

### Post by randiroo76073 on 2009-07-03
@-graaant: Thanks, that did the trick :) But, ARRGH, just updated Jaunty- xlrunner and it wiped out my graphics(I'm posting from Mint 7,am multibooted/chainloader), so have to get in and figure that out. LOL! ain't that great! Oh well-ROFLMAO that's life.

---

### Post by caryb on 2009-07-03
Can comfirm the same with Kubuntu


Cary

On the 3rd attempt it crashed but I was able to boot the drive & update, now have to work out how to get grub to recognise my other installs on the disk:-)

CB

---

### Post by caryb on 2009-07-04
Well I can report that rebuilding was the best thing I could have done;) It has fixed so many problems. Not in any order..

1) It now installs the GLX (Nvidia) driver properly
2) Network applet now works for wireless (wep)
3) Sound works flawlessly only gotcha for Kubuntu users is non-free-codecs installs  pulseaudio I removed it before it caused me any grief.
4) Weather picture background now works

I think the upgrade from KDE4.2 to 4.3 is not a clean as previous upgrades, my only fault I can see so far is plasma still crashes regularly & you will have to do the remove the dreaded Grub floppy problem in previous posts.


Cary

---

