---
title: "Worst release so far for me.."
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-04-22
Ok, I tought it might be ok to install today since it will be released tomorrow and all alphas and betas I've tried were fine.

Installation went smooth as always. Then I rebooted and found out I could not click my gnomepanels. I logged out and back in again. That fixed the problem but gave me a new one. Gnome-settings-daemon failed to start and I had no soundcontrol or theme.

I was going to ask for some help in #ubuntu+1 when pidgin kept segfaulting for me. I downloaded another IRC-client and when I was just seconds from logging in I got the infamous hard freeze and had to reboot. This hard freeze have since I installed appeared 5 times. Judging from the forums I am not the only one with that freezeproblem :( 

I keep my fingers crossed that I will be able to download the Intrepid-ISO before another hard freeze forces me to reboot :)

---

### Post by eldragon on 2009-04-22
> **olskar said:**
> Ok, I tought it might be ok to install today since it will be released tomorrow and all alphas and betas I've tried were fine.

Installation went smooth as always. Then I rebooted and found out I could not click my gnomepanels. I logged out and back in again. That fixed the problem but gave me a new one. Gnome-settings-daemon failed to start and I had no soundcontrol or theme.

I was going to ask for some help in #ubuntu+1 when pidgin kept segfaulting for me. I downloaded another IRC-client and when I was just seconds from logging in I got the infamous hard freeze and had to reboot. This hard freeze have since I installed appeared 5 times. Judging from the forums I am not the only one with that freezeproblem :( 

I keep my fingers crossed that I will be able to download the Intrepid-ISO before another hard freeze forces me to reboot :)

if you are having hard freezes (probable due to xorg or display drivers) id suggest you take note of the download link and use wget through a terminal. ;)

---

### Post by olskar on 2009-04-22
> **eldragon said:**
> if you are having hard freezes (probable due to xorg or display drivers) id suggest you take note of the download link and use wget through a terminal. ;)

Haha, firefox segfaulted and aborted my download just when I had read your answer :) wget it is

---

### Post by philinux on 2009-04-22
Shame about that for you been really fine here.
Must be hardware related. Hope you file a bug report.

---

### Post by canesalato on 2009-04-22
mmm...all these problems make me suspect about a bad iso? Did you check md5sum? Maybe you could try downloading that again...

---

### Post by olskar on 2009-04-22
> **philinux said:**
> Shame about that for you been really fine here.
Must be hardware related. Hope you file a bug report.

Yes, the funny thing is that it used to be more stable in alpha than one day from final :(

I guess I am suffering from the same freezebug as some of those people. I get the same freeze in three different computers running Jaunty.

[http://ubuntuforums.org/showthread.php?t=1128583](http://ubuntuforums.org/showthread.php?t=1128583)
[http://ubuntuforums.org/showthread.php?t=1127591](http://ubuntuforums.org/showthread.php?t=1127591)
[http://ubuntuforums.org/showthread.php?t=1129414](http://ubuntuforums.org/showthread.php?t=1129414)
[http://ubuntuforums.org/showthread.php?t=1129729](http://ubuntuforums.org/showthread.php?t=1129729)

---

### Post by megamania on 2009-04-22
> **olskar said:**
> Ok, I tought it might be ok to install today since it will be released tomorrow and all alphas and betas I've tried were fine.
By installing the Beta today, you installed the beta that was released weeks ago. 
I've seen several hundred updates since I installed the Beta version the day it was released.

My suggestion is to wait one or two days and download the final release. At that stage, if you still have problems, it will be easier to help you.

---

### Post by olskar on 2009-04-22
> **megamania said:**
> By installing the Beta today, you installed the beta that was released weeks ago. 
I've seen several hundred updates since I installed the Beta version the day it was released.

My suggestion is to wait one or two days and download the final release. At that stage, if you still have problems, it will be easier to help you.

Ah sorry, I forgot to write that it was a daily build I installed, I think it was one or two days old

---

### Post by xebian on 2009-04-22
> **olskar said:**
> Ah sorry, I forgot to write that it was a daily build I installed, I think it was one or two days old

So why would you call it the [COLOR="DarkRed"]worst release[/COLOR] then instead of the [COLOR="Red"]worst daily build[/COLOR]?:confused:

---

### Post by olskar on 2009-04-22
> **xebian said:**
> So why would you call it the [COLOR="DarkRed"]worst release[/COLOR] then instead of the [COLOR="Red"]worst daily build[/COLOR]?:confused:

Touché ;) However I do not think the freezebug(s) will be fixed for tomorrow :(

---

### Post by Technoviking on 2009-04-22
I would suggest trying a fresh install of the Ubuntu 9.04 final, and definitely report bugs.

---

### Post by rajeev1204 on 2009-04-22
Maybe olskar got a bit carried away when giving the title ,but jaunty has three things i hate

1.Disappearance of the old notify icon
2,Disable ctl alt backspace
3.Fast user switch applet ( it doesnt have any icons)

---

### Post by VMC on 2009-04-22
> **eldragon said:**
> if you are having hard freezes (probable due to xorg or display drivers) id suggest you take note of the download link and use wget through a terminal. ;)
I think this might be the issue. I didn't use any previous beta releases and somewhere along the line with RC I got freeze. When I rolled back my Intel driver to v2.4 everything work. 

What graphic chip do you have?

---

### Post by KrazyPenguin on 2009-04-22
Best release for me so far , no freezes on my laptop!!!
(i use to have to edit the grub file nolapic noapic)
+1

---

### Post by crjackson on 2009-04-22
> **rajeev1204 said:**
> Maybe olskar got a bit carried away when giving the title ,but jaunty has three things i hate

1.Disappearance of the old notify icon
2,Disable ctl alt backspace
3.Fast user switch applet ( it doesnt have any icons)

1. You can restore that. Do a search, I saw the procedure a couple of days ago.

2. You can restore that too, check release notes

3. Intrepid was the same way. I put them back using a 3rd party repo. I'll try to locate that for you this weekend. Since the thread will be closed by the I'll send you PM if you don't mind.

It's too soon to tell if it will be the worst, best, or average. Up to now, Hardy was the best, Intrepid 50/50, Jaunty - Not released yet, but testing version has been great except for crappy video support.

---

### Post by go7Ul1ai on 2009-04-22
> **crjackson said:**
> 1. You can restore that. Do a search, I saw the procedure a couple of days ago.

2. You can restore that too, check release notes

3. Intrepid was the same way. I put them back using a 3rd party repo. I'll try to locate that for you this weekend. Since the thread will be closed by the I'll send you PM if you don't mind.

It's too soon to tell if it will be the worst, best, or average. Up to now, Hardy was the best, Intrepid 50/50, Jaunty - Not released yet, but testing version has been great except for crappy video support.

Unfortunately the guy doesn't like "quick and dirty" fixes ^_^

---

### Post by ktp on 2009-04-22
> **lee.jarratt said:**
> Unfortunately the guy doesn't like "quick and dirty" fixes ^_^

You also have to consider that changing options mean it is not supported.

---

### Post by olskar on 2009-04-23
> **VMC said:**
> I think this might be the issue. I didn't use any previous beta releases and somewhere along the line with RC I got freeze. When I rolled back my Intel driver to v2.4 everything work. 

What graphic chip do you have?

It's Nvidia. 

People with all kind of graphiccards have experienced freezes and all of us can make a freeze happen with the command strace gedit

---

### Post by rajeev1204 on 2009-04-23
> **lee.jarratt said:**
> Unfortunately the guy doesn't like "quick and dirty" fixes ^_^


No comments.:D

---

