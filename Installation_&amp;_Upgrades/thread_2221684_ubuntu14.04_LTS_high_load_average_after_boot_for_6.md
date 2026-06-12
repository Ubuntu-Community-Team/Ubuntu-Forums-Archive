---
title: "ubuntu14.04 LTS high load average after boot for 6 minutes"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by jcdenton21 on 2014-05-03
Hello everybody
my main computer
Xeon x3440
8GB DDR3 Kingston RAM
Asus P7P55D-E
1TB WD 5400RPM HDD (system drive)
3TB Seagate 7200RPM HDD (data drive)
nVidia GT440 OEM 1.5GB DDR3
Seasonic S12 380W
2x Dlink DFE-580TX card
TeVii S470 DVB-S2 card


I installed Ubuntu 12.04 back when it was released and upgraded it over time to 12.04.4 with 3.8 kernel and did not have any problem

then I decided to perform upgrade to 14.04LTS via do-release-upgrade and this problem emerged

right after boot the load reported by top command starts to rise and it takes ~5-6 minutes for the system to calm down

I made a few screenshots that show this problem
strange thing is that I am not aware of any daemons that should be starting at bootup time and CPU shows 99% idle and little to no waiting-for-IO

[[IMG]http://s27.postimg.org/cu7vwo21r/Screenshot_from_2014_05_03_15_34_23.png[/IMG]]("http://postimg.org/image/cu7vwo21r/")

[[IMG]http://s27.postimg.org/t6hxmegdb/Screenshot_from_2014_05_03_15_34_51.png[/IMG]]("http://postimg.org/image/t6hxmegdb/")

[[IMG]http://s27.postimg.org/5jcdkjlnj/Screenshot_from_2014_05_03_15_35_28.png[/IMG]]("http://postimg.org/image/5jcdkjlnj/")

[[IMG]http://s27.postimg.org/wrdt5mkwv/Screenshot_from_2014_05_03_15_35_55.png[/IMG]]("http://postimg.org/image/wrdt5mkwv/")

[[IMG]http://s27.postimg.org/4v3j1lmxr/Screenshot_from_2014_05_03_15_36_46.png[/IMG]]("http://postimg.org/image/4v3j1lmxr/")

[[IMG]http://s27.postimg.org/kqsd4wdi7/Screenshot_from_2014_05_03_15_37_13.png[/IMG]]("http://postimg.org/image/kqsd4wdi7/")

[[IMG]http://s27.postimg.org/jfklwfhwf/Screenshot_from_2014_05_03_15_37_45.png[/IMG]]("http://postimg.org/image/jfklwfhwf/")

[URL="http://postimg.org/image/k6dc27k9r/"][IMG]http://s27.postimg.org/k6dc27k9r/Screenshot_from_2014_05_03_15_38_15.png[/IMG]

[/URL]
could you please help me and try to identify the culprit of this behaviour?
I did not see it in 12.04 and it is quite annoying having to wait for 6 minutes before the system is usable after boot

any ideas are welcome
if you need output of any other commands please let me know and I will post it ASAP

thank you very much in advance

---

### Post by jcdenton21 on 2014-05-04
any ideas or suggestions how to troubleshoot this?

I just wanted to add that the only proprietary driver I am using is the latest from nVidia website

---

