---
title: "Installed version 7.01 in error, how do I erase and load 10?"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by eckelsburrows on 2010-08-25
A real newbie mistake, used an old CD and it installed version 7.01 on a rebuilt compaq presario.  It is an assortment of various parts, not all orginial.

The CD/DVD RW drive won't work or mount, but internet (firefox) works fine.  I tried to down load and install version 10, but it tried to burn a disk...actually burned something on the disk, but can't read whatever it wrote.

How do I get version 7 off this machine and version 10 on?

I am not a techie at all, but running a tiny non-profit organization and I just couldn't afford to pay for windows, and I love open office so I decided to try ubuntu.  Thanks for any help you can provide!

---

### Post by Sef on 2010-08-25
> The CD/DVD RW drive won't work or mount, but internet (firefox) works fine. I tried to down load and install version 10, but it tried to burn a disk...actually burned something on the disk, but can't read whatever it wrote.

1) Did you burn the iso as an iso?  

2) Do you mean you installed 7.10? (7.01 does not exist.)

3) Do you have usb on the computer?

4) Do you have another computer that you can download Ubuntu to?

---

### Post by eckelsburrows on 2010-09-05
Thanks for posting back so quickly.  Spent the week in intense negotiations with my better half.  We've decided to take that machine, a Dell, and putting XP bacvk on it for him, and taking another machine, which I also loaded 7.10 on and keeping that as our linux machine, and upgrading it to version 10

So, in the interest of family harmony we'll need to know how to get ubuntu OFF the dell and XP ON it.  any ideas how I do that?

Then I can work on my linux machine.  Later this week I will set up the linux machine and test it for working hard drive, usb ports etc.  then i will post back.  I Think the disk I burned was an installation disk, but I don't really know for sure.  Is that what you meant by ISO?

thank you again for helping me!
Brenda

---

### Post by pricetech on 2010-09-05
Short answer: DBAN.  Use the autonuke command to do a DOD wipe on the drive.

Slightly longer answer: At install time have the OS you are installing remove the old partition and create a new one.

Longer answer: Boot to the Ubuntu live CD and use GParted to remove the partition from the drive, then install.

Even longer answer: Download and install the Windows AIK from Microsoft (free) and create a Windows PE disk.  Handy if you do a lot of work on windows computers.  Use "diskpart" to clean the drive.

I've used all the above and they all work.  My "favorite" method depends upon the circumstances.

---

### Post by eckelsburrows on 2010-09-06
thanks...I think that theone he wants windows on will probably require the AIK solution, but the other ones probably could be the short solution.  Will spend my evenings this week playing with them....thank you again

---

