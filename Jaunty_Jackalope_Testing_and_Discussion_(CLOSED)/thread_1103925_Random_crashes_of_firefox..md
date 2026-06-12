---
title: "Random crashes of firefox."
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Taiebot65 on 2009-03-23
It s not the first time that it s happening firefox just crash with no action so i would like to report a bug. How can i debug that kind of error.

---

### Post by dBuster on 2009-03-23
I had random crashes of Firefox as well when I was trying to get the 64bit java working on my old Hardy laptop.  It had something to do with the icedtea, 64bit plugin and some other java choking on each other and dumping firefox.  

If your looking to report a crash isn't the crash report coming up when you go to start it or after it closes?

You could start Firefox from terminal and see if there is any verbose as to what may have happened when it crashed.  That might be a start.

---

### Post by UntidyUser on 2009-03-23
This also happens to me when I try to access internetbanking account and other java applets. It is however not them all, it appears to be mainly ones that are used for secure things. 

So I can e.g. google 'do i have java', and the answer is a positive one, and does in no way mess up my browser.

Its annoying and means I havent completely switched to ubuntu.

---

### Post by Nullack on 2009-03-23
icedtea doesnt work for me, Ive bugged it. As a workaround use suns binaries they work.

---

### Post by Taiebot65 on 2009-03-23
I ve unfortunately deleted the log when i was cliking on tab but i think yes it was related to java.

---

### Post by dBuster on 2009-03-23
I am running a 64 bit Ubuntu and only have just the SUN Java plugin.  I used the following [SCRIPT]("http://home.comcast.net/~ubuntume/Get64bitJava-0.1.2.tar.gz") with a slight modification for the current release of the script.  

The script goes through and will remove any icedtea or other plugins I believe and then install the sun java plugin.  I have had no problems what so ever.  I then went and installed from the package manager the latest sun java as well still no java issues with firefox or any browser for that matter.

I would at least try the script and have allow it to remove any other java that may be causing the issues that is if your using a 64bit Ubuntu install....

---

### Post by Flarkis on 2009-03-23
I will point out that the new nvidia drivers, 180.x and higher, caused firefox to crash on my computer.

---

### Post by dBuster on 2009-03-23
> **Flarkis said:**
> I will point out that the new nvidia drivers, 180.x and higher, caused firefox to crash on my computer.

Okay have you tried any further trouble shooting before you came to that conclusion?  

There has to be something else not just the nvidia drivers.  I am running 180.37 without any issues what so ever. 

Once again there is probably something else that is causing the conflict with your nvidia drivers and choking your system.  

How many different flash versions along with java are installed on your computer?  Do you have the nonfree flash plugin?

If you check out some bug reports they are all mentioning the flashplugin-nonfree and nvidia.  Since I do not run the nonfree, just the 64 bit flash plugin I have no issues with my nvidia card/drivers.  

[ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=726968")
[bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/218483")
[www.avsforum.com]("http://www.avsforum.com/avs-vb/showthread.php?p=15408576#post15408576")

Just something to think about and trouble shoot.  I do not think it is solely your nvidia drivers.

---

### Post by Taiebot65 on 2009-03-23
I'm on intel ... and i ve noticed it i do not know why it crashes because it was not doing anything....Is there a way to find the log that i ve deleted.

---

### Post by Bakon Jarser on 2009-03-23
I'm running the invidia 180.x driver with flash 10 from the repos and haven't had a single crash.

---

### Post by Bakon Jarser on 2009-03-23
> **Taiebot65 said:**
> I'm on intel ... and i ve noticed it i do not know why it crashes because it was not doing anything....Is there a way to find the log that i ve deleted.

Taiebot, this combined with your other thread about programs taking forever to close makes me think this might not be a firefox issue.

---

