---
title: "Acroread black screen in firefox"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by wwbdd on 2011-04-07
Most every time in firefox that I open a pdf, the window comes up completely black. I seem to have been able to resolve the issue temporarily by reinstalling acroread, but then I get a black screen for the next pdf I open. So I wind up reinstalling acroread several times a day to open pdfs.  There has got to be some better solution. Anyone know what to do about this?

---

### Post by wilee-nilee on 2011-04-07
> **wwbdd said:**
> Most every time in firefox that I open a pdf, the window comes up completely black. I seem to have been able to resolve the issue temporarily by reinstalling acroread, but then I get a black screen for the next pdf I open. So I wind up reinstalling acroread several times a day to open pdfs.  There has got to be some better solution. Anyone know what to do about this?

I have at times a problem similar generally hitting the reload at the right end of the URL window reloads it to show, I have had to run this reload up to 5 times, using the esc to stop or clicking the url bar and then enter. I have at times had to turn off some of the add-ons like noscript that I have tweaked to block some script needed.

These are pdf's though from research publications through my college library's data base and google scholar, turning off noscript in this circumstance is a fairly safe move. I am running Linux so I have  certain amount of built in safety not running in root.

Hard to say if any of this helps, I have started having this problem lately, I'm not sure it isn't a FF4 thing.

---

### Post by martine.ginette on 2011-06-02
does

sudo apt-get install mozplugger

help?

---

### Post by gromoloser on 2011-08-01
mozplugger solved the problem. Thanks.

---

### Post by lucacerone on 2011-08-18
> **gromoloser said:**
> mozplugger solved the problem. Thanks.

Hi, I could solve the issue by disabling Adobe plugin
it the preference tab of firefox.
Without doing it it seems that mozplugger and adobe somehow
constrast one each other.

---

### Post by sea-geek on 2012-04-11
Using FF 10.0.2 in Ubuntu 10.04 and was getting this same problem
for the last few months.
This solved my problem and I didn't even have to restart FF:

sudo apt-get install mozplugger

Thanks!

---

### Post by ProgRobUK on 2012-09-22
Ubuntu 11.10. Had to install Acroread to fix other pdf problems and started getting black screen issues.

This fixed it for me too!

Thanks

---

### Post by habana on 2012-10-01
Fixed for me too. Many thanks.

---

