---
title: "HELP! no display after installing updates for 8.10"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Brickedin21 on 2008-10-20
hello, i installed 8.10 ibex with no issue, everything was working fine. after i was done installing i was prompted to download updates. so i did, afterwards i restarted as usual, and then boom, no display. the log on sounds and everything are there... just no display... i did sudo etc/init.d/gdm stop    from pressing control alt f1 but it didnt work. not sure what else to do... any help would be greatly appreciated... thank you.:confused:


I have a Toshiba A305-S6898 Special Edition
ATI HD 3470 Video card...

---

### Post by overdrank on 2008-10-20
Moved to Intrepid Ibex Testing and Discussion

---

### Post by jerrylamos on 2008-10-20
On my IBM Thinkpad R31 I get a similar no display.  In my case the trouble is compiz, the "eye candy" special effects for splashes, fades, yata yata.  See launchpad bug 277344

To see if compiz is the culprit, try:

Boot in rescue mode.
At the window select root command line.
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If this works, you're O.K.  If it doesn't, maybe someone else with similar hardware to yours would have an idea.

If you do get running with internet access and want to try compiz, you can always sudo apt-get install compiz & sudo apt-get install compiz-core.
Then presuming it boots O.K. do System Preference Appearance Visual Effects and choose your eye candy option.  Bear in mind visual effects do eat CPU power and time slowing response time.

Since I do Alpha's and Beta's and other buggy code prior to release, I have two installs on this Thinkpad.  One runs O.K. it's an Alpha 5 Intrepid NOT UPDATED, the other is for testing in this case Intrepid Beta with compiz removed.

Jerry

---

### Post by Brickedin21 on 2008-10-21
thanks! but it didnt work lol, im still stuck.

---

