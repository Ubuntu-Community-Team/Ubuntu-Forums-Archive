---
title: "Latest update has a bug in keyboard configuration."
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by ubix on 2011-12-20
In the new release 11.10 (perhaps even in 11.04, which due to the maturity problems and numerous bugs I skipped) there is a branch of special directories and files missing! It used to be there in previous releases, (the latest I use and where it works is in 10.10). The branch of special directories and files under **/sys/module/**, called **hid_apple/parameters** and the function key parameter file **fnmode** disappeared when I Installed new Unity based release 11.10.  Due to the reasons beyond your interest here,  _changing a keyboard is not an option_!!!! 


Despite the objection of a moderator who, suggested that this issue earlier was not posted in the correct forum, I insist this is the Installation Upgrade issue! Even worse, the upgrade introduced a  ***»_bug_«***.

_***Moderators***_, would you be so kind and propagate this issue further up the chain of command, or at least tell us where should we report serious bugs introduced by new releases. True that for a regular mouse pusher this is not a problem, but I already burned myself by upgrading to 11.04, and reverting back due to problems there, hoping that 11.10 would address most annoying ones. I am starting to wander whether Ubuntu is interested to keep their customers happy?  It is utterly unacceptable, that a problem like this gets brushed under the rug by some inexperienced and incompetent administrator. :confused:

---

### Post by ubix on 2011-12-20
In another thread, ***scognito*** claims he does not have the same problem on ***11.10 Oneric***. There may be few reasons we do not see the same behaviour. Following may highlight the hidden issues: 

> **"ubix"][QUOTE=scognito said:**
> I told you, I'm using 11.10 :)
It is 64 bit version btw.Sorry, I missed your mention of ***Oneric***, _because you didn't explain how you installed it_? You most likely have upgraded from an earlier release where special files where created and kept over in the upgrade. Just as well, I have told you that already too! And FYI, I too have installed 64bit version of Oneric on my Mac Server, however mine is a new installation, and not an upgrade.

The new installation for some reason did not create special files! And you can not create them with a **sodo** or even if you create **root** account. Clearly you or I are missing something here. Your commands you have posted in your 1st post here should fail if the pertinent ***/sys/module*** infrastructure doesn't get installed or is missing just like the ones run from ***/etc/rc.local***.

Though unlikely, there may be yet one more possibility we both are not considering. Namely, I also have installed Ubuntu 11.10 on Mac mini Server in ***Virtual box***. Perhaps for some reason in VB this problem develops. But I will only know this for sure after I install ***11.10*** in true (not virtual) box. But that may not be so soon, due to still many unresolved issues. I do not want to loose the most stable Ubuntu platform yet to the flaky Unity based "serwups".:(
[/quote]


The point is that on 11.10 (Oneric) I can no longer use the following command in **/etc/rc.local** 
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```

to make my Ubuntu recognize Apple keyboard. Namely, the special directories **hid_apple/parameters** and the function key parameter file **fnmode** are now (in ***11.10***)  missing in **/sys/module/** hierarchy, and indeed, can not be created because these are special files!

---

### Post by ubix on 2011-12-21
Update from another thread is in order:

> **ubix][QUOTE=Apewall said:**
> i do have a /sys/module/hid_apple which fnmode will temporarily work, however it will reset itself, all 3 of the suggested "permanent" methods to set fnmode do not work for me.

Tested on a fresh install of 11.10 ubuntu and 11.10 Xubuntu, Macbook Pro 4,1.

So basically, the files are there for me but do not work as they should.**fnmode** _definitely should not reset itself_! Do you have the following line in **/etc/** 
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```NOTE: there must be _**exit 0**_ at the end of rc.local file!  However, I am even more surprised, the special files are there for you, perhaps this really is a VirtualBox issue, though I am not willing to risk to upgrade on the true hardware box (I mean outside VB) yet until a more trustworthy evidence comes around. All the answers here are too contradictory to be taken seriously, unless Ubuntu updates fixed this problem in the past, but why would files not exist on my out of the box and otherwise perfect installation, which also had been installed with updates option checked, as well as I had made the updates a few times since then. The fact is that Ubuntu since introduction of Unity has become a very problematic proposition. We can only hope that things will get better, after all we try to be helpful too and contribute to this process. [/quote]

---

### Post by ubix on 2011-12-28
> **Apewall said:**
> This is my rc.local file
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
exit 0

```
Output after 10 hours of uptime for fnmode
```

~$ cat /sys/module/hid_apple/parameters/fnmode
~$ 1

```

fnmode resets itself to 1.

As promised, I have done some research on this matter, and it is time to report back. In fact instead, I will refer you to the document I wrote about this. See: [Trouble With Apple Keyboard On Ubuntu](https://help.ubuntu.com/community/TroubleWithAppleKbdOnUbuntu). 

The problem is much more complex than originally anticipated, because it is rather inconsistent. As is seen by the interest and responses here, not many even know about this problems. This is the reason I decided to write forementioned document and adorn it with a few pictures, to underscore that this is not merely an Apple Ubuntu issue, but it pertains to all who use Apple keyboards, and even more so for those who run Ubuntu as a VM on Macs. I am adding the two pictures that reveal this point also here. Hopefully they will convey this very point about the problem not being only Apple Ubuntu, but rather a general Ubuntu installation and configuration problem.

[img]https://help.ubuntu.com/community/TroubleWithAppleKbdOnUbuntu?action=AttachFile&do=get&target=macmini-w-vBox-s200.png[/img] - - [img]https://help.ubuntu.com/community/TroubleWithAppleKbdOnUbuntu?action=AttachFile&do=get&target=my-amd-n-AppleKBD-w-vBox-s200c-h.png[/img]

---

