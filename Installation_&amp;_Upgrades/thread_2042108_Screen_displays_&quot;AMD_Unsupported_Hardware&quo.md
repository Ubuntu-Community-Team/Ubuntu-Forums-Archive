---
title: "Screen displays &quot;AMD Unsupported Hardware&quot;"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2012-08-14
After installation, I saw "Additional Drivers" Under Hardware.  I have a AMD 7750 video card, which I understand is supported by Ubuntu native drivers, so I assumed these drivers were for my card.  (See   [http://www.theinquirer.net/inquirer/news/2162461/amd-releases-source-linux-driver-support-southern-islands-gpus](http://www.theinquirer.net/inquirer/news/2162461/amd-releases-source-linux-driver-support-southern-islands-gpus)   and   [http://www.anandtech.com/show/5541/amd-radeon-hd-7750-radeon-hd-7770-ghz-edition-review/](http://www.anandtech.com/show/5541/amd-radeon-hd-7750-radeon-hd-7770-ghz-edition-review/)) 

My screen now displays "AMD Unsupported Hardware"in the lower right corner.

How do I :
1) Get this off my screen?
2) Get the right drivers?

Thanks!

---

### Post by Bucky Ball on 2012-08-14
1/ Untick the Additional Driver and that should go. 
2/ Working on it but others have had issues getting this up. If you have the driver enabled you should also have the Catalyst Control centre installed. Launch it, and find out which version it is (12.3 for instance). 

Seems this graphics card is not supported on older versions of Catalyst. You are using 12.04?

PS: I don't see anything about Ubuntu on the links you provided ... ;)

---

### Post by RogerDavis on 2012-08-14
The drivers are both unticked.  They are indicated as inactive.  The "Unsupported" icon is still there.

I am using 12.04 .

How do I launch Catalyst Control Center?

I couldn't find the Ubuntu reference quickly enough to make this post rapidly.

Now I'm trying to find the log file it gave me, but no luck...

Thanks!

---

### Post by Bucky Ball on 2012-08-14
I use Xubuntu but from memory you should find it in System>Administration or Preferences.

---

### Post by RogerDavis on 2012-08-14
Got it... I'm pretty sure it wasn't there before, must have been added by the drivers.

STILL have the "Unsupported" incon.

---

### Post by RogerDavis on 2012-08-14
OK, I found Catalyst Contol, but it's not doing me any good.  The #@%%$^%$ icon is still there, and now my alt/tab switching doesn't work.

How do I just get rid of it?

---

### Post by RogerDavis on 2012-08-14
Failire Log file attached

---

### Post by Bucky Ball on 2012-08-14
> **RogerDavis said:**
> Failire Log file attached

Sorry, can't see attached file. ;)

---

### Post by qamelian on 2012-08-14
Your card is too new for the driver included with Precise. To install a newer version, follow the link below. This will walk you through creating debs of the newest available driver, which should support your card.

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

---

### Post by RogerDavis on 2012-08-14
My card is the 800 mhz version, not the newer 900.  

Is the driver still too old?

---

### Post by qamelian on 2012-08-14
> **RogerDavis said:**
> My card is the 800 mhz version, not the newer 900.  

Is the driver still too old?

Yes, that is what the watermark on your display is telling you. I had the same problem on my netbook with the 6310 GPU a couple of releases ago. Once you install the latest drivers following the instructions at the link I posted, the watermark should go away.

---

### Post by RogerDavis on 2012-08-17
A few questions:
1) I don't suppose you have any idea how long until it gets native support?
2) If I install from the instructions, will updates happen automatically?
3) If I want to back off until native support, or just get rid of the @#$%%^ "unsupported hardware"until I can install fully, can I simply click "Remove" in Additional Drivers and the icon will go away?
4) Should I report a bug that System Settings picks up the wrong drivers?
Thanks!

---

### Post by Bucky Ball on 2012-08-17
Yea, try disabling the restricted drivers.

Just out of curiosity; I have two restricted driver, on stable and on and update to that. The stable works fine but if I attempt to enable the update it crashes the system. You haven't got that second one enable also, by chance?

---

### Post by RogerDavis on 2012-08-17
I only have the earliest one enabled, I couldn't get the second one to load.  
 
Do you have any ideas about :
1) I don't suppose you have any idea how long until it gets native support?
2) If I install from the instructions, will updates happen automatically?
3) If I want to back off until native support, or just get rid of the @#$%%^ "unsupported hardware" icon until I can install fully, can I simply click "Remove" in Additional Drivers and the icon will go away?
4) Should I report a bug that System Settings picks up the wrong drivers?

Thanks!

---

### Post by qamelian on 2012-08-18
> **RogerDavis said:**
> I only have the earliest one enabled, I couldn't get the second one to load.  
 
Do you have any ideas about :
1) I don't suppose you have any idea how long until it gets native support?
2) If I install from the instructions, will updates happen automatically?
3) If I want to back off until native support, or just get rid of the @#$%%^ "unsupported hardware" icon until I can install fully, can I simply click "Remove" in Additional Drivers and the icon will go away?
4) Should I report a bug that System Settings picks up the wrong drivers?

Thanks!
1) Probably not until the next Ubuntu release
2) No, updates will need to be done manually following the same instructions.
3) Yes, provided nothing else is wrong.
4) No, it isn't a bug. This is the version of the driver that was stable when your version of Ubuntu was released. It is normal for packages to be stablized like this between releases, except in special circumstances.

---

### Post by Bucky Ball on 2012-08-19
Point to be made here, Roger Davis. This has nothing to do with Ubuntu or Linux full stop. If third parties decide they are going to port to Linux as well as MS and Mac, so be it. Ubuntu users, or anyone else, can't rely on that. I hate to bring up the issue of money but why would they waste their time?

This is the point: Open source developers can't do much with an OS or an app if the third-party hardware manufacturers are not playing along and supplying drivers and support. What they can do is spend their own good money to buy hardware simply to take it apart, figure out how it works, and write the code for the community (donations anyone?). 

We could go further with this but don't want this thread to wind up in 'Recurring Discusssions'. 

The questions you ask are totally relevant and valid. Makes you wonder how far behind in software/hardware sophistication we are due to third-party interference! But they are my own futurist tendencies.

Best
BB

PS: What you're asking can possibly only be answered by yourself and ask more questions when you hit a wall. Keep asking ... ;)

---

### Post by RogerDavis on 2012-08-19
It seems that there are drivers for this card in existence based on both one of the earlier answers, and on an announcement that this card will be supported natively -  see   [http://openbenchmarking.org/result/1207092-SU-AMDCATALY06:ZmdscnggOS4wLjAgQmV0YQ](http://openbenchmarking.org/result/1207092-SU-AMDCATALY06:ZmdscnggOS4wLjAgQmV0YQ)  and   [http://www.theinquirer.net/inquirer/news/2162461/amd-releases-source-linux-driver-support-southern-islands-gpus](http://www.theinquirer.net/inquirer/news/2162461/amd-releases-source-linux-driver-support-southern-islands-gpus)   .

So I was hoping that someone who either plays a part in making these drivers native in Ubuntu or someone who knows details could inform me and others of the status and the rest of the answers to my questions.

Thanks!

---

