---
title: "2 distro one \home"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by wojb on 2012-12-20
Hi

Is it possible to have one \home for  2 distributions?
I.e  I have installed 11.04 (32bit) and 12.04 (64bit) on one machine 
and would like to use one common \home\user for both.
Both systems have their own partition as well as \home.

Regards

---

### Post by oldfred on 2012-12-20
Not recommended.

If upgrading that would work, but when using the older system it may then find new settings from the new system that it does not know how to deal with.

Often better to have a shared data partition. If all data is in another partition /home is tiny and you can copy settings over when first installings but avoid the issues of different versions writing to the same file.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Pjotr123 on 2012-12-20
Not recommended +1.

Personally, I consider a separate /home (or any other separation) to be a needless complication:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column)

Only for the swap it's a real advantage to have a separate partition.

---

### Post by snowpine on 2012-12-20
I have done this before and it works fine. The secret is that you need to use separate usernames (and UUID's) for each distro.

What is the benefit of dual booting an obsolete "end of life" release, if you don't mind my asking?

---

### Post by wojb on 2012-12-20
Thanks all of you for answer. 

I understand thread.

Interesting and clever solution Snowpine.
Aswering to your question
I have stable and heavely covered  instance of 10.04.
Now I'd like to migrate to 12.04 - with minimal effort of course :).
But If I will find that something is wrong with 12.04, 
maybe after some time of work them,
I need to have my old sys in reserve.
After sometime - maybe year - if all will be ok I remove old sys
of course.

---

