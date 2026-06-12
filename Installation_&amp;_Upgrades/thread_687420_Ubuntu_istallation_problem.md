---
title: "Ubuntu istallation problem"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by bookworm_2008 on 2008-02-04
I am trying to install Ubuntu 7.10 but having a problem completing the process by getting strange graphics display on the screen.

I have currently installed XP Pro & Vista Ultimate on the system with no problems. Approximately 30 GB unpartitioned space is allocated on the drive for Linux installation. The system is based on Pentium D and ASUS motherboard with integrated Intel G35 Express chip set with 4GB memory on the board.

I downloaded and made the CD for 64bit AMD/Intel based systems.

It initially starts the process fine but after a short while all I see is garbled graphics and nothing else.
:(

Any ideas?

---

### Post by Carl H on 2008-02-04
How far through the installation process do you get before this happens? 

For instance, have you got past the disk partioning stage?

---

### Post by POL(greece) on 2008-02-04
i have tha same problem with him.  i asked  someone and he said that after clicking install ubuntu i must clik (ctrl+alt+backspace) many times to continue the installation. is that correct? what i suppose to do when the screen is black?

---

### Post by jken146 on 2008-02-04
First, check the md5sum of the ISO you downloaded.  If it doesn't match, download it again, maybe with a different mirror or better still bittorrent.  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that's OK, re-burn your CD at the slowest speed you can (4x or lower is best).

There is also an integrity check option when you first boot the CD.

---

### Post by POL(greece) on 2008-02-04
the same disk works in my brother's pc what exactly i must do?

---

### Post by jken146 on 2008-02-04
Please describe your problem in more detail, POL(Greece).  At what stage does the screen go black?

You shouldn't need to press CTRL+Alt+backspace during installation.  That will kill your X session and log you out.

---

### Post by bookworm_2008 on 2008-02-04
After reading the first reply I tried the re-installation again to leave better input. Lo and behold this time the installation went through without any hick up (sure glad it did.)

So my problem is resolved. Thanks for taking the time to reply to my post.

:guitar:

---

### Post by POL(greece) on 2008-02-04
ok i choose boot from cd. then i see the list with the options. i choose install ubuntu. i dont see anything else just a black screen.

---

### Post by jken146 on 2008-02-04
The only other things I can suggest, POL(greece), without any more info from you, is to try the safe graphics mode on the CD, and to try the alternate install CD.  I have to go now, but I'm sure someone else will help you.  Hope you get it sorted :)

---

### Post by jken146 on 2008-02-04
> **POL(greece) said:**
> ok i choose boot from cd. then i see the list with the options. i choose install ubuntu. i dont see anything else just a black screen.

Please post your system specs.  You'll need at least 256MB RAM to run the Ubuntu live CD.

---

### Post by POL(greece) on 2008-02-04
there is no diference betwen choosing install and anyother option appears in first screen. the result is the same......black screen.

---

### Post by manimal347 on 2008-02-04
Just run the alternate install CD. Don't worry, it uses ANSI graphics, like those of the old MSDOS programs like Word Perfect and Lotus 123 to create menus that guide you through the installation. Frankly, it looks like the old MSDOS-Windows XP install, and isn't much harder. All prompts are well-explained, and its partitioner is a simple text frontend onto Parted so it's just as safe and easy to partition. 

f you can't get this to work, then we can take a look at your hardware. Also, when you write out this ISO, make sure you're using recent media (it decays with age and exposure), ideally Japanese, and you burn it at a reduced drive speed like 16X. Bad install media causes lots of perplexing errors.

---

