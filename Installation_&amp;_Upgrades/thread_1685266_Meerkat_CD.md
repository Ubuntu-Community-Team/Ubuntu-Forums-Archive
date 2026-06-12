---
title: "Meerkat CD"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by lupo1939 on 2011-02-10
I downloaded 10.10 and burned it to a CD.  When boot is attempted from the CD it spins and a 'stickman' appears at the bottom of the screen.  No message(s).  If I press and hold enter, the screen to select language appears.  After English is selected 5 choices are listed:
Try without install
Install
Check disk
Test memory
Boot from hard disk
I want to try 10.10 without doing an install.  When that option is selected the CD spins but nothing happens.  I have tried check disk with the same results.  Test memory works.
What am I doing wrong?

---

### Post by dino99 on 2011-02-10
is it with the "alternate" cd ?

---

### Post by lupo1939 on 2011-02-10
Not sure what you mean by alternate.  I set the bios to boot from the CD as first choice.  The CD was burned from a download.  Is there a way to check the 'health' of the CD?

---

### Post by plucky on 2011-02-10
Did you run an MD5SUM on the downloaded ISO?

See [HowTo MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> Is there a way to check the 'health' of the CD?


That is the "Check disk" option on the list.

Is the light on the CD drive flashing when you are select "Try without install" option?

---

### Post by lupo1939 on 2011-02-12
The light on the CD drive blinks on and off, slowly.  Nothing seems to happen, however, even if left to run for some time.

Will read the MD5SUM directions and report back after running.

---

### Post by mörgæs on 2011-02-12
How much memory does the machine have?

---

### Post by lupo1939 on 2011-02-12
machine has 4mb of memory.

I read the md5sum instructions but cant get the cd command to work.

File name is ubuntu-10.10-desktop-i386.iso
I've tried several combinations for a prefix, including none, but get
ted@Teds:~$ cd ted.desktop.ubuntu-10.10-desktop-i386.iso
bash: cd: ted.desktop.ubuntu-10.10-desktop-i386.iso: No such file or directory
as a reply.  What does it want for file name?

---

### Post by plucky on 2011-02-12
> machine has 4mb of memory.

I assume 4 Gigabyte of memory

This command makes no sense 
> cd ted.desktop.ubuntu-10.10-desktop-i386.iso

It should be ```
cd ~/Desktop
``` if the file is on your Desktop.

Which is the same as```
cd /home/ted/Desktop/
```

Linux is case sensitive.

Then ```
md5sum ubuntu-10.10-desktop-i386.iso
```

Hope this helps

Good Luck

---

### Post by lupo1939 on 2011-02-13
The download is bad.  The first 4 characters in the hash document are f59d, from running the md5sum command f64c.  Guess I need to do another download.  If it doesn't work, I'll have to buy a 10.10 CD.

  If the snow ever melts, I'm changing ISPs.

---

