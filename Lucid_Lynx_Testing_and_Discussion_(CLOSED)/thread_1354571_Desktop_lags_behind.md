---
title: "Desktop lags behind"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by YosefKaro on 2009-12-14
I've did some searching around and haven't found a solution to my problem.  Whenever I start up, I get the default ubuntu desktop  wallpaper and then it takes a couple of minutes before my desktop wallpaper appears.  After that, it takes another minute or two before my icons appear.  Is there a CLI command that I can execute to make my desktop appear?  Or better yet, is there a known solution to this problem?

-Yos

---

### Post by mikewhatever on 2009-12-14
Is that a known problem to have a known solution? Can you post your computer specs, CPU, RAM, graphics.

---

### Post by YosefKaro on 2009-12-14
Some specs:

AMD TurionTM 64 X2 Dual-Core
Memory: 2048MB
Graphics: ATI Technologies Inc RS690M [Radeon X1200 Series]

Hope this helps.

-Yos

---

### Post by mikewhatever on 2009-12-14
OK, these specs shouldn't cause problems. How about the output of <sudo fdisk -l>? Does the disk indicator how a lot of activity while your settings load?

---

### Post by YosefKaro on 2009-12-14
This is the output of sudo fdisk -l [http://pastebin.ubuntu.com/341023/](http://pastebin.ubuntu.com/341023/)  As far as the disk indicator showing a lot of activity, I have never noticed.

-Yos

---

### Post by mikewhatever on 2009-12-14
So, you seem to have enough RAM and an ample partition to run Ubuntu, and with that out of the way, I am not quite sure what's wrong. Logs may reveal somethings useful. I am no expert with logs, but try logging your boot messages with bootlogd, and post the result.
[http://www.foogazi.com/2008/06/07/quickzi-how-to-log-boot-messages-in-ubuntu/](http://www.foogazi.com/2008/06/07/quickzi-how-to-log-boot-messages-in-ubuntu/)

---

### Post by YosefKaro on 2009-12-14
Well now it knows that it is being watched; oddly enough, this seems to have solved the problem: just by turning logging on.  Thank you.

-Yos

And for some odd reason, the logs are not being kept where they are supposed to be kept now.

---

### Post by mikewhatever on 2009-12-14
That's odd. Where are the logs kept? Also, I forgot to ask, are you running Karmic or another release?

---

### Post by YosefKaro on 2009-12-14
Well, the logs should be kept there.  The message that I get from the file /var/log/boot is (Nothing has been logged yet.)  I have no idea if these logs are being kept somewhere else now.  I am on Lucid.

-Yos

---

### Post by lavinog on 2009-12-14
you probibly shouldn't be using an alpha if you are posting in the beginners section.

Does it happen every time, is there hard drive activity, could a filesystem check be going on in the background?

It could be a bug, in which case you should file a bug report.

You should be posting this in the development and testing forum:
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by YosefKaro on 2009-12-14
I filed a bug report about an hour ago and it has already been confirmed.  No, no background fsck going on and the disk is not busy with activity during that time.  Thanks for your help.

-Yos

---

### Post by lavinog on 2009-12-14
did you setup any network shares recently?

---

### Post by YosefKaro on 2009-12-14
No, I haven't made any relative changes.  I'm running ubuntu on my laptop.

-Yos

---

### Post by VMC on 2009-12-14
> **YosefKaro said:**
> Some specs:

AMD TurionTM 64 X2 Dual-Core
Memory: 2048MB
Graphics: ATI Technologies Inc RS690M [Radeon X1200 Series]

Hope this helps.

-Yos
Are you using the 64-bit version software? I know there has been issues with using alpha amd64. Someone with with a amd needs to report if they have the same problem.

Using the LiveCD did you have any problems o only since you installed?

---

### Post by YosefKaro on 2009-12-14
Thank you for your response. :)  No, I am not using the 64-bit software...I stick to 32-bit.  And about this problem, I have only been experiencing it since my upgrade to lucid.  Not from the beginning, but just the last couple of days.  I don't know exactly when the problem started or what updates/upgrades immediately proceeded the problem...I wish I had that info.  :(

-Yos

---

### Post by VMC on 2009-12-14
> **YosefKaro said:**
> Thank you for your response. :)  No, I am not using the 64-bit software...I stick to 32-bit.  And about this problem, I have only been experiencing it since my upgrade to lucid.  Not from the beginning, but just the last couple of days.  I don't know exactly when the problem started or what updates/upgrades immediately proceeded the problem...I wish I had that info.  :(

-Yos

Do you use Update Manager and did you do the partial update?

Here's what I use with following 'gdm' being held back:

[COLOR="Gray"]sudo aptitude update && sudo aptitude safe-upgrade
[/COLOR]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages have been kept back:
  gdm 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by YosefKaro on 2009-12-14
I used update manager to do the partial upgrade.

-Yos

Using that command, I now see that there is another upgrade.  Nice.  Hopefully it will remedy a couple of problems that I am having.

---

