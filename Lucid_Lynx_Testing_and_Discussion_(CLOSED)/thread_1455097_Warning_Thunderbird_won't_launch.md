---
title: "Warning: Thunderbird won't launch"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by castrojo on 2010-04-15
[https://bugs.edge.launchpad.net/ubuntu/+source/thunderbird/+bug/563893](https://bugs.edge.launchpad.net/ubuntu/+source/thunderbird/+bug/563893)

Being worked on now and the platform team is blocking the binaries on the mirror. Please subscribe to the bug for details.

---

### Post by ranch hand on 2010-04-15
Mine is working fine but I have never upgraded to the newest one.  Glad  I haven't now.

---

### Post by andrewabc on 2010-04-15
Bug report says it is fixed now.
Of course mirrors might not be up to date though.

---

### Post by chrisccoulson on 2010-04-15
I just mailed ubuntu-devel-annouce. For the benefit of those who are not monitoring that list, here is what I wrote:

> Hi,

Some people have experienced a problem with Thunderbird failing to start after upgrading to 3.0.4+nobinonly-0ubuntu2 (see [1]). An updated version which fixes this bug has been uploaded already and the affected binaries removed from the archive. If you have already updated to the affected version and you are experiencing this problem, then you will need to recover manually in order to use Thunderbird again.

The issue is that under certain conditions, the thunderbird wrapper script replaces your profile with a recursive symlink. If you are running the affected version and thunderbird no longer starts, please open a terminal and run "ls -ld ~/.*thunderbird*". If you see output similar to the following, then you are affected by this bug and will need to proceed with the instructions following.

lrwxrwxrwx 1 chr1s chr1s   24 2010-04-15 19:08 /home/chr1s/.mozilla-thunderbird -> /home/chr1s/.thunderbird
lrwxrwxrwx 1 chr1s chr1s   24 2010-04-15 19:08 /home/chr1s/.thunderbird -> /home/chr1s/.thunderbird
drwx------ 3 chr1s chr1s 4096 2010-04-15 19:08 /home/chr1s/.thunderbird.upstream

To recover from this, you need to:
1) Delete the recursive symlink (~/.thunderbird) by running "rm ~/.thunderbird". 
***Only do this if you see the output above, else you could be deleting your profile. If you are unsure, then rename the file instead***
2) Move ~/.thunderbird.upstream to ~/.thunderbird by running "mv ~/.thunderbird.upstream ~/.thunderbird"

Once you have done this, you will be able to open Thunderbird again.

Sorry for the inconvenience.

Regards
Chris

[1] - [https://launchpad.net/bugs/563893]("https://launchpad.net/bugs/563893") 

---

### Post by Cavsfan on 2010-04-15
My system is completely up to date (as of 1/2 hour ago) and I cannot open Thunderbird.

I will follow chrisccoulson's steps and get it fixed. Glad I seen this thread.

Thanks chrisccoulson!

---

### Post by FrancoNero on 2010-04-16
yeah those fixed it... for some reason it told me i cant rename thunderbird.upstream to thunderbird because it already existed when it really wasnt but oh well....

---

### Post by sartic on 2010-04-16
thx it was easy to recover from update width this thread

---

### Post by bplzip on 2010-04-16
Installed Thunderbird yesterday and had this problem. Ran Update Manager a few minutes ago. Thunderbird was one of the updates listed. I installed this update, but this did not fix the problem. So I uninstalled it, then reinstalled it using Ubuntu Software Manager.
Still did not work, so I ran the commands recommended above. I now have a Thunderbird that is working great.:P

Thanks, Chris.

---

### Post by Cavsfan on 2010-04-16
All fixed and working great now! Thanks!

---

### Post by KrazyPenguin on 2010-04-19
People still use Thunderbird???

I am way more productive using gmail with GTD (Getting thing done) combined with Firefox and a gmail ad-on, and push email on my phone.

Just wondering how opening another app (since 99.999% of people use a browser) is more productive then gmail and GTD and incorporated through firefox.

This is my setup and I haven't found one better.  Maybe I am retarded or maybe I am ahead of my time.  Or maybe some people are stuck in an old system.  But apps for email are kind o old fashion don't you think!?!?!??!?

;-)

---

### Post by cariboo on 2010-04-19
I use Thunderbird, because I pay for internet service, why should I pay extra to receive email on my cell phone? With my netbook, I can access email anywhere there is a wifi-signal.

---

### Post by ranch hand on 2010-04-19
> **KrazyPenguin said:**
> People still use Thunderbird???

I am way more productive using gmail with GTD (Getting thing done) combined with Firefox and a gmail ad-on, and push email on my phone.

Just wondering how opening another app (since 99.999% of people use a browser) is more productive then gmail and GTD and incorporated through firefox.

This is my setup and I haven't found one better.  Maybe I am retarded or maybe I am ahead of my time.  Or maybe some people are stuck in an old system.  But apps for email are kind o old fashion don't you think!?!?!??!?

;-)
There are actually many people, hard as it may be to believe, that don't like having anything to do with google in anyway.  Yes I am one of them and I do use Thunderbird.

There are also folks that do not like the idea of there email in the hands of some large data base.  I do admit to that also.  I can access the data base on my ISP and delete the whole bunch at any time.

I do have a little used webmail account that I use for contacting people to see if their main interest is spamming.  I look at it about 6 times a year.

---

### Post by wilee-nilee on 2010-04-19
I use Thunderbird and alltray to stick it in the notification area so that I will have easy access. I don't always have my browser open.

---

### Post by Cavsfan on 2010-04-19
> **ranch hand said:**
> There are actually many people, hard as it may be to believe, that don't like having anything to do with google in anyway.  Yes I am one of them and I do use Thunderbird.

There are also folks that do not like the idea of there email in the hands of some large data base.  I do admit to that also.  I can access the data base on my ISP and delete the whole bunch at any time.

I do have a little used webmail account that I use for contacting people to see if their main interest is spamming.  I look at it about 6 times a year.

I feel the same about google and I don't like webmail either. I like Thunderbird.

---

### Post by Technoviking on 2010-04-19
Fix has been released and sent to archives mirrors.

T-V

---

### Post by Kirk M on 2010-04-19
> **Technoviking said:**
> Fix has been released and sent to archives mirrors.

T-V

Many thanks. I love it when things (fixes) like this happen nice and quick. I didn't actually suffer from the problem since Thunderbird opened just fine after the update to 3.0.4 (perhaps due to using a separate profile for Thunderbird and not the default?) but it's great nonetheless. :lolflag:

---

