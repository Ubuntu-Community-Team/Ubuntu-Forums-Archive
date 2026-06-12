---
title: "Unable to copy audio CD with Brasero"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-02-25
I tried, just minutes ago, to copy audioCD in Brasero. It did not work, as it said, due to missing plugins... I have Brasero out-of-the-box that came with Lucid. What am I, if I am, doing wrong?

---

### Post by mc4man on 2010-02-25
> What am I, if I am, doing wrong?

Other than thinking that at any point in space and time brasero works 100% correctly, nothing.

If anything is missing it would be cdrdao, try installing if not already and give it another try..

---

### Post by VMC on 2010-02-25
You just reminded me to try Brasero again. Last time it failed to work.

This time it works perfectly.

I have Feb24th daily-live installed with all updates as of today. I haven't seen any Brasero updates come by in a while. I haven't installed any plugins either.

edit: Brasero 2.29.91

---

### Post by jppr on 2010-02-25
> **zika said:**
> I tried, just minutes ago, to copy audioCD in Brasero. It did not work, as it said, due to missing plugins... I have Brasero out-of-the-box that came with Lucid. What am I, if I am, doing wrong?

Zika, do sometimes clean / fresh installation and also your system works fine ;)

---

### Post by zika on 2010-02-25
> **VMC said:**
> You just reminded me to try Brasero again. Last time it failed to work.

This time it works perfectly.

I have Feb24th daily-live installed with all updates as of today. I haven't seen any Brasero updates come by in a while. I haven't installed any plugins either.

edit: Brasero 2.29.91Same version here.

---

### Post by zika on 2010-02-25
> **jppr said:**
> Zika, do sometimes clean / fresh installation and also your system works fine ;)Thank You. This is a rather fresh install that I'm on now... Where did You get impression that my install is stale...?

---

### Post by zika on 2010-02-25
> **mc4man said:**
> Other than thinking that at any point in space and time brasero works 100% correctly, nothing.

If anything is missing it would be cdrdao, try installing if not already and give it another try..cdrdao is a package separate from Brasero or it is a part of it...?

Update: This little program cdrdao worked like a charm! Thank You... Brasero, still, refuses to copy, log that it makes is empty... It'll come to state that it is usefull, once... I think it works for making LiveCD, that is enough, now that I have cdrdao...

---

### Post by andrew.46 on 2010-03-11
Hi zika,

> **zika said:**
>  This little program cdrdao worked like a charm! 

Perhaps you might be interested in copying audio cds with cdrdao alone? I have an old guide buried here:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

This is a technique I use all the time on my own system and has never failed me while the glitzy guis have let me down before...

All the best,

Andrew

---

### Post by zika on 2010-03-11
> **andrew.46 said:**
> Hi zika,



Perhaps you might be interested in copying audio cds with cdrdao alone? I have an old guide buried here:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

This is a technique I use all the time on my own system and has never failed me while the glitzy guis have let me down before...

All the best,

AndrewWhe I said it worked like a charm I meant that I was using cdrdao alone. Without these switches, but it copied a bunch of my Keith Jarrett CD's without a problem. Thank You for hints on /etc/cdrdao.conf. Can I put that file somewhere in $HOME? OK, I've found in man that I can use $HOME/.cdrdao. Great.

---

### Post by skitching on 2010-03-22
Thanks Andrew. I also have been unable to copy a CD with Brasero, but cdrdao from the commandline worked fine and saved the day.

Just for reference for others:
  Brasero version 2.29.91-0ubuntu2

Trying to "copy cd to cd" gives message:
  All required applications and libraries are not installed
  Please install the following manually and try again:
   cdda2wav (application)
   cdda2wav (application)

(yes, that is the same package-name twice)

After installing cdda2wav, the message is now:
  All required applications and libraries are not installed
  Please install the following manually and try again:

(yes, that is a totally blank list of packages to install)

Trying to "copy to image file" originally gave message:
  Please install the following manually and try again:
   toc2cue (application)
   cdrdao (application)

where toc2cue is not recognised by apt-get as a package-name.
Now I'm getting the same blank-list-of-packages-to-install.

If things don't improve in the near future, I'll raise a bugreport for this.

---

### Post by andrew.46 on 2010-03-22
Hi skitching,

> **skitching said:**
> Thanks Andrew. I also have been unable to copy a CD with Brasero, but cdrdao from the commandline worked fine and saved the day.

I remember switching a while back to commandline burning after a few bad experiences with gui offerings. If you are interested I wrote up what I considered the most usefull commands here:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

But bear in mind Ubuntu uses a fork of cdrecord and friends...

Andrew

---

### Post by skitching on 2010-04-01
I see the "copy cd to cd" issue has been reported as a bug:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696)

---

