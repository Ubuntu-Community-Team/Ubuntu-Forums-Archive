---
title: "Message when testing integrity of Lucid CD"
date: 2009-12-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wpshooter on 2009-12-24
Why do I get "**_Opening pipe: No such file or directory_**", when attempting to run a check CD for defects function on the Lucid daily build 32 bit desktop version ?

After this message is displayed NOTHING else happens.  The integrity check function does not continue and eventually the message disappears from the screen and I then have to reboot the computer.

Thanks.

---

### Post by phillw on 2009-12-25
> **wpshooter said:**
> Why do I get "**_Opening pipe: No such file or directory_**", when attempting to run a check CD for defects function on the Lucid daily build 32 bit desktop version ?

After this message is displayed NOTHING else happens.  The integrity check function does not continue and eventually the message disappears from the screen and I then have to reboot the computer.

Thanks.

Are you using the inbuilt CheckCD integrity ? Obviously, if CD is not 'well' then that, in itself could be affected. Have you tried running the md5 checksum on it from a working  installation ? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the Disk checks out as okay by that method & the CheckCD hangs - then it looks like a bug that needs reporting.

Phill.

---

### Post by kansasnoob on 2009-12-25
Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+bug/500198](https://bugs.launchpad.net/ubuntu/+bug/500198)

---

### Post by ranch hand on 2009-12-25
> **kansasnoob said:**
> Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+bug/500198](https://bugs.launchpad.net/ubuntu/+bug/500198)
And you BETTER add to that bug.  Right now it is listed as effecting 2 people.  I do not think that is right.  I know it is hard to click on that link and then on "effects me too but DO IT anyway.

---

### Post by kansasnoob on 2009-12-25
> **ranch hand said:**
> And you BETTER add to that bug.  Right now it is listed as effecting 2 people.  I do not think that is right.  I know it is hard to click on that link and then on "effects me too but DO IT anyway.

I just realized I hadn't clicked on that :P

Launchpad can be almost overwhelming at times, it seems like I learn more every day.

---

### Post by ranch hand on 2009-12-25
OK now all three of us that have this problem are on record.  I sure am glad it isn't more.

Yes I know I am a grumpy geezer.  I also know that a lot of people are going to be pissing and moaning about this when it is released.

---

### Post by jerrynewt on 2009-12-25
Same here for me. I even tried remastersys to create a custom distro from my install on my desktop (which is working fine far as I can tell). Burned the iso to disc and still get the same thing on my laptop. Dunno what the updates did but it messed up a lotta stuff!

---

### Post by ranch hand on 2009-12-26
> **jerrynewt said:**
> Same here for me. I even tried remastersys to create a custom distro from my install on my desktop (which is working fine far as I can tell). Burned the iso to disc and still get the same thing on my laptop. Dunno what the updates did but it messed up a lotta stuff!
I hope you got on to that bug.

---

### Post by jerrynewt on 2009-12-26
> **ranch hand said:**
> I hope you got on to that bug.

Sure did -- hope it does some good, and more people get on it.

---

### Post by ranch hand on 2009-12-26
You are good GOOD boy.

This is what we are here in testing for.

Have a cookie with your FUN.

---

