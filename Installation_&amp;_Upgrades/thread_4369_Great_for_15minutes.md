---
title: "Great for 15minutes"
date: 2004-11-14
forum: Installation &amp; Upgrades
---

### Post by doans on 2004-11-14
I have recently downloaded (verified MD5sums) burned CD (verified burn) and installed Ubuntu with no problems.  Appears to be a really great looking distro.  In fact I am interested in attempting to use it as my main OS (currently using Xandros).  

But, the problem is that I have not been able to use Ubuntu longer than about 15minutes before it locks up the entire computer.  Lock-ups happen at random and different points every time.  I have not found anything to bring the computer back.  I have installed various Linux distributions without problems. Don't know why this would happen.

Was wondering if anyone has exprienced the same thing? If so, how do I fix it?  Or how can I diagnose this intermittent lock-up problem?  Any help would be much appreciated.  Also, fairly new at Linux.

---

### Post by sfw5000 on 2004-11-14
To start you might want to post your hardware -- what mobo/chipset/video card do you have? You might be having some kind of basic driver problem... Also did you install the stable warty or the nightly build?

---

### Post by TravisNewman on 2004-11-14
When you boot the computer, press esc to bring up the grub menu and run a memory test. I've had major problems with lock ups when my memory was bad.

---

### Post by doans on 2004-11-14
[QUOTE=sfw5000]To start you might want to post your hardware -- what mobo/chipset/video card do you have? You might be having some kind of basic driver problem... Also did you install the stable warty or the nightly build?[/QUOTE]
 I have ECS K7S5A Pro motherboard, NVIDIA Gforce2 MX400, and SiS® 735 Chipset.  As I said I have 5 or 6 OS installed and have never encountered this problem before.  I installed Warty release version.  I will try the memory check when I reboot.  Thanks for the help.

---

### Post by adbak on 2004-11-14
Sorry you are having problems.  I don't know how to remedy this problem of yours, but I do want you to persevere because

Ubuntu is worth it!

Don't give up.  Ubuntu is well worth it.

---

### Post by ubuntu-geek on 2004-11-15
[QUOTE=adbak]Sorry you are having problems.  I don't know how to remedy this problem of yours, but I do want you to persevere because

Ubuntu is worth it!

Don't give up.  Ubuntu is well worth it.[/QUOTE]
 I have had this issue when running on the default "nv" drivers for Nvidia. I suggest if you havent already here and installing the better Nvidia drivers.

Take a look at section 2 under Nvidia
[http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

---

### Post by trico on 2004-11-15
I think I have the problem you're describing too - and don't have a solution.  My system takes much longer to lock up.  A few times it has been as quickly at 30 minutes to an hour.  Most times its locked up in the morning if I leave it up over night.

I think it has to do with the Gui and have been slowly looking for things in that area to fiddle with.   Nothing has made a difference so far and I've been thinking about trying out xorg on he hoary beta.

My system is an IBM x86 pc, 2.4 ghz with HT, 512 mbytes memory, two disk drives (swap partition is on the first along with windows parition, ubuntu is on the second),  usb 2.0, keyboard, usb wheel mouse and ethernet.  The graphics is pretty standard, just the Intel Graphics chips that came with the system, no  video cards.  The display is a 1280x1024 mitsubishi lcd panel.

trico

---

### Post by Marauder1 on 2004-11-15
Could be an OpenGL prob.
Try to run an OpenGl screensaver and see if it bugs.
( Just something i had on previous distros ). :-? 

AND DON'T GIVE UP, YOU LEARN AND WE ALL !!!! [-X

---

### Post by doans on 2004-11-16
[QUOTE=ubuntu-geek]I have had this issue when running on the default "nv" drivers for Nvidia. I suggest if you havent already here and installing the better Nvidia drivers.

Take a look at section 2 under Nvidia
[http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)[/QUOTE]
 I believe thats it!  I installed the nvidia driver instead of using the generic "nv" driver and now I can see the greatness for longer than 15mins.  Very stable at the moment.  Thanks.

---

### Post by avallon on 2004-11-16
Since I am very new in all of this, I would like to ask you the question related to your statements in the first message of this thread:
- md5sum - I have learned how to do this

- check burnt CD - How would I do this? 

I have at my disposal Nero Express in W2000, the same Nero in XP and K3B in Mandrake 10.0. Unfortunately, to this day I have not been able to install ubuntu on my notebooks.
I did check the Ubuntu CDs during installation with the option during install, but it would be great to check all Cds with the other distributions ( as if I am collecting them), such as Impi1 and Impi2, Mandrake Move 1 and Move 2, Suse 9.1, Gento from Linux format magazine.
Please help

---

