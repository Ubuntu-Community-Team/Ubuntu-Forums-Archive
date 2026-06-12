---
title: "using intrepid repos as well as hardy repos in sources.list"
date: 2008-06-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pluckypigeon on 2008-06-04
In my sources.list I have added intrepid as well as hardy.:confused:

Is their anything wrong in doing this?? :confused:

I was looking for an update of audacity and I saw it was in the intrepid repos.:(

What is the worst that could happen?? :confused:

Would I be able to solve the problems? :)

I keep my home folder on a different Hdd so I'm not to worried:)

---

### Post by Oldsoldier2003 on 2008-06-04
> **pluckypigeon said:**
> In my sources.list I have added intrepid as well as hardy.:confused:

Is their anything wrong in doing this?? :confused:

I was looking for an update of audacity and I saw it was in the intrepid repos.:(

What is the worst that could happen?? :confused:

Would I be able to solve the problems? :)

I keep my home folder on a different Hdd so I'm not to worried:)

bad idea

mixed repos are always a bad idea

compile it from source

you could render your system unusable and require a reinstall

possibly, but its very likely you would not

---

### Post by pluckypigeon on 2008-06-04
> **Oldsoldier2003 said:**
> 

you could render your system unusable and require a reinstall

how unusable?? wouldn't I just get broken dependencies??

---

### Post by Oldsoldier2003 on 2008-06-04
> **pluckypigeon said:**
> how unusable?? wouldn't I just get broken dependencies??

Yes, the problem is that when you mix the repos you will break dependencies and often place your self is an unrecoverable position.

You have to remember that Intrepid is pre alpha and will be prone to catastrophic failurefor some time to come.

Unless you plan on being an early tester of Intrepid its just safer to just compile the apps you want from source. The fact that we are having this conversation leads me to believe that you aren't interested in being an Alpha tester?

---

### Post by pluckypigeon on 2008-06-04
> **Oldsoldier2003 said:**
> The fact that we are having this conversation leads me to believe that you aren't interested in being an Alpha tester?
 Actually, I would like to contribute. Not sure actually where to begin though. What do I need to know? What sort of stuff would I have to do??:)

---

### Post by bapoumba on 2008-06-04
Did you run the upgrade or not ? If not, please remove all your Intrepid repos and reload the sources.list file.

---

### Post by pluckypigeon on 2008-06-04
> **bapoumba said:**
> Did you run the upgrade or not ? If not, please remove all your Intrepid repos and reload the sources.list file.

Why?

---

### Post by robertchahine on 2008-06-04
> **bapoumba said:**
> Did you run the upgrade or not ? If not, please remove all your Intrepid repos and reload the sources.list file.
bapoumba is right.
i think it will be a disaster if you update your system

---

### Post by pluckypigeon on 2008-06-04
> **bapoumba said:**
> Did you run the upgrade or not ? If not, please remove all your Intrepid repos and reload the sources.list file.

I haven't run the upload. What use are the intrepid repos if intrepid alpha isn't out till the 12th and I can't use them with Hardy?

I would like to help test ubuntu alpha. My terminal/linux knowledge is minimal but I know python and c++

---

### Post by Oldsoldier2003 on 2008-06-04
> **pluckypigeon said:**
> Actually, I would like to contribute. Not sure actually where to begin though. What do I need to know? What sort of stuff would I have to do??:)

Testing a pre-alpha release is not for the faint of heart and definitely not the thing to do on your "production" machine. If you are interested in it I would suggest you re-install Hardy on a separate partition and upgrade it. (I'm not sure if the daily builds of Intrepid have started yet, since I wont be bothering to test Intrepid until its at Alpha2) You should also familiarize yourself with basic linux troubleshooting and how to file a proper bug report. Expect a few glitches along the way and don't get overly discouraged if something fails to work- thats how  the release gets debugged and fixed up until its ready for release.

---

### Post by sayakb on 2008-06-04
If you intend to test the alpha, you can rather start from a [barebone install]("https://help.ubuntu.com/community/Installation/MinimalCD") and add only intrepid repos there.

---

### Post by pluckypigeon on 2008-06-04
I'm an idiot anyway. I installed hardy from the alpha stage and had it ever since. (with a few problems, which aren't their anymore though)

I'll give testing a go this time (if i install intrepid alpha)

---

### Post by bapoumba on 2008-06-04
> **pluckypigeon said:**
> I haven't run the upload. What use are the intrepid repos if intrepid alpha isn't out till the 12th and I can't use them with Hardy?

I would like to help test ubuntu alpha. My terminal/linux knowledge is minimal but I know python and c++
You cannot mix several distros (debian + ubuntu) or several releases (hardy + intrepid) without problems.
Packages are all tied up in the dependencies tree. They are at the proper versions, within one particular release. If you mix up repos, you can end up in dependency hell and an unusable system. An upgrade installs the newest, higher version packages. Say some are upgraded, some not and still depend on the lower version, you're in trouble. If just the package manager complains, you can get away with it, with some non-functional applications. If system packages are borked, you can say goodbye to your system (and reinstal..).

> **Oldsoldier2003 said:**
> Testing a pre-alpha release is not for the faint of heart and definitely not the thing to do on your "production" machine. If you are interested in it I would suggest you re-install Hardy on a separate partition and upgrade it. (I'm not sure if the daily builds of Intrepid have started yet, since I wont be bothering to test Intrepid until its at Alpha2) You should also familiarize yourself with basic linux troubleshooting and how to file a proper bug report. Expect a few glitches along the way and don't get overly discouraged if something fails to work- thats how  the release gets debugged and fixed up until its ready for release.
+1

> **pluckypigeon said:**
> I'm an idiot anyway. I installed hardy from the alpha stage and had it ever since. (with a few problems, which aren't their anymore though)

I'll give testing a go this time (if i install intrepid alpha)
If you want to test intrepid, or contribute to its development and troubleshoot bugs, or just have fun with it, you can do it, but on a separate install.

---

### Post by iamkrazee on 2008-08-04
I was wondering.. the only package that I'd REALLY need is w64codecs and a couple of its siblings. Mostly they don't have many dependancies in hardy, so fetching them from medibuntu source shouldn't cause any "unrecoverable" problems right? Usually I go into testing all out, like without worrying much about the system, the only thing is that my connxn has gone VERY weak since a past few days so I'm reconsidering that policy. I already have intrepid installed and a bunch of softwares installed from intrepid repos.

---

### Post by northern lights on 2008-08-04
'medibuntu' is not a different release. You can safely add the (right) medibuntu repositories.

As an aside: Dude, this is major archeology. You should have posted in a new thread.

---

### Post by shenki on 2008-08-05
> **pluckypigeon said:**
> In my sources.list I have added intrepid as well as hardy.:confused:

Is their anything wrong in doing this?? :confused:

I was looking for an update of audacity and I saw it was in the intrepid repos.:(


This is fine to do, as long as you take the right precautions.

You need to pin apt so that it will still use Hardy packages by default, and only install Intrepid versions when you explicitly ask for it.

To do this, create the file /etc/apt/preferences with the following:

```

 Package: *
 Pin: release a=hardy
 Pin-Priority: 900
 
 Package: *
 Pin: release a=intrepid
 Pin-Priority: 800

```

Now you can install the updated audacity by one of two ways.

The first will not work if the Intrepid version of Audacity relies on versions of other packages that are only available in intrepid:

```
sudo apt-get install audacity/intrepid
```

The second way will work if Audacity requires dependencies from Intrepid, but has a higher chance of breaking your system as it will be pulling in more than just audacity from Intrepid:

```
sudo apt-get -t intrepid install audacity
```

Here is a good reference that explains apt pinning (if my explanation differs, please follow the instructions on this page):

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by northern lights on 2008-08-05
> **northern lights said:**
> this is major archeology
@shenki: Are you aware of the age of this thread?

---

### Post by shenki on 2008-08-05
> **northern lights said:**
> @shenki: Are you aware of the age of this thread?

Sure.

I was looking for solutions to my (unrelated) intrepid issue, and while reading this thread I noticed it was was full of incorrect advice.  Feel free to ignore it if you're not interested :)

---

### Post by northern lights on 2008-08-05
Did anything but ignore. Sensible post, valuable information.
Nonetheless, it _is_ archeology.

Unsubscribing from this thread, over & out.

---

### Post by usb.poncho on 2008-09-28
just updated my hard to intrepid with manual mixed intrepid/hardy repos. I did not really know what I do, it was just a test. ;)

and so far, it runs fast & stable, only had a few small dependencies issues...

---

### Post by deadite66 on 2008-09-28
getdeb has updated audacity debs for hardy
[http://www.getdeb.net/app/Audacity](http://www.getdeb.net/app/Audacity)

---

