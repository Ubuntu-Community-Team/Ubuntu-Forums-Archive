---
title: "Critical Temperature reached During Install"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by mhancoc7 on 2005-02-11
Ok, I finally got the grub loader working so that is a step in the right direction.

Now after installation the Install CD is ejected and the laptop reboots. When grub loader opens I select to boot Ubuntu and start the final process of install. After quite sometime in the process the display says Critical Temperature reached 95c Shutting Down. The fan is working fine in Win Xp, but does not seem to be working when installing Ubuntu. Can someone please help me get this resolved. I am so close to my goal of dual booting linux and xp. I am a linux newbie so please if I could get step by step help that would be wonderful.

My System:
Compaq Armada 1750
Pentium III 500 mhz
192MB Ram

Thanks in advance, Jereme

---

### Post by NemoTheLobster on 2005-02-11
I had a lot of problems with overheating when I installed on my Athlon XP laptop.  It turned out part of the problem was just that my office at work was extremely hot, so I had much better luck at home (and sitting outside on a cold night).

One thing you can try is to do a custom install of just the base system.  Then get acpid and powernowd running (or I had much better luck with cpufreqd) before you apt-get install ubuntu-desktop.

I still had problems with overheating, so I've had to force it to run at 87% CPU most of the time in the cpufreqd config.  I also hacked up a script so that any time an acpi thermal_zone event is tripped, it forces it to powersave/minimum CPU for a minute to let it cool off.  Not sure if it works, but it hasn't overheated in a while!

---

### Post by mhancoc7 on 2005-02-11
Thanks for the reply.

Most of that went over this newbies head however. This is my first time experimenting wiht a linux install. I have played around with LiveCDs, but I am not familiar with actually installing it and working from command line, etc.

Thank, Jereme

---

### Post by mhancoc7 on 2005-02-11
SWEET SUCCESS!!!!

I am now officially dual booting Ubuntu and WinXp on my Armada 1750.

Thanks to for all the help. The solution was of course very simple. I did a fresh install with acpi=off by typing in linux acpi=off. Now the fan is working fine and the install completed no problems.

Now for my next big challenge. To setup Win4Lin to run Windows 98se.

Wish me luck, I am sure I will be back for more help.

God Bless, Jereme

---

### Post by unarmedninja on 2005-10-16
Hey, I have the exact same setup as you and I had the same problem.  I did a server install and then added the desktop after.  The problem i have now is the fan still wont come on.  I disabled acpi in grub but that hasnt solved the problem.  Can anyone tell me how they fixed this on a compaq armada 1750? using acpi=off on the livecd seemed to work but not on the hdinstall.

---

### Post by mhancoc7 on 2005-10-21
Hi,
I have had success by adding the following line to my kernel.

noacpi acpi=off apm=off

Now the fan comes on and off as needed. I am now trying to figure out how I can monitor the temperature. All of the applets that I have tried require ACPI.

Hope that helps.

God Bless, Jereme

---

### Post by mhancoc7 on 2005-10-23
I have found what I think is a much better solution to the overheating issue on the Compaq Armada 1750.

First I went into Synaptic and made sure that laptop-mode and laptop-mode-tools were installed. 

Second I removed the noacpi acpi=off apm=off from my kernel.

Third I installed [laptoptemp]("http://infinito.f2o.org/laptoptemp/") applet. It can be downloaded from [http://infinito.f2o.org/laptoptemp/]("http://infinito.f2o.org/laptoptemp/").

Then I added the [laptoptemp]("http://infinito.f2o.org/laptoptemp/") applet to my panel and rebooted. Now my laptop is maintaining around 63 degrees celcius. I also use one of those cool pads. I am not sure how much it helps, but I am happy with my laptops performance with the new setup.

God Bless, Jereme

---

