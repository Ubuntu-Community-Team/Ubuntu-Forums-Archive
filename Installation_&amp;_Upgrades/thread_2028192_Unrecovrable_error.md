---
title: "Unrecovrable error"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by OldTelephone on 2012-07-17
I wanted to install Xubuntu on a old computer, a 850Mhz Celeron with 512 Mo ram. I have tried to install it but I got a message :" The installer encountered an unrecoverable error..." Then it started a live CD desktop session so I could investigate the problem But I don't Know what to do.

Then I have tried to install Lubuntu, from the CD I could test the memory and the CD. Both were good. But the installation just froze in the middle. 

Should I try an another distro?

---

### Post by sudodus on 2012-07-17
Welcome to the Ubuntu Forums :-)

When you can run a live session, it is also possible to run the same system installed, but sometimes it is a little tricky to find what to tweak.

Did you use any boot options to make the live sessions work? In that case you need them also in the installed system, but you have to enter them in a different way.

What about your internal hard disk drive and its partitions. If you run a live session and post the output of the following command, it might be easier to help.
```
sudo fdisk -lu
```

You might also have problems with the installer itself. In this case, it might work better with the alternate installer. For that old computer I would recommend Lubuntu.
[[COLOR="Red"]_http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-alternate-i386.iso_[/COLOR]]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-alternate-i386.iso")

---

