---
title: "[SOLVED] no &amp;amp;amp;quot;option to upgrade&amp;amp;amp;quot; dialogue in 8.04 on inserting 8.1 c"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by necronwarrior on 2008-11-04
I've just tried to upgrade my ubuntu 8.04 to 8.01 using the alternate cd.
I downloaded the cd image and mounted in using the command given on the ubuntu upgradation site but nothing happened.

"sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0"

I also wrote the image to a cd,inserted it.Still no dialogue asking me to upgrade.
I've also tried using the alternate command after pressing alt+f2

"gksu "sh /cdrom/cdromupgrade""

It opens a "starting administrative task" window in the bottom desktop panel.then it goes upto asking my password and when I enter it the comp returns to normal as if nothing had happened.
I'v tested the cd for defects by booting from it and also run a live session from it.
Please help.

---

### Post by crazyness003 on 2008-11-04
Do you not have internet connectivity? if you do there's a WAY easier way to do this

Check out his page: [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

but I think you've already seen this page, so my help is useless. Sorry, cant help you much.

---

### Post by ad_267 on 2008-11-04
Have you gone to System - Software Sources - Updates and selected "Normal releases" under Show new distribution releases?

---

### Post by Partyboi2 on 2008-11-04
> It opens a "starting administrative task" window in the bottom desktop panel.then it goes upto asking my password and when I enter it the comp returns to normal as if nothing had happened.
I'v tested the cd for defects by booting from it and also run a live session from it.
Please help.
The alternate cd does not run as a live session. Are you sure you downloaded the alternate cd not the live cd?

---

### Post by necronwarrior on 2008-11-04
well i guess you are right.I downloaded the live cd .
thanks.

---

### Post by crazyness003 on 2008-11-04
> **Partyboi2 said:**
> The alternate cd does not run as a live session. Are you sure you downloaded the alternate cd not the live cd?

There's a reason why you're "Iced Blended Vanilla Crème Ubuntu"

---

### Post by necronwarrior on 2008-11-05
Well i downloaded the alternate cd and still no avail..........
still no dialogue is displayed.I've tried everything listed on the ubuntu site.
the cd ran fine on my friends laptop.he sucessfully upgraded to 8.1 from it.

---

### Post by crazyness003 on 2008-11-06
Okay, a number of things could have gone wrong. First off, were you sure you're running the i386 (32bit) version and not amd64 (64bit)? and did you download the correct cd version for your distro architecture.

Type "uname -a" in terminal, it should tell you the architecture and some extra stuff too. If it says x86_64 anywhere you have amd64 installed. Otherwise, you should have the x86 (aka i386).

Other than that, it may be possible your cd drive is not being mapped correctly or could even be out of commission(broken). But these are just possibilities. The more info you give us the better.

Thats all i can think of right now, sorry if this gets you nowhere, but at leased we're trying.

---

### Post by necronwarrior on 2008-11-07
Yes i'm sure that its the right version(i386).I have a lenovo R61 laptop with a intel centrino processor.

uname -a returns the following line in terminal:

Linux Tejas 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

I'm also sure that the cd and the cd rom drive is perfect(I can run the live cd ).

Some other problems i've been facing are:

1.My system has become quite slow.It takes about a minute to open terminal!

2.Whenever I try to open any application which requests the password(eg. i try to open the synaptic package manager),It gives a "Starting Administrative Application" window in the lower panel (but no window is shown on the screen).after that nothing happens.

3.Also at the same time, I became unable to install or uninstall anything. I can start the add/remove applications window, tell it to reload the list of available applications, and it just sits there spinning its wheels forever.

4.When press ctrl+alt+backsp and re login it takes about 3 min to load the panels.But the desktop icons are displayed normally and i can open them.

---

### Post by crazyness003 on 2008-11-07
Wow! Id definitely report this on [Ubuntu's Launchpad]("https://launchpad.net/ubuntu"). These seem like major bugs that may be linked to the entire apt system or gksu (since you never get to input your password.)

My [unfortunate] recommendation is a clean install of 8.10 (or 8.04, but definitely get a fresh copy on there). Again, if you file the bugs first, someone may be able to help you.

If you dont know how to file a bug with launchpad, go here:
[https://launchpad.net/ubuntu/+filebug/+login](https://launchpad.net/ubuntu/+filebug/+login)

Or if you just want to ask a question:
[https://launchpad.net/ubuntu/+addquestion/+login](https://launchpad.net/ubuntu/+addquestion/+login)

You will need to register (of course free and easy...and recommended). There you will probably get help from the devs and coders...hence more insightful advice, and maybe even tell them that they did something wrong.

---

