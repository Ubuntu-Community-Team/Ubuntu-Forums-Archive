---
title: "Upgrade from 10.10 to 11.04 error. I am stucked"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Mantsa on 2011-04-28
Hey

Today I upgraded my 10.10 to 11.04. Since the last step of upgrading, when it was restarted, I get stucked in consola where it is checking, and there is written fail at stopping automatic crash report generation. 

How can I repair it. I tried to do 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo reboot

but it doesn't do it properly.

Please help me

---

### Post by kansasnoob on 2011-04-28
We need to know exactly what the error message says.

I do know the servers are simply flooded ATM.

I even got bounced using the zsync server :(

---

### Post by Cristobal:gallardo on 2011-04-29
I have the same problem :(

---

### Post by KegHead on 2011-04-29
Hi!

There has been many reports of overwhelmed servers.

Try;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead

---

### Post by aniac on 2011-04-30
I have the same problem and the above doesn't resolve it. Everytime I re-boot, the server says "stopping automatic crash report generation [failed]". Could anyone help please?

---

### Post by Riskexas on 2011-04-30
dont care about this post i acedently post it

---

### Post by Riskexas on 2011-04-30
well im not good at ubuntu but if i launch ubuntu normaly as i do in 10.10 nautilus (or something else) doesnt start :confused:. only whit safe mode i can do something :|
if u want more specific explain here it is: i login and folders (on desktop) blinks. if i manage to open a new window (like help) there is no top of bar (i dont know how to call it see in attach)

by the way i didnt want to create new topic so answer this :-k

---

### Post by teguhb on 2011-05-02
[B][SIZE=2]I got this error message:
[/SIZE][/B]
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

---

### Post by aniac on 2011-05-06
Hi guys, are there any news regarding the above issue "automatic crash report generation [failed]" ? 

I have 5 questions and would appreciate if you could answer these for me please: 

1. How serious is this issue? 
2. What is the reason for this happening? 
3. Can this be fixed or do I need to reinstall Ubuntu Server 11.04? 
4. Will this issue re-occur on a fresh Ubuntu 11.04 Installation? 

I hope to hear from you soon again! 

Regards,

---

