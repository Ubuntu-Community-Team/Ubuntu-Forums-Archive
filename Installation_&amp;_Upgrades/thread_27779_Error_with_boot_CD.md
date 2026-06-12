---
title: "Error with boot CD"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by cmay119 on 2005-04-17
I just burned in ISO Image of the 5.0.4 that was made bootable. Once I boot up the system though to start the install off the CD, I get an error that says:

"EMM 386:Warning:Address Line A20 Already Enabled." Then the system just sits there, and I have to hard reset the machine. (CTRL+ALT+DEL Doesn't work). 

I'm trying to have a dual boot system with an install of Windows XP Pro. Ubuntu 4.10 had no trouble booting from the CD. 

Any suggestions on what to do? Or what the problem could be?

---

### Post by andvaranaut on 2005-04-17
Hi cmay119,

You probably have recorded the ISO image as a regular file; it must be written as a CD image instead. The main symptom is that, when you see the CD contents (eg. with Windows Explorer), only a file shows up; it should actually be a bunch of files and a few folders. Please see [http://ubuntuforums.org/showthread.php?p=136991](http://ubuntuforums.org/showthread.php?p=136991) , I just posted a reply to a similar problem.

Hope this helps, andvaranaut

---

### Post by cmay119 on 2005-04-17
okay, thank you very much advaranaut. I'll give that a try.

---

### Post by cmay119 on 2005-04-18
Thank you very much Andvaranaut. It worked perfectly. I appreciate the help :)

---

