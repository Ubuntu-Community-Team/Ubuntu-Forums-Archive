---
title: "DVD upgrade? user friendly phone upgrade?"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2008-06-21
[SIZE=2][FONT=Franklin Gothic Medium]I have a 57K phone modem. I tried several times to upgrade from 7.10 to 8.04, which would take about a week if all goes well. The KPPP daemon would always die after a few days.

My question is not about my KPPP daemon. I would like to know why the upgrade installer insists on aborting when the phone connection flakes out. This is somewhat disconcerting to see after downloading for five straight days. Would it be so difficult to provide the user with the option to resume after fixing the phone connection? What is so time sensitive that it cannot wait?

I ordered Kubuntu 8.04 on DVD. Could someone please point me to a web page which explains how to perform the upgrade with this DVD? My notion is to first add the DVD to the repository, and then see if the upgrade installer will recognize this as a way to upgrade.

Thanks for your time.
[/FONT][/SIZE]

---

### Post by logos34 on 2008-06-21
> **David J Bush said:**
> [SIZE=2][FONT=Franklin Gothic Medium]
I ordered Kubuntu 8.04 on DVD. Could someone please point me to a web page which explains how to perform the upgrade with this DVD? My notion is to first add the DVD to the repository, and then see if the upgrade installer will recognize this as a way to upgrade.

Basically you just insert the dvd and follow the prompts:
[https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

---

### Post by David J Bush on 2008-06-26
> **logos34 said:**
> Basically you just insert the dvd and follow the prompts:
[https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)


I got the dvd today, and following the instructions on the above link, I got as far as the command

kdesu "/cdrom/cdromupgrade"

The file structure of the dvd does not contain any file cdromupgrade. Attached is the recursive directory structure of my 8.04 dvd. It is the output of the command ls -aRl, compressed in bz2 format.

How should I upgrade with this dvd? Thank you.

---

### Post by David J Bush on 2008-06-27
bump

> **David J Bush said:**
> I got the dvd today, and following the instructions on the above link, I got as far as the command

kdesu "/cdrom/cdromupgrade"

The file structure of the dvd does not contain any file cdromupgrade. Attached is the recursive directory structure of my 8.04 dvd. It is the output of the command ls -aRl, compressed in bz2 format.

How should I upgrade with this dvd? Thank you.

---

### Post by Pumalite on 2008-06-27
You need the Alternate CD/DVD.

---

### Post by David J Bush on 2008-07-03
Where do I get this Alternate DVD? All I want is to upgrade my Kubuntu 7.10 to 8.04. I buy a DVD and now I'm told it's the wrong DVD. The store I bought it from does not list any "alternate" DVD for purchase. Neither does Canonical, nor Amazon, nor any other vendor I can find.

Is this some sort of bizarre rite of passage? Is this a puzzle I'm expected to figure out? **Where can I buy what I need to upgrade my machine? **I have dialup. Downloading is impractical. Thanks for any help you can provide.

---

### Post by MWt on 2008-07-04
As far as I know there is no "Alternate" DVD. But it is very strange that you don't have 'cdromupgrade' file in the main dir of your DVD...
It is listed as one of files included on Kubuntu 8.04 DVD -- see e.g. [kubuntu-8.04-dvd-i386.list]("http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/8.04/release/kubuntu-8.04-dvd-i386.list")

I'm sorry, I don't really have a good advice for you, but maybe it is possible to ask some vendor to check if they have the 'cdromupgrade' file on their DVD before sending it to you? Or make sure that the DVD is exactly the same as available from Kubuntu.org download section?

P.S.
I have just downloaded this DVD and it contains 'cdromupgrade' file.
Anyway I'm going to test it next week. If it works, and all other possibilities fail for you, I can burn this DVD for you and send it by post. Send me a private message if you would like it.

---

### Post by David J Bush on 2008-07-10
[SIZE=3][FONT=Century Gothic]I appreciate your offer of help. I was able to upgrade over the Net after all, using a phone modem. The PPP daemon died about a dozen times. Each time I restarted the process took up about 40 minutes of initial stuff (something to do with setting channels) before it finally resumed downloading the files, picking up the count at close to where it left off.

The company I bought the DVD from is on-disk.com. BEWARE they do not include the upgrade file! The disk is still useful to me, and I probably would have had to download a lot of files anyway, since I have a lot of stuff installed, but this is one of those things that should be mentioned in the online documentation. Not all DVDs will work with the listed procedure.

Ubuntu online docs should also mention that when a popup window says "the upgrade aborts now," that does not mean that all the files downloaded in the process are lost. It's simple stuff like this that makes a big difference in the experience for newbies.

Thanks for your time and help!
[/FONT][/SIZE]
> **MWt said:**
> As far as I know there is no "Alternate" DVD. But it is very strange that you don't have 'cdromupgrade' file in the main dir of your DVD...
It is listed as one of files included on Kubuntu 8.04 DVD -- see e.g. [kubuntu-8.04-dvd-i386.list]("http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/kubuntu/releases/8.04/release/kubuntu-8.04-dvd-i386.list")

I'm sorry, I don't really have a good advice for you, but maybe it is possible to ask some vendor to check if they have the 'cdromupgrade' file on their DVD before sending it to you? Or make sure that the DVD is exactly the same as available from Kubuntu.org download section?

P.S.
I have just downloaded this DVD and it contains 'cdromupgrade' file.
Anyway I'm going to test it next week. If it works, and all other possibilities fail for you, I can burn this DVD for you and send it by post. Send me a private message if you would like it.

---

