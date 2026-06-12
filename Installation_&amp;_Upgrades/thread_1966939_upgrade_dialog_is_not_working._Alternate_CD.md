---
title: "upgrade dialog is not working. Alternate CD"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by excobra on 2012-04-27
[FONT=Arial]Hi 

i am using 11.10, NOw i am trying to upgrade to 12.04 using alternate cd. (Please don't ask why i am using this method and not others).

i followed the procedure mentioned at [https://help.ubuntu.com/community/PreciseUpgrades.]("https://help.ubuntu.com/community/PreciseUpgrades")

i successfully created the directory using `
[/FONT]```
sudo mkdir -p /media/cdrom
```[FONT=Arial]then i executed the command in terminal as instructed
[/FONT]```
sudo mount -o loop ~/Desktop/ubuntu-12.04-alternate-i386.iso /media/cdrom
```[FONT=Arial]it showed the folloing result in terminal

```
mount: warning: /media/cdrom seems to be mounted read-only.
```But after that now upgrade dialogue was shown,

so then i executed

 [/FONT]```
gksu "sh /media/cdrom/cdromupgrade"
``` [FONT=Arial]by pressing alt+F2

even then there was no upgrade dialogue

so i tried again the same command but without commas("")

like this 

```
gksu sh /media/cdrom/cdromupgrade 

```[/FONT][FONT=Arial]it did bring the upgrade dialogue,

[/FONT][FONT=Arial]then it says that i need to download the data as this much data needed , please see attached image
[IMG]http://i47.tinypic.com/mb1uuw.png[/IMG]

[/FONT][FONT=Arial]Now the whole point is i cant use Internet to upgrade to 12.04. ans that is why i downloaded the alternate disc,

then it showed the following messages and end

[IMG]http://i45.tinypic.com/f1w3k1.png[/IMG]

[/FONT][FONT=Arial]NO upgrade. 

Please help how can i upgrade to 12.04 sing alternate disc. 

[/FONT]

---

### Post by darkod on 2012-04-27
I don't know about the alternate cd but the latest versions offer the option to upgrade with the standard live cd. And I don't think it needs internet during the upgrade.

If you can get hold of the live cd, you can try that way.

---

### Post by haresear on 2012-04-27
> **darkod said:**
> I don't know about the alternate cd but the latest versions offer the option to upgrade with the standard live cd. And I don't think it needs internet during the upgrade.

If you can get hold of the live cd, you can try that way.

I've tried the live ISO, but don't see that option. How do you get it to expose that option. The options I'm offered are:
1. Install along side existing OS(s)
2. Erase and use entire disk.
3. Something else (manual partitioning).

(One of the existing OS is U11.10.)

---

### Post by darkod on 2012-04-27
I have no idea. Yesterday I was testing some scenarios in virtual box, and had 11.10 installed first. Then when I booted the 12.04 live cd into live mode first, and clicked the Install 12.04 icon, the option to upgrade 11.10 was there.

Now sure if it has anything to do with dual boot. I had only ubuntu in my test system.

---

### Post by ajohnson2371 on 2012-04-27
> **haresear said:**
> I've tried the live ISO, but don't see that option. How do you get it to expose that option. The options I'm offered are:
1. Install along side existing OS(s)
2. Erase and use entire disk.
3. Something else (manual partitioning).

(One of the existing OS is U11.10.)


From personal experience on this, as I'm doing it right now.
On the Live CD, the option to upgrade directly to 12.04 LTS is offered only when you have internet access. Not sure why, but that's the way it is.

To be on the safe side, I backed up files and cloned my drive onto an external drive just in case I needed to do a clean install.

---

### Post by excobra on 2012-04-27
Ok everybody not sure about you guys but i have solved my problem.:guitar:

The real problem was update manager as i unchecked all the option of download from Internet in the software source and all other updates. Means i unchecked all the update sources.

Then i mounted the iso of alternate cd as mentioned in my first post and then i ran the command ```
gksu sh /media/cdrom/cdromupgrade

```and from there i clicked on install upgrade and everything worked smoothly.

Thanks anyway for your time.:lolflag:

---

### Post by jetpeach on 2012-05-01
thanks for the followup, i have the same problem so am going to test your solution.

followup: it seems to be working now, all i had to do when asked whether to use the internet was select "no" isntead of yes (i initially had chosen yes thinking to save time and pacakages that were newer on the internet than on the DVD image would be updated, but this apparently causes problems...)

---

