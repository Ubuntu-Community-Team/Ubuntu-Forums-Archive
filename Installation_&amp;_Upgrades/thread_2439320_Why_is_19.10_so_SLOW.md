---
title: "Why is 19.10 so SLOW ?"
date: 2020-03-26
forum: Installation &amp; Upgrades
---

### Post by oygle on 2020-03-26
Have been using Kubuntu 16.04 LTS for quite a while. Backup up, reformatted the HDD and did a clean/fresh install of Kubuntu 19.10

Everything is so much slower. It's not CPU as I have been checking it. Sometimes there is only 6% CPU, yet the mouse is not smooth, sometimes not able to move it at all. Overall performance is terrible, apps taking much longer to load. I search and many posts of how fast 19.10 is. Two links here but they seem to be load times

[https://askubuntu.com/questions/1184774/some-applications-on-ubuntu-19-10-very-slow-to-start/1189599#1189599](https://askubuntu.com/questions/1184774/some-applications-on-ubuntu-19-10-very-slow-to-start/1189599#1189599)

[https://askubuntu.com/questions/1194788/fresh-19-10-install-filezilla-and-beyond-compare-slow-launch-time](https://askubuntu.com/questions/1194788/fresh-19-10-install-filezilla-and-beyond-compare-slow-launch-time)

Same computer - quad processor and 4Gb ram, plenty of swap size, and HDD only less than half used. What could be causing this ?

There was a notification for "akonadi migration agent". Do I need that for KDE ?  Just remembering what a waste of resources when I used KMail (use Claws now) and anything with akonadi used a lot of resources. What else could be in 19.10 to cause the poor performance ?

---

### Post by crip720 on 2020-03-26
Would run 'top' or 'htop' in terminal and see if any process is using excess ram or cpu.  Sometimes a process gets wonky and uses too many resources.

---

