---
title: "Reboot PC from USB"
date: 2020-04-12
forum: Installation &amp; Upgrades
---

### Post by adsrvaim on 2020-04-12
**Currently Installed on Lenovo PC: Ubuntu 16.04**

[B]Question 1: I have a USB thumb drive and I would like to reboot from USB.  How can I reboot from USB? I don't have Ubuntu on that that USB thumb drive.
[/B]
[B]Question 2: My Lenovo ideapad P500 has brightness issue, sometimes it becomes very dark. Previously I had Windows 8 on this PC and I used to do following to fix the issue.  Now that I have Ubuntu installed on this PC. How                       

                  do I perform the following stops to fix this problem[/B]? 


[LIST=1]
[*]Click on D drive
[*]Click on DRIVER
[*]Click on VGA
[*]Intel
[*]64
[*]Keep clicking until you get to setup
[*]click Setup
[*]Now follow the screens.  It will ask you, do you really want to install old driver, say YES.
[*]Just keep clicking and it will download and install older driver from Intel website.
[*]Reboot

Thanks for your help.
[/LIST]

---

### Post by CelticWarrior on 2020-04-12
Welcome.

Unfortunately this is a bad start. Question 1 is nonsensical and question 2 just shows you don't understand much about computers and Windows. There's no point in describing with such granular detail that, in Windows, you repeatedly installed some driver (very likely you would had a much better chance of solving it once and for all by installing updated drivers directly from Intel instead of an old driver). 

Now, obviously you won't do the same in Ubuntu.
The question is do you have the same problem or is this just an hypothetical question? Can't you set the intended brightness level with the keyboard?

---

### Post by yancek on 2020-04-12
> **I have a USB thumb drive and I would like to reboot from USB.  How  can I reboot from USB? I don't have Ubuntu on that that USB thumb drive.** 

If you want to boot from the usb drive, you don't need Ubuntu on it but you do need some bootable Linux live OS or some bootable utility.  The steps you posted 1-10 will are steps which will work on windows only, there are no partition labels such as 'D' in Linux.  What exactly do you have on the usb and what is on the D drive and do you have some release of wndows installed.  Drivers for windows don't work on Linux if that is what you have.

---

### Post by adsrvaim on 2020-04-13
Mr. Warrior:

Thanks for kind reply and ZERO help. FYI, If I could fix the brightness issue with a button, do you think I would have gone through the trouble of creating this post ????

Lenovo has hardware issue that causes this brightness problems appear every few weeks, at that point brightness buttons don't work.  In the past, the only way I fixed that problem was following the steps that described, and I simply asked if there was anything similar in Ubuntu that could be done.

Have a good day, and don't reply.
[COLOR=#000000]
[/COLOR]

---

### Post by adsrvaim on 2020-04-13
Yancek,

Thanks for your help and kind reply. On USB I have Oracle Linux and I would like to install it and clear off Ubuntu. I have Ubuntu on another computer and it works perfectly on that one. 

I used to take those steps when Lenovo used to have Windows 8 OS, recently I installed Ubuntu on it. So I was trying to find out if there were any steps or method in Ubuntu to perform the same task.  Lenovo has hardware problem that causes brightness buttons to not work after every few weeks. In the past I followed the steps that described to fix that probelm.

Thanks and have a good day.

---

### Post by CelticWarrior on 2020-04-13
>  Have a good day, and don't reply.

Oh no, I will reply and it will be long, so buckle up.
As a scientist, it's my duty to combat cognitive bias and the Dunning-Kruger effect can be reversed.

Whether you like it or not, whether you understand it or not, often the harsh truth is a lot more helpful than sweet comments that look helpful, superficially, but in essence aren't and the typical end result is increased frustration.

As much as I would love to get people to use Linux instead of proprietary OSes that isn't always possible or advisable but the harsh truth is that some people simply don't know enough to change it on their own.

Sometimes I explain it with a cars analogy. It goes like this: If you own a car and a driver's license certainly you can drive. However, that doesn't mean every driver is qualified to maintain the car. More often than not a mechanic and even a mechanical engineer are needed and the vast majority of drivers are neither. Installing an OS, especially one *not *supported by the manufacturer requires a "mechanic" qualification and occasionally one needs to be a "mechanical engineer" when a certain hardware requires special care.

> I used to take those steps when Lenovo used to have Windows 8 OS,  recently I installed Ubuntu on it. So I was trying to find out if there  were any steps or method in Ubuntu to perform the same task.

Yes, your Lenovo Ideapad P500 has an hardware/firmware problem in the brightness regulation. It has been discussed in many places, namely at [https://forums.lenovo.com/t5/Lenovo-P-Y-and-Z-series/LENOVO-P500-BRIGHTNESS-ISSUE/td-p/948141](https://forums.lenovo.com/t5/Lenovo-P-Y-and-Z-series/LENOVO-P500-BRIGHTNESS-ISSUE/td-p/948141) , when running the original Windows 8 OS and apparently the problem is even worse when running the unsupported Windows 7 -> [https://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/P500-Brghtness/td-p/926265](https://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/P500-Brghtness/td-p/926265) . 

> this brightness problems appear every few weeks
This suggests Windows has installed a different driver, probably alongside other OS updates. So, **reinstalling the original graphics driver**, which is what you did but with ZERO understanding of the "why" and "how", solve it temporarily until the some update was automatically reinstalled. So, not really a solution.
**The actual solution, for Windows, was given here [https://forums.lenovo.com/t5/Lenovo-P-Y-and-Z-series-Notebooks/Can-t-adjust-brightness-in-Windows-8-1-for-IdeaPad-Z400/m-p/1284173?page=1#1341763](https://forums.lenovo.com/t5/Lenovo-P-Y-and-Z-series-Notebooks/Can-t-adjust-brightness-in-Windows-8-1-for-IdeaPad-Z400/m-p/1284173?page=1#1341763) , and not surprisingly it's the exact same I mentioned in post #2: > installing updated drivers directly from Intel instead of an old driver **Intel also provides **- **again, for Windows - an auto detection tool that downloads and installs up-to-date drivers for all Intel parts inside. The relevant one for this problem is the Intel HD graphics drivers only.

The above is obviously applicable only to Windows. **In all major Linux distros, Ubuntu included, up-to-date Intel drivers are automatically installed and updated whenever needed.** Therefore users don't have and shouldn't have to install any Intel drivers manually. And the drivers currently in use for Linux **shouldn't have the same brightness problem as in Windows around 2012**. [B]If you have the same problem in Ubuntu then I can't guarantee a solution but we have some very smart people here that can work with you to test a few solutions that, in any case and if not clear enough by now, will have nothing to do with reinstalling drivers the way you are used to do in Windows.

[/B]A likely solution is **additional kernel parameters**. Some laptops with Intel Graphics need one or more parameters added in order to make the brightness keys work.

Now, if you want help with Ubuntu you will do the smart thing which is to keep it and wait for expert suggestions.
**Ubuntu is very "beginner friendly", Oracle Linux is exactly NOT that. **

---

