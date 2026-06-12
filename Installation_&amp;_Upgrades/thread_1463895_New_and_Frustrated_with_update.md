---
title: "New and Frustrated with update"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by rd-350 on 2010-04-27
hi i am new to ubutu and linux. i just got my ubuntu and  cd last month and finally decided to install it on my 2nd pc.
my config is as follows 
amd athlon xp 2000+
Ram:1.5gb

now my problem and the reason why i am really frustrated is as follows.
I have tried installing and then updating my ubuntu 9.10 11 times.
Thats right ELEVEN TIMES and each time i try to update the OS the comp keeps getting f****d up.There is no problem during installation only the update is a MAJOR problem.
Let me summarize what all i have tried till now.

the 1st time  installed it via the cd all was smooth till this update manager pops up after i restart my comp after install.i am like yeah this is just like windows and  go ahead with the upgrade.after downloading during install no errors. i restart the comp as advised.during boot up the os hangs on the white ubuntu sign and my caps and scroll lock start blinking.i restart the comp thinking might be some error and this time i get a kernel load error. have to reinstall

then i reinstall again no problems this time i look around the net a bit and find that people say update via terminal is better so i go ahead with that again download all updates installed them no problems. the moment i restart grub throws up this screen with 4 modes ubuntu ,ubuntu (recover) memtest,memtest (recovery)
i choose the 1st option wham again some shitty critical kernel error.

ok at this point i was really pissed so i see the ubuntu site for solutiosn during which 
my eyes fall upon 10.04 RC and i am like ok must be the updated version so should not have all those update problems i download the .iso and run the cd wham some shitty critical error the installation doesnt even start...i have noticed quite a few people have got this problem.

again i installl 9.10 and this time i do "update-manager -d" and try to install 10.04 via update manager download and install is fine and terminal screen in update manager shows no errors during install. i restart my comp wham again kernel error damn thing wont boot.

i even tried installing ubuntu 9.10 from a fresh iso downloaded from the net and not the cd but same results.
i am pretty new so still learning to work with the os.:confused:
so any willing to help me please do so as if you were teaching a child.
thanks

---

### Post by wyliecoyoteuk on 2010-04-27
The RC is only a release candidate, not the official full release.
It sounds like you have some sort of problem with the hard drive installation.
This can happen with some hard disk controllers, where the PC BIOS changes the boot order.

How many disk drives do you have?
Are they IDE or SATA?
Does the CD work OK in Live mode (not installing, just running from the CD)

---

### Post by rd-350 on 2010-04-27
i have 1 40 gb IDE drive in and no other peripherals connected.
yes live mode works just fine.

---

### Post by rd-350 on 2010-04-27
bumping this up no reply yet

---

### Post by greenstar on 2010-05-17
During installation, instead of formatting your Ubuntu partition as ext4, try using ext3. I've solved a good number of problems just by sticking with the tried and true ext3.

---

### Post by Chronon on 2010-05-17
I would download the 10.04 final release now.  It's generally better to do a fresh install instead of upgrading.

---

