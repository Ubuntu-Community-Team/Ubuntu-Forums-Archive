---
title: "Feb 22, Pre A3-What is the current status of getting full ATI graphic support?"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-22
Just wondering - I recall something about the "X" window having problems, the kernel not being updated, the FGLRX not ready for either and the Closed Source ATI/AMD driver not anywhere near being ready.

---

### Post by anders_c_ on 2010-02-22
Isn't fglrx and closed source driver the same thing?
And no, Catalyst 10.2 (latest one right now) does not support the Xserver used in Lucid. But they release a new one each month so we will "hopefully" have it soon...

---

### Post by antiram on 2010-02-22
open source radeon works with r600 (hd3450) and live image from 20-Feb. i had kms with dri-1 3d. firefox scrolling was fast.

the only problem is the same as in fedora 12: mode switching with kms makes a black screen for ~30s.

---

### Post by cariboo on 2010-02-22
I tried to install todays daily, and couldn't boot to the desktop because of the lack of the safe graphics option. I'm using an Nvidia GT210, which isn't detected properly at startup. I used the alpha2 to install and it download 734 updates, and that's without having anything installed.

---

### Post by emarkay on 2010-02-23
Will the Alpha3 release have this problem resolved?

---

### Post by anders_c_ on 2010-02-23
> **emarkay said:**
> Will the Alpha3 release have this problem resolved?
No, since this has nothing to do with ubuntu development. The driver is closed source so Ubuntu devs can't do a thing about it. ATI "decides" when this will be resolved...

---

### Post by kansasnoob on 2010-02-23
> **cariboo907 said:**
> I tried to install todays daily, and couldn't boot to the desktop because of the lack of the safe graphics option. I'm using an Nvidia GT210, which isn't detected properly at startup. I used the alpha2 to install and it download 734 updates, and that's without having anything installed.

This:

> the lack of the safe graphics option

I was asking about here:

[http://ubuntuforums.org/showpost.php?p=8872534&postcount=9](http://ubuntuforums.org/showpost.php?p=8872534&postcount=9)

Since you didn't include a bug report number I guess I should file one.

---

### Post by kansasnoob on 2010-02-23
> **emarkay said:**
> Will the Alpha3 release have this problem resolved?

Doubtful if people don't file "critical" bug reports!

---

### Post by kansasnoob on 2010-02-23
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526781](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526781)

---

### Post by cariboo on 2010-02-23
Actually I did post a bug number in another thread but here it is. #[lpbug]525966[/lpbug] Safe graphics mode was removed from the F4 menu, as it isn't needed any more. Press F6 and select nomodset, is now the preferred way to boot if your graphics card isn't detected properly. Using nomodset solved my boot problem with yesterdays daily build.

---

### Post by kansasnoob on 2010-02-23
> **cariboo907 said:**
> Actually I did post a bug number in another thread but here it is. #[lpbug]525966[/lpbug] Safe graphics mode was removed from the F4 menu, as it isn't needed any more. Press F6 and select nomodset, is now the preferred way to boot if your graphics card isn't detected properly. Using nomodset solved my boot problem with yesterdays daily build.

I'll mark mine invalid then.

I do wonder though, if that stops someone from being able to use the Live CD is it "fixed"?

---

### Post by rbmorse on 2010-02-23
Bryce reported in a similar thread that he expects a Lucid compatible update to FGLRX before Lucid goes final.

---

### Post by cariboo on 2010-02-23
> **kansasnoob said:**
> I'll mark mine invalid then.

I do wonder though, if that stops someone from being able to use the Live CD is it "fixed"?

It may stop someone if they aren't aware of the change, like I was. After it didn't work yesterday I marked the CD NFG and threw it in the garbage, I saw Colin's reply later on that night, so I dug it out of the garbage this morning and gave it a second try, it worked using nomodeset the way it was supposed to.

Hopefully they add something to the release notes about it.

---

### Post by keypox on 2010-02-23
The question i asked for years until i finally went nvidia.

---

### Post by emarkay on 2010-02-24
> **kansasnoob said:**
> Doubtful if people don't file "critical" bug reports!

Don't consider lack of 3D "bells and whistles" as "critical", and I know there are more than a few reports detailing the ATI issues in Lucid.

Just wanted a "status update"  :)

---

