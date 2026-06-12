---
title: "update manager freeze bc dpkg"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by DeceptiveHornet on 2011-12-22
Hello!

I'm on my fourth fresh install of Kubuntu 11.10. The installation goes all fine, but when i login and am about to update the system as the first thing i do - the update process freezes at installation on 57%. Once it hits this sweet percentage, it just stops doing anything. The computer doesn't freeze but the update process is just stopped. I have googled but found precious little (read nothing) on how to fix this.

So ... i am placin my hopes in you guys and gals. Anyone know how to fix this extremely frustrating problem?

---

### Post by DeceptiveHornet on 2011-12-22
Hello!

I'm on my fourth fresh install of Kubuntu 11.10. The installation goes  all fine, but when i login and am about to update the system as the  first thing i do - the update process freezes at installation on 57%. I can't remembe the exact phrasing but the notice bar says something about installing or upgrading dkpg.  Once it hits this sweet percentage, it just stops doing anything. The  computer doesn't freeze but the update process is just stopped. I have  googled but found precious little (read nothing) on how to fix this.

My computer is a HP Pavilion G7 with Kubuntu 11.10 amd64.

So ... i am placing my hopes in you guys and gals. Anyone know how to fix this extremely frustrating problem?

---

### Post by inobe on 2011-12-22
forget about the GUI app, run the updates from terminal/ konsole.

run

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

this will get you a list of updates, type **y** for yes and hit enter.

don't disturb the process, if it stops, you will get an actual error, in any case i doubt that it'll stop.

---

### Post by DeceptiveHornet on 2011-12-22
> **inobe said:**
> forget about the GUI app, run the updates from terminal/ konsole.

run

```
sudo apt-get update
```then

```
sudo apt-get upgrade
```this will get you a list of updates, type **y** for yes and hit enter.

don't disturb the process, if it stops, you will get an actual error, in any case i doubt that it'll stop.

That did the trick! Strange ... any idea why this is happening when using the GUI?

---

### Post by AckiyBolt on 2011-12-22
hello. i have exactly the same problem.
i had installed a fresh Kubuntu, everything was fine. but when i trying to update, the progress freezes at 52% and not even trying to move. stops at stage of launching dpkg or something like that. reinstallation and google does not help =)

installed on the noname laptop from Kubuntu DVD 11.10, x32

---

### Post by rotave on 2011-12-22
how are you installing the update? through a GUI or through the terminal? if using the GUI, try updating via the terminal.

---

### Post by AckiyBolt on 2011-12-22
> **rotave said:**
> how are you installing the update? through a GUI or through the terminal? if using the GUI, try updating via the terminal.

update was installed through a GUI.

I think the problem is solved. I manually killed the processes dpkg and muon, then, through the terminal, reran dpkg:
$sudo dpkg --configure -a
update process was continued. then hard reboot and all was well =)

---

### Post by inobe on 2011-12-22
yes, the app is new, it must have been pushed upstream with a glitch.

usually updates will include the fixes, just that you have to get around using the app, terminal is the way.

personally, whether or not it's functioning properly, i still use terminal, seems faster.

---

### Post by DeceptiveHornet on 2011-12-23
> **inobe said:**
> yes, the app is new, it must have been pushed upstream with a glitch.

usually updates will include the fixes, just that you have to get around using the app, terminal is the way.

personally, whether or not it's functioning properly, i still use terminal, seems faster.

I see! Thanks for explaining it to me. I'm new to Kubuntu and am finding so much new bells and whistles all the time! I have one follow up question though. Kubuntu keeps reminding me there are security updates, but when i use the commands you gave me - it doesn't really want me to type "y". Instead it just says "3 upgradeable" or something like that. How do i do to install the security updates as well?

---

### Post by inobe on 2011-12-23
you can highlight the things in terminal, copy and paste them here.

that way i can see.

side note, after the first update, you can use the package manager instead of terminal, you shouldn't have any trouble.

---

### Post by lisati on 2011-12-24
Threads merged. 
Please do not start multiple threads for the same problem, it dilutes the community's efforts to help.

---

### Post by teh603 on 2012-01-03
I'm having the same problem in Kubuntu; Muon freezes at 53% when trying to update packages, on "running dpkg." Gonna try using the fix in the OP and see if it helps; be back in an hour or two.

Edit: If this affects you, please please PLEASE FOR THE LOVE OF PETE MARK THIS BUG AS AFFECTING YOU! [https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/905415](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/905415)

The developers don't seem to read the forums, so this is our only way to guarantee communication with them.

---

### Post by RJARRRPCGP on 2012-02-11
> **DeceptiveHornet said:**
> Hello!

I'm on my fourth fresh install of Kubuntu 11.10. The installation goes all fine, but when i login and am about to update the system as the first thing i do - the update process freezes at installation on 57%. Once it hits this sweet percentage, it just stops doing anything. The computer doesn't freeze but the update process is just stopped. I have googled but found precious little (read nothing) on how to fix this.

So ... i am placin my hopes in you guys and gals. Anyone know how to fix this extremely frustrating problem?

Help! I have a similar problem, it freezes at 48 percent with Acer TravelMate 4200 and XP Pro SP3 works fine.

---

