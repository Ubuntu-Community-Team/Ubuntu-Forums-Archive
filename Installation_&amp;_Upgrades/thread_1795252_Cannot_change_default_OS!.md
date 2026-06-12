---
title: "Cannot change default OS!"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by fixerman on 2011-07-02
I have installed Ubuntu 11.4 on my PC along with Windows 7. The PC boots into Ubuntu by default. I want the default to be Windows 7. I have tried to change the default OS in Windows 7 and in Ubuntu but Ubuntu is not listed in Startup manager in Ubuntu or in in Windows 7. The only OS listed under either is Windows 7 and Windows 7 is selected on both.

Please advise how to change this.:D

---

### Post by churlishbeaver on 2011-07-02
(I doubt if I can offer much help, but it's possible that people with expertise here my be able to offer me help in the thread 
[**GRUB: How to configure for what I would have thought were commonplace requirements?**]("http://ubuntuforums.org/showthread.php?t=1795228"))

I am a little confused.  "The PC boots into Ubuntu by default" "but  Ubuntu is not listed in Startup manager in Ubuntu".  If it boots into Ubuntu by default, then Ubuntu is in effect the default menu option in Startup manager.  Did you mean "Windows 7 is not listed in Startup manager in Ubuntu"?

---

### Post by fixerman on 2011-07-02
> **churlishbeaver said:**
> (I doubt if I can offer much help, but it's possible that people with expertise here my be able to offer me help in the thread 
[**GRUB: How to configure for what I would have thought were commonplace requirements?**]("http://ubuntuforums.org/showthread.php?t=1795228"))

I am a little confused.  "The PC boots into Ubuntu by default" "but  Ubuntu is not listed in Startup manager in Ubuntu".  If it boots into Ubuntu by default, then Ubuntu is in effect the default menu option in Startup manager.  Did you mean "Windows 7 is not listed in Startup manager in Ubuntu"?

I know that it sounds like I made an error in typing but, no, Startup Manager lists Windows7 as the only OS. I am totally confused also.

---

### Post by YesWeCan on 2011-07-02
> **fixerman said:**
> I have installed Ubuntu 11.4 on my PC along with Windows 7. The PC boots into Ubuntu by default. I want the default to be Windows 7. I have tried to change the default OS in Windows 7 and in Ubuntu but Ubuntu is not listed in Startup manager in Ubuntu or in in Windows 7. The only OS listed under either is Windows 7 and Windows 7 is selected on both.

Please advise how to change this.:D
I presume you are talking about the Grub2 boot menu.
That is to say, when you installed 11.04 you also installed Grub2, so when your bios boots your disk you first see the Grub menu, listing Ubuntu, Memtest and Windows7. It automatically boots Ubuntu after a time-out. Is that correct?

If so, you can change the order on the menu so Windows is listed first and is booted by default.
Boot Ubuntu. In /etc/grub.d move 30_os-prober to 09_os-prober (the lower number 09 makes Grub search for Windows and put it on the menu before it searches for linux using 10_linux):
[COLOR=Navy]cd /etc/grub.d
sudo mv 30_os-prober 09_os-prober
sudo update-grub[/COLOR]

---

### Post by foresthill on 2011-07-02
Hey OP, I think I might have the solution. I installed Startup Manager in 11.04, and noticed that when you choose the default OS, you need to go one entry further down.

For example, on my system, I have to choose the recovery mode for the kernel I want to boot up as default. If I choose the regular mode in Startup Manager, it will boot up in Windows, because that's the next entry up on my list.

It appears to be a bug in the program, but is easy to work around.

HTH.

---

### Post by fixerman on 2011-07-02
> **YesWeCan said:**
> I presume you are talking about the Grub2 boot menu.
That is to say, when you installed 11.04 you also installed Grub2, so when your bios boots your disk you first see the Grub menu, listing Ubuntu, Memtest and Windows7. It automatically boots Ubuntu after a time-out. Is that correct?

If so, you can change the order on the menu so Windows is listed first and is booted by default.
Boot Ubuntu. In /etc/grub.d move 30_os-prober to 09_os-prober (the lower number 09 makes Grub search for Windows and put it on the menu before it searches for linux using 10_linux):
[COLOR=Navy]cd /etc/grub.d
sudo mv 30_os-prober 09_os-prober
sudo update-grub[/COLOR]

There seems to be two Ubuntus, two memory tests and then finally windows7. If I scroll down to Windows7 it boots fine but I want it to boot into Windows7 by default.

---

### Post by YesWeCan on 2011-07-02
Yes, that's right. 2 Ubuntu & 2 memtests & W7.
If you do those commands you will see W7, 2 Ubuntus and 2 memtests and W7 will be the default.

---

### Post by fixerman on 2011-07-02
> **YesWeCan said:**
> Yes, that's right. 2 Ubuntu & 2 memtests & W7.
If you do those commands you will see W7, 2 Ubuntus and 2 memtests and W7 will be the default.

YesWeCan, yes we did!:KS

 After carrying out your instructions I was able to see those options in Startup Manager whereas before it only listed Windows7. I then reselected Window7 with the new extra instruction and away we went and restarted into Windows7.

Many thanks! You have been a great help to me.:popcorn:

---

