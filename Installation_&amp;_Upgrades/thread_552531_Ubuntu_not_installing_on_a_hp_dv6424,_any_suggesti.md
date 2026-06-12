---
title: "Ubuntu not installing on a hp dv6424, any suggestions would be appreciated, thanks!!"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by linuxuser187 on 2007-09-16
Hi everyone, i would like to know if anyone could help me with installing linux onto my HP dv6424ca as i'm running into trouble, i am a bit experienced eith linux as i used to used mandrake before, i made a boot cd of ubuntu 64bit and 32 bit, mandriva 64bit and 32bit, suse 32bit and all have the same problem, when i'm booting up the cd it's fine then i choose to install and it tells me that it's loading the kernel after wards it says loading a couple of things in text format and ok but then it comes up to a point that it says it can't access a certain memory range, it continues ahead and when it was trying to detect some hardware it stays frozzen on the text screen, all the linux cd;s i've mentioned above have this problem, tried to run live cd's as well but same prob, there definately is a hardware detection issue somewhere and i think that it's something to do with a section of my ram memory that's reserved and linked for my nvidia geforce 7200 videocard as it uses shared system ram, does anyone have any ideas as i see that you guys were talking about the HP dv6424ca, if it helps when installing suse it comes up to a point to verify the cpus and says the model and info of the cpu then it said something which i'm trying to remember, i think it said id 1 id 2 mismatch but then it said corrected and stayed frozzen there, i also tried to install with the command line to disable apic and local apic, same thing, any input at all would help!

Thank You!

---

### Post by Pumalite on 2007-09-16
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by linuxuser187 on 2007-09-16
Thanks for the info, much appreciated, i will try all of that out right after i finish work! :)

---

### Post by Pumalite on 2007-09-16
Good hunting!

---

### Post by linuxuser187 on 2007-09-16
i tried putting in the command at the boot screen noapic irqpoll noirqdebug and it worked! thank you again! :)

---

### Post by Pumalite on 2007-09-16
You are welcome. Good for you!

---

