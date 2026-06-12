---
title: "Ubuntu 10,04 not recognising battery"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by basilwatson on 2010-03-01
I am not sure where this question should be posted so please forgive 

Anyway I couldn't wait for the final release of Ubuntu 10.04 so I installed it on my 
MSI u100 

all has gone well except the battery 

when I unplug the power lead it say 2 min left and shuts down , even though the battery is full
also the battery indicator is flacky and flicks on and off

where would I go to solve this problem 

all else is ok !!!

Thanks in advance and sorry if its in the wrong place ...

Stephen[
s@s-laptop:~$ cat /proc/acpi/battery/BAT1/statepresent:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      1962 mAh
present voltage:         12418 mV
s@s-laptop:~$

---

### Post by basilwatson on 2010-03-01
I am not sure where this question should be posted so please forgive

Anyway I couldn't wait for the final release of Ubuntu 10.04 so I installed it on my
MSI u100

all has gone well except the battery indicator

when I unplug the power lead it say 2 min left and shuts down , even though the battery is full
also the battery indicator is flaky and flicks on and off and disappears for some time 

but when I boot using battery power all is well
where would I go to solve this problem

all else is ok !!! AND MY UNBROKEN IPHONE IS RECOGNIZED !!!!

Thanks in advance and sorry if its in the wrong place ...

Stephen[
s@s-laptop:~$ cat /proc/acpi/battery/BAT1/statepresent: yes
capacity state: ok
charging state: charged
present rate: 0 mA
remaining capacity: 1962 mAh
present voltage: 12418 mV
s@s-laptop:~$

---

### Post by Gadgetech on 2010-03-21
Running the Beta1 now. Unplugging initially shows 4 minutes remaining. After that, clicking on the applet icon correctly shows 4 hours. Things are getting better.

---

### Post by NightwishFan on 2010-03-21
I have a power related issue as well, my system will not blank my screen automatically. It 'can' blank just not automatically.

Perhaps this is related to the dropping of HAL? I would post a bug:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

