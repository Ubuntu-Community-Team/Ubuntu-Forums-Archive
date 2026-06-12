---
title: "What's the best way to upgrade to Intrepid from hardy?"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bwallum on 2008-09-21
Hi All

I now have a machine available that is not a production unit. Quite ok to mince, dice, slice or obliterate but I would like to test upgrading from Hardy to Intrepid alpha 6.

So...can anybody tell me how to upgrade to Intrepid please using the terminal.

Regards
Bob

---

### Post by Patrick793 on 2008-09-21
```
sudo update-manager -d
```
should work.

---

### Post by Kevbert on 2008-09-21
Best way is to use
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
A more stable way to do it is to burn yourself a copy of the latest Alpha release to CD and then install from there.

---

### Post by kevpan815 on 2008-09-21
Clean Install From Either The Alternate CD ISO Images (The Live CD's Are Still Troublesome On My 2 Test Machines), And/Or The DVD ISO Image Using The Debian Installer Package (Same As Alternate CD Installer).

---

### Post by bwallum on 2008-09-21
> **Patrick793 said:**
> ```
sudo update-manager -d
```
should work.

Does work Patrick, thank you, hole in one. For me, being at the end of a very long wire (60kB/s) in the Scottish Borders it will be around 3 hours or so before I get to try it.

Thank you very much
Bob

---

### Post by taavikko on 2008-09-21
```
sudo do-release-upgrade --devel-release
```

---

### Post by bwallum on 2008-09-21
> **Kevbert said:**
> Best way is to use
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
A more stable way to do it is to burn yourself a copy of the latest Alpha release to CD and then install from there.

Thanks for the help but this does not work for me. It updates Hardy ok but doesn't get the Intrepid repositories and upgrade.

```
sudo update-manager -d
```does the job though. just noting the difference in case others follow the thread,

Kind Regards
Bob

---

### Post by Kevbert on 2008-09-21
Good luck with the upgrade.

---

### Post by ronacc on 2008-09-21
@ bwallum  for the first method to work you have to edit your sources list (/etc/apt/sources.list) to change each instance of hardy to intrepid .After making myself a 200 year supply of coasters with brassero I installed K3B ;)

---

### Post by tom-ubuntu on 2008-09-21
> **Patrick793 said:**
> ```
sudo update-manager -d
```
should work.

That's what I used aswell (for 8.10 and also previous version; well, since supported actually ;-)). Works fine.

---

### Post by gjoellee on 2008-09-21
I used a CD

---

### Post by bwallum on 2008-09-23
Intrepid up and running using Patrick793 method. Seems to be stable, quick and not much difference visually from Hardy. It 'just worked', including finding the router and Internet. I managed to break the upgrade when instead of closing the Java licence window I closed the terminal instead. (yes I did flagellate myself to within an inch of life) Upon reboot I went back to Update manager and it continued to install the upgrade. That's pretty good in my book. I'm now trying to find bugs and report them before they get fixed, not found an unreported one yet!

---

### Post by dawynn on 2008-09-24
In my experience, had to reinstall.  Upgrade from Hardy to Intrepid broke pulse-audio in a way I was unable to repair.  Install from CD gave me sound.

---

### Post by Sef on 2008-09-24
1) Best way is a clean install.

2) Upgrade - all may work fine, but then something may not fail to work.

---

