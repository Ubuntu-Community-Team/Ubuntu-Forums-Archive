---
title: "first update after new install 7.10 - Problem"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2008-09-04
I have just done a new install of 7.10 from a desktop shipit cd (it went ok) and then immediately did the updates using adept from the 'updates ready' icon. There were 187 updates waiting.
However, partway through the process, an error occurs
'There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. [OK]'

(no it is not ok with me....)

This occurs when the progress bar indicates 62% and the declared information is
'preparing to configure new version of libqt3-mt...'

This is a replay of the same thing which happened yesterday, only at that time I was not exactly sure that my actions of installing firefox and also the proprietary nvidia driver might have been implicated. Apparently not so. Same problem again today.

I am just about to press 'OK' on the error message now, and wondering what will happen. This is all on this PC I am using for this mesage. I trust that I will be able to recover the situation with whatever knowledge I have.

Wish me luck?

---

### Post by Peter09 on 2008-09-04
Have you enough disk space free to accommodate the changes?

---

### Post by candtalan on 2008-09-04
After I accepted the error message by clicking OK, every thing appeared normal. I rebooted to be sure that I would be making a fresh start.

I then tried to run adept to check if any updates were still relevant. However, adept would not open. An error was shown that the 'Database is locked' with some other comments. This meant I could not find out if all updates were completed.

I used a terminal with
sudo dpkg --configure -a

and when asked, I chose to accept the package maintainers configuration, not the non standard one which was found.

This seems to have sorted the locked problem. I then ran adept and looked for updates (Fetch Updates) and there were none indicated.

So I conclude that whatever caused the original error, the dpkg command activity sorted it out.

Hope this helps others?

and also........
In case a question arises, I know that the current k/ubuntu is 8.04 and I am using it elsewhere. However, I want to use 7.10 in this case because a multimedia package krecord, a simple audio record app, is not included in the 8.04 repos. (not yet anyway). Krecord (not krec, which is a different app) has been particularly good at capturing the audio information in my machine.

---

### Post by candtalan on 2008-09-04
> **Peter09 said:**
> Have you enough disk space free to accommodate the changes?

thanks for your response.
Yes - loads of space - it is being installed into a 28GB partition. 

(fwiw the machine has two 300GB hard drives)

The odd thing is, that I now recall installing 7.10 kubuntu into a friends laptop and getting the same problem, many months ago, when 7.10 was still latest current version.

I do not really know if the same problem would happen if I followed the same install and update process starting with ubuntu.

---

### Post by Sef on 2008-09-04
> The odd thing is, that I now recall installing 7.10 kubuntu into a friends laptop and getting the same problem, many months ago, when 7.10 was still latest current version.

I do not really know if the same problem would happen if I followed the same install and update process starting with ubuntu.

I would suspect that the install disk is bad.   Check it before booting into the disk, there is an option to check the disk for errors.

---

### Post by candtalan on 2008-09-05
> **Sef said:**
> I would suspect that the install disk is bad.   Check it before booting into the disk, there is an option to check the disk for errors. Thanks

The install cd used is a Shipit actual CD. I have just now checked it in the install (problems) machine using the live cd  facility Check CD for defects, and it checks ok. I also checked it similarly in another machine, also gives OK.

I handle quite a few CDs, mostly ones I burn myself, because I have a regular display table at a local computer fair - handing out information and CDs. So the CD used on the earlier occasion for a friends laptop would not have been the same CD as this particular one. When I burn CDs they are also checked at the time. So I do not believe I have a CD problem.

I suggest it is a problem for people (everyone?) installing clean kubuntu 7.10 from desktop live CD at this time, - when the updates number around 187 in quantity.  The problem may not have existed early on in the release time following 7.10 and as time goes on, and some updates change, it is possible that the problem may disappear. Anyway, I do not suppose many people are installing 7.10 kubuntu at this time, but it may be important to people who are expecting a new install to go well and easily. If I am correct in my guesses.

---

