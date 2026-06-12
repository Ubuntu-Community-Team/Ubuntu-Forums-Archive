---
title: "Not able to install Lucid invalid username."
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-02-19
Hi All,

I just downloaded the daily image. I logged in as Ubuntu and password. When i try to install it gives me an error invalid username at the partition editor stage. I am also not able to get rid of the pop up windows as pressing OK brings back the pop up windows.

Thanks,
SK.

---

### Post by sparker256 on 2010-02-20
> **soham_1207 said:**
> Hi All,

I just downloaded the daily image. I logged in as Ubuntu and password. When i try to install it gives me an error invalid username at the partition editor stage. I am also not able to get rid of the pop up windows as pressing OK brings back the pop up windows.

Thanks,
SK.

This daily live should not ask you for a username or password to install. I put mine on a usb thumb drive and is how I install.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Bill

---

### Post by rogerdean on 2010-02-21
I'm afraid it does Bill, tested also with the daily image for today. Is anyone else having this trouble?

Cheers
Roger

---

### Post by antiram on 2010-02-21
yes the installer (from 20-Feb) says wrong username/pw or so and i cannot install. I used a selfmade partition layout. 

Maybe it work with th default partition layout?

And another thing: Sometimes the x-session crashed and gdm want a username/pw. Don't know which, i restarted gdm from a shell.

---

### Post by rogerdean on 2010-02-21
interesting... i just installed in virtualbox (so no custom partitioning) and all is well. but usually i too use a pre-set partitions, and doing that it failed. i guess this suggests a bug in ubiquity...

---

### Post by VMC on 2010-02-21
**This is inexcusable.**

Yes, I know, this is testing, but if you can't install it, what's to test ?! 

Can someone explain to me why Ubiquity has so many problems. It's a crap-shoot each time I try to install using Ubiquity. It appears as fragile as an egg. One wrong move, game over. 

**debian-installer** used in the alternate install is rock solid. Whatever gui they use for Ubiquity, needs to be re-thought. Its just not reliable.

Here's a picture of the error the OP was talking about. This is most frustrating:

---

### Post by mc4man on 2010-02-21
See the same thing, it's skipping the set username screen after partitioning, so you get the error, complete pita
(though the resolution of setup is much improved, previously was 1600x1200, now a more usable 1280x1024

---

### Post by rogerdean on 2010-02-22
still no change on today's daily image...

---

### Post by soapytheclown on 2010-02-22
daww i got this as well using manual partitioning! :(

---

### Post by VMC on 2010-02-22
Here's the fix, if you have Windows on your first partition (maybe any partition):

Boot up using the first menu option, "Try..."

Once booted up do the following:

**Alt+F2**, then insert the following command:

```
sudo ubiquity --no-migration-assistant
```

That worked for me. Once I find the bug report I created, I will post it back here.

---

### Post by rogerdean on 2010-02-22
Works, many thanks
I don't think it's anything to do with Windows though, rather just having custom partitioning. I don't have Windows...
Cheers

---

### Post by VMC on 2010-02-22
This has been fixed in ubiquity - 2.1.24

Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/524993").

---

### Post by soapytheclown on 2010-02-22
yay it works all installed now :D

---

### Post by donniezazen on 2010-02-22
> **VMC said:**
> This has been fixed in ubiquity - 2.1.24

Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/524993").


The daily image from Feb 22 still have the bug.

---

### Post by donniezazen on 2010-02-22
The daily image from Feb 22 still have the bug.

---

### Post by VMC on 2010-02-23
> **soham_1207 said:**
> The daily image from Feb 22 still have the bug.

Try opening a terminal and type 'ubiquity --version'. 
See if its "2.1.24".

Also, todays daily-live(Feb23), doesn't have this error anymore.

---

### Post by rogerdean on 2010-02-23
confirmed, that's great

perhaps OP could mark this one as solved...?

---

### Post by VMC on 2010-02-23
We have a new error related to *migration-assistant* though. I updated the bug report to reflect the error.

---

### Post by donniezazen on 2010-02-23
> **VMC said:**
> Here's the fix, if you have Windows on your first partition (maybe any partition):

Boot up using the first menu option, "Try..."

Once booted up do the following:

**Alt+F2**, then insert the following command:

```
sudo ubiquity --no-migration-assistant
```

That worked for me. Once I find the bug report I created, I will post it back here.

> **VMC said:**
> Try opening a terminal and type 'ubiquity --version'. 
See if its "2.1.24".

Also, todays daily-live(Feb23), doesn't have this error anymore.

The today's image did have a bug but above command was able to solve the problem. I will try to get the ubiquity version later tonight.

> **rogerdean said:**
> confirmed, that's great

perhaps OP could mark this one as solved...?

I could mark this as solved but their is another related bug??

Thanks all.

---

