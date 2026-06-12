---
title: "upgraded to 11.10 then 12.04--both keep stopping"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by Cecil McCoy on 2012-11-10
I am not new to Ubuntu, but feel like.  I have been using 10.10 since it came out and after a couple of "bumps" it has been working perfectly.  I hadn't used this laptop for several months and, when starting it in August, it said 10.10 was no longer supported and that I needed to upgrade.  I upgraded to 11.10.  It worked fine.  Day before yesterday, 11/8/2012 I decided to upgraded to 12.04 LTS because it is, well, LTS.  Something has changed as 12.04 will not work. very long, for me.  The system stops responding, although the cursor still works.  After the problem with 12.04 i reinstalled 10.11 and now it is doing the same thing.  I have tried several things mentioned on the internet, such as disabling hardware acceleration on Firefox, as that seems to be where it happened quickest.  None of the worked. The reason I originally went to Ubuntu/Linux is the laptop came with VISTA and I had had enough of MS; I have had good luck with Ubuntu so would appreciate any help.

---

### Post by ibjsb4 on 2012-11-10
Hi Cecil

Could be you need to install the proper video driver.  The right one could of got lost in the shuffle.  What kind of video card do you have?

---

### Post by Cecil McCoy on 2012-11-10
It's on an HP Pavillion laptop; I don't know what video set it uses.  I'm going to have to go back to notes as it's been years since I've used the terminal.  The 10.10 version just didn't give me any problems.

---

### Post by Cecil McCoy on 2012-11-10
GE Force 7150M/nForce 630m by nVidia.  Couldn't believe I found the notes so quick.

---

### Post by ibjsb4 on 2012-11-10
If you want a fix that will work right now you could download/install Lucid 10.04 LTS.  It is still supported until April of next year.

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by ibjsb4 on 2012-11-10
GE Force 7150M

[http://ubuntuforums.org/showthread.php?t=2028549](http://ubuntuforums.org/showthread.php?t=2028549)

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GE+Force+7150M+precise+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GE+Force+7150M+precise+12.04&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by critin on 2012-11-10
Just to be sure the machine can run Unity, copy and paste this code into the terminal, if you haven't already.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Cecil McCoy on 2012-11-10
> **critin said:**
> Just to be sure the machine can run Unity, copy and paste this code into the terminal, if you haven't already.

```
/usr/lib/nux/unity_support_test -p
```

Everything said yes including compatible with Unity!

---

### Post by Cecil McCoy on 2012-11-10
> **ibjsb4 said:**
> If you want a fix that will work right now you could download/install Lucid 10.04 LTS.  It is still supported until April of next year.

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Thanks for the info.  I'm just bull-headed enough to want to get this working.  I'm amazed at the amount of help from the Linux/Ubuntu community.  I'm far from a computer nerd and just like a system that is reliable--which Linux/Ubuntu is once the bugs are found.

---

### Post by Cecil McCoy on 2012-11-10
> **ibjsb4 said:**
> GE Force 7150M

[http://ubuntuforums.org/showthread.php?t=2028549](http://ubuntuforums.org/showthread.php?t=2028549)

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GE+Force+7150M+precise+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GE+Force+7150M+precise+12.04&as_qdr=all&sa=Google+Search&lang=en)

I downloaded the recommended driver; will let you know how it works.  Like I told ibjsb4 the Ubuntu community is amazing in their willingness to help!!!

---

### Post by ibjsb4 on 2012-11-10
> **critin said:**
> Just to be sure the machine can run Unity, copy and paste this code into the terminal, if you haven't already.

```
/usr/lib/nux/unity_support_test -p
```

Thats one cool test  :)

---

### Post by critin on 2012-11-11
Yes, it is.  Someone gave it to me  long ago and I found I couldn't run unity 3D.  2D is the best I can use, but it works for everything since I don't need turning cubes and bouncing what-evers.  lol

---

### Post by wjwh on 2012-11-11
> **critin said:**
> Just to be sure the machine can run Unity, copy and paste this code into the terminal, if you haven't already.

```
/usr/lib/nux/unity_support_test -p
```

Cannot get this to work.  Get the reply "No such file or directory" each time I try!  Any ideas.  I am using Ubuntu 10.04.

---

### Post by Cecil McCoy on 2012-11-11
> **critin said:**
> Just to be sure the machine can run Unity, copy and paste this code into the terminal, if you haven't already.

```
/usr/lib/nux/unity_support_test -p
```

It says it can.

---

### Post by Cecil McCoy on 2012-11-11
Downloaded the recommended driver yesterday and nothing changed.  I'm at the Denver airport on the way to a 2 week job so will be a bit before I get back to the problem.  Fortunately, I have another laptop for contract jobs.
Thanks for all the responses!!:smile:

---

### Post by ibjsb4 on 2012-11-11
> **wjwh said:**
> Cannot get this to work.  Get the reply "No such file or directory" each time I try!  Any ideas.  I am using Ubuntu 10.04.

10o4 is pre-unity (gnome2) and I suppect it is simply not offered.

---

### Post by wjwh on 2012-11-11
> **ibjsb4 said:**
> 10o4 is pre-unity (gnome2) and I suppect it is simply not offered.

So I need to be running Unity before I can run a test to see whether I can run Unity?  Duh!

---

### Post by ibjsb4 on 2012-11-11
> **wjwh said:**
> So I need to be running Unity before I can run a test to see whether I can run Unity?  Duh!

You made me laugh, but yes I guess that's one way to look at it.  So you install 12o4 and unity3d wont boot, instead you go to unity2d.  Or maybe your running 12o4 and want to upgrade to 12.10 which does not have the 2d option.  Don't you think it would then come in handy?  Plus I said I suspect that's the reason; maybe its time to do some googling  :)

---

