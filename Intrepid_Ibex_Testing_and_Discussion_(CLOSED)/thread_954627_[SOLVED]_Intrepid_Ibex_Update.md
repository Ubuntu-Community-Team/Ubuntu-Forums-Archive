---
title: "[SOLVED] Intrepid Ibex Update"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lhb1142 on 2008-10-21
:KSI am curious as to what will happen in a few days when Intrepid Ibex is released.

Will the Update Manager offer to download and install this version?

Will my Software Sources (especially third-party sources) be changed automatically?

Would my installed programs be retained and/or updated automatically?

Based on others' previous experience, would it be better to:

1) Let the Update Manager handle everything, or

2) Install Intrepid Ibex from a disc, or

3) Leave well enough alone and stay with Hardy Heron. If I do that, will there be notices of "bugs" and "fixes" in Intrepid Ibex? In other words, should I be the first kid on my block to install this new OS or is it better to wait?

Thanks for any information on this subject.:lolflag:

---

### Post by Crandom on 2008-10-21
Read this for more info: [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

You will basically have 2 options:

1. Follow the "automated" install. This will "convert" your pc to hardy while keeping all your settings and it should be usable after one restart. It takes about 40-60mins and requires a reliable (preferabley) fast internet connection. All your current  hardy packages are deleted and shiny, new intrepid packages (often exactly the same data) is downloaded. You retain all you programs.

2. Reinstall from the new livecd. If you have a separate /home partition, you retain your files and settings. If not you don't retain anything and should BACKUP EVERYTHING onto an external device. Likely to work.

Every time I have let update manager try to upgrade, it has dramatically failed and left me with a terrible, half broken wretch of an operating system that crashes every 12 seconds. If you have ATI and are using fglrx, never take option 1. I would suggest you take option 2. Sure it takes longer but is garunteed to work without too much failure.

---

### Post by wolfen69 on 2008-10-21
> **lhb1142 said:**
> 
2) Install Intrepid Ibex from a disc, or

3) Leave well enough alone and stay with Hardy Heron.

i suggest one of those options. if hardy works for you, why switch?

---

### Post by lhb1142 on 2008-10-22
I do believe that I'll stay with 'Hardy" for the time being. As 'Ibex' is not a long-term release and the next LTS is coming out in April 2009, I may skip 'Ibex' unless it turns out to be something superlative.

I thank those who replied to me.

---

### Post by wgrant on 2008-10-22
The next LTS will not be 9.04. It will be 10.04.

---

### Post by lhb1142 on 2008-10-25
Dear Mr. Grant;

I am curious. Who decides and how is it decided whether a release will be offered long-term support or will just be a standard release?

Is there a reason that some releases are LTS and others are not?

Let us suppose, for the sake of argument, that v. 8.10 'Intrepid Ibex' turns out to be a superlative release, one that everyone loves. Would that release be able to be "converted" to LTS?

Is there any possibility in future releases that updated programs could be added to the repository(s) in a current release? I am referring in particular to OpenOffice v.3.0 which, I understand, will not be added to 8.04 'Hardy Heron.' Can this policy be changed in the future?

Thank you for any information you can supply.

Lawrence H. Bulk

---

### Post by jmmL on 2008-10-25
I'm not Mr Grant, and I won't be able to answer your questions fully, but here goes.

I assume the MOTUs decided to set up the LTS strategy. Currently, ever 2 years there is a LTS release. So far we've had Dapper (6.06) and Hardy (8.04). The next one will therefore be 10.04.

OO.o3 should become available in the hardy-backports repo. Currently, it's not even in intrepid, because it was released too close to intrepid's main release. It should become available in the repos within a few weeks I guess.

Also (correct me if I'm wrong), but 8.04.2 should contain updated programs, whenever that's released, in the same way 8.04.1 had the final version of Firefox 3.

---

### Post by maestrobwh1 on 2008-10-25
I think the pattern for LTS is 18 months to 2 years and I don't remember which. 

It seems those beginning with even numbers and having a decimal .04 are the LTS versions.  The last LTS was 6.04, Dapper Drake.  8.04 Hardy Heron is, and then 10.04.

There are some quirks with Intrepid so far, and wireless is a bit flaky still; however, other things on my laptop seem to work really well... hibernate never worked and now it does.  

If you are using Kubuntu, then the difference wiht Intrepid is even greater.  KDE4.1 is fully integrated into the user directory and there is no overlap of KDE3.

If everything is how you like it already, just stick with Hardy.

---

### Post by autocrosser on 2008-10-25
The LTS release time is every two years--Dapper (6.06) was late due to "teething problems"--we all decided to delay to make it better. Also, the support time for a LTS is three years--so you have plenty of time to decide.....

---

### Post by lhb1142 on 2008-10-25
Thanks to all who have replied to me.

Here is another question: how does one find out about a new interim release such as 'Hardy Heron' v. 8.04.1 or v. 8.04.2?

I found out about 8.04.1 strictly by accident and, of course, downloaded it. It is the version I used when I reinstalled Ubuntu.

Is there an "official" place to find out about these new interim releases? Does Ubuntu have an e-mail service which would send such information?

BTW I tried to install the DEB version of OO v.3.0 with no luck at all. I got most of the 48 folders installed (all but 10 I think) and I got the "main" program to install but nothing actually worked. So I uninstalled all of v. 3.0 and reinstalled 2.4.

Thanks again to all for your assistance and consideration.:)

---

### Post by Sealbhach on 2008-10-25
Canonical releases a new version every six months, in the fourth month and the tenth month of every year.

Hence 8.04 and 8.10.

So, you can predict with some confidence that Ubuntu 20.10 will be released in October 2020.:)


Some more info here:

[http://www.downloadsquad.com/2008/05/12/ubuntu-release-schedule-right-on-schedule-and-then-some/](http://www.downloadsquad.com/2008/05/12/ubuntu-release-schedule-right-on-schedule-and-then-some/)

.

---

### Post by kansasnoob on 2008-10-25
First of all, if you want to stay with 8.04.1 LTS (aka Hardy) just make sure this page in Software Sources:

[ATTACH]89656[/ATTACH]

Is set to LTS Release only!

Second what I like to do is shrink my current Ubuntu OS and install a fresh new Ubuntu OS like this:

[ATTACH]89656[/ATTACH] 

That way I can easily transfer files from one OS to the other, and when I'm all done I'll usually have things in somewhat of a mess, so I just use manual partitioning to delete the unwanted OS and do a fresh installation of my new OS on a primary partition. Then I transfer all of my files and the beauty is that I never lose the use of my puter!

Clear as mud:confused:

---

### Post by kansasnoob on 2008-10-25
Oops, I goofed the second screenshot!

[ATTACH]89660[/ATTACH]

---

