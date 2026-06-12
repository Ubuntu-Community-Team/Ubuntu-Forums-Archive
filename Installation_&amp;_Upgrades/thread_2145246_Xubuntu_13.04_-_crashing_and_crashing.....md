---
title: "Xubuntu 13.04 - crashing and crashing...."
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by Alan.Brown on 2013-05-14
Since upgrading from 12.10 to 13.04 I have had nothing but trouble.  Xubuntu has worked excellently for me for the last 4 years.   But after the last upgrade to 13.04 my system has become very unstable.   It keeps dropping out of my session and returning to the session login window.   This happens so often that I cannot determine what I am doing that causes it.   One thing I cannot do is to save the current session.  Common  causes of crashing have included **apport-gtk**, **xfce4-session** and **skype** and chrash reports have been submitted - several times a day.

I have tried many Linux distros and all of the *ubuntus and settled on Xubuntu as the best for my needs.   Now I am seriously considering dumping it and going to Mint or even Puppy just to get some stability.

I hoped that after a couple of weeks after the upgrade was issued there would be fixes to make the system more reliable but that has not happened.

I will give Xubuntu 13.04 another week then I will move on.

Any suggestions from anyone??

TIA

Alan

---

### Post by mörgæs on 2013-05-15
How does 13.04 work in a live boot?

---

### Post by Alan.Brown on 2013-05-15
I have not tried a live 13.04 disk.  I upgraded from 12.10.   I installed Xubuntu 10.04 ages ago and have always upgraded every six months since then - never had any trouble before.

I tried Kubuntu 13.04 live DVD today and cannot read the screen because there is no video driver for **NVIDIA GeForce G210** during installation.   I suspect the same will apply if I try **Xubuntu 13.04** live disk.

---

### Post by mörgæs on 2013-05-15
I don't think it's worth the effort to troubleshoot a system which has been upgraded so often. I would erase it right away and do a fresh install using only open-source drivers. They are almost guaranteed to work but might be slow.

When that has worked well for some time you can try adding closed-source drivers (if you really need them).

---

### Post by sharky6000 on 2013-05-15
Hi Alan, I am having the same problem. 

I can't be sure yet but it seems to only be happening to me when: 

a) I have Thunderbird open
b) I have Firefox open
c) I try to open Firefox or Thunderbird
d) I try to run soffice 

I was able to prevent the crashes for about an hour while only having gnome-terminal and gvim open. When I do the "show details", it's always a different process, so I can't pin it down.

I have only upgraded this system once (to 13.04) from a fresh 12.04 installation, and don't have much special/custom software. 

I do have a flash plugin installed in my browser as well IcedTea java plugin. These have caused problems in the past so I'm wondering if it's those. Now I'm running Chrome and so far so good (no crash for about 20 minutes). 

I have not tried any of morgaes' suggestions yet. I'll collect more data and keep updating.

---

### Post by Alan.Brown on 2013-05-15
[**[COLOR=#C61919][B]@mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") 	 
I think your idea is very good and probably just what I need to do.   My system has probably gathered a lot of cruft over the years and some of this may be causing the problems.  I will try the reinstallation in a couple of days.

@[**[COLOR=#000000]sharky6000[/COLOR]**]("http://ubuntuforums.org/member.php?u=94420")
I run both Firefox and Thunderbird and have not had any trouble when opening, closing or using them.  The dropping out of the session does not seem to be linked to any action in particular.

Thanks to you both for your replies.

Alan

---

### Post by slickymaster on 2013-05-15
Alan.Brown, please take a look at this bug and see if your situation falls under the same category:

[Bug #1104435 - xfce4-session crashed with SIGSEGV in g_slice_alloc()]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435")

---

### Post by sharky6000 on 2013-05-15
> **Alan.Brown said:**
> 
I run both Firefox and Thunderbird and have not had any trouble when opening, closing or using them.  The dropping out of the session does not seem to be linked to any action in particular.


Alan, let me be more clear.

My sessions are crashing. Sometimes the sessions is reset seemingly completely at random. Sometimes it's triggered by something. In all cases, I had either Firefox or Thunderbird or OpenOffice open. 

I have been running with only Google Chrome and gnome-terminal open for the past ~ 2 hours and my session has not crashed yet. Earlier, the crashes were quite frequent: at least one every 30 minutes. 

Can you try the same?

Funny thing: I thought it'd be related to my plugins, but Chrome also uses the flash and IcedTea plugins.

---

### Post by sharky6000 on 2013-05-15
> **slickymaster said:**
> Alan.Brown, please take a look at this bug and see if your situation falls under the same category:

[Bug #1104435 - xfce4-session crashed with SIGSEGV in g_slice_alloc()]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435")

Ah seems like this is applicable, so I'll try it as well, but can only report results in several hours.

---

### Post by sharky6000 on 2013-05-15
> **slickymaster said:**
> Alan.Brown, please take a look at this bug and see if your situation falls under the same category:

[Bug #1104435 - xfce4-session crashed with SIGSEGV in g_slice_alloc()]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435")

I have updated xfce4-session from the PPA as suggested by Moritz's comment (#19) from the bug page linked above and it seems to have fixed the problem for me (at least it hasn't crashed in the past 30 minutes with Firefox and Thunderbird open).

Thanks for pointing us to it slickymaster!

I'll provide feedback on launchpad as requested by Moritz but will wait a few hours to be sure.

---

### Post by Alan.Brown on 2013-05-15
@[**[COLOR=#000000]slickymaster[/COLOR]**]("http://ubuntuforums.org/member.php?u=1753126")
Yes - my experiences are the same as in the Bug Description in the link you gave.   Most of the other information is the same also.

@[**[COLOR=#000000]sharky6000[/COLOR]**]("http://ubuntuforums.org/member.php?u=94420")
Yes - I have always had Firefox and Thunderbird open at the same time as the crashes occur as far as I know.  I dont use Open Office.   I will try Google Chrome for a while and see what happens - but I have several Add Ons on Chrome which may cloud the issue.

Following the suggestion from [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")above, I think I will reinstall Xubuntu 13.04 from a fresh copy soon.   There must be a lot of cruft in my system now which could be causing problems.   My last fresh install would have been 2 or 3 years ago.

Again - thanks for the replies and suggestions

Alan

---

### Post by sharky6000 on 2013-05-15
> **Alan.Brown said:**
> 
Following the suggestion from [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")above, I think I will reinstall Xubuntu 13.04 from a fresh copy soon.   There must be a lot of cruft in my system now which could be causing problems.   My last fresh install would have been 2 or 3 years ago.


Alan, 

You may not have to reinstall. There's a bug in xfce4-session, and you can install a patched version which fixed it for me. I've been using Firefox and Thunderbird for several hours now without any problem. 

See the link posted by slickymaster.

---

### Post by Alan.Brown on 2013-05-17
1
On my old installation I installed the fix as mentioned above [Moritz #19] and have had no more crashes even when both Firefox and Thunderbird are open.  This seems to be working OK now - for several hours.

2
I installed a freshly downloaded copy of **Xubuntu 13.04** and installed it on a new partition and updated it.  I have been using it for a day now with no crashes.   Also using Firefox and Thunderbird OK.

Problems seem to have been fixed now - for me at least

Thanks for all the suggestions and help

Alan

---

### Post by Bucky Ball on 2013-05-17
Simple solution: Go back to 12.10 or stick to the LTS release 12.04 LTS. Was there a specific reason you upgraded when Xubuntu 12.10 was perfect for your needs? My rule of thumb: If it ain't broke don't fix it. Set up a stable partition and install 13.04 on a spare one to play with. That's what I do with interim releases, sticking with the LTS as my main squeeze. I need my computers to be rock solid.

---

### Post by Alan.Brown on 2013-05-17
I usually upgrade when they become available on the understanding that there will be bug and security fixes and further developments.   This is the first time I have had problems with an upgrade in at least two years.  I would be interested to know whether these problems are confined to Xubuntu or whether there are similar problems in other *ubuntus.   
I now have a fresh version of Xubuntu 13.04 in a new partition as you suggest. I also have a new version of Kubuntu to test.  I too need my computers to be rock solid.  Usually I upgrade on only two computers and leave the third upgrade until I am satisfied with the other two so I always have at least one functioning machine.

Thanks for your suggestions

---

### Post by hans12345 on 2013-08-19
> **slickymaster said:**
> Alan.Brown, please take a look at this bug and see if your situation falls under the same category:

[Bug #1104435 - xfce4-session crashed with SIGSEGV in g_slice_alloc()]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435")

Great! I also tried Moritz's suggestion (post 19) and it seems to have worked.

For the record, I had Firefox, Doc viewer and gpodder running. My 3 recent crashes were:
- twice when I opened gedit
- once when I tried to reboot

Thanks

---

