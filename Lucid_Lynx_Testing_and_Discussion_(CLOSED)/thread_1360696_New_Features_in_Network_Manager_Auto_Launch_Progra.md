---
title: "New Features in Network Manager Auto Launch Programs"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2009-12-21
In Lucid there will be a new feature that allows Network Manager to launch programs once it is connected. (for wireless)

This is awesome since most people using a desktop in the morning just want to get online and check email, facebook, latest news, etc.

Now once the Lucid desktop comes up and a connection is made, it automatically launches programs that the user easily adds through a GUI.  
These programs are ones that connect to the internet, like amsn, or thunderbird, firefox, facebook, Chrome, news, weather, blogs,etc.  Whatever you want without having to do the same routine over and over again everyday.

This allows easily configuration of the system and it very friendly.

Unfortunately what I just wrote is not true.  Hopefully somebody reads this and implements it, since this is truly the direction computers are heading.

Maybe there is a way to do this now, like a timer or some kind of script.
That isn't easy and the timer isn't what i am referring to either.  
I'm talking about actually launching those internet programs AS SOON as a connection is established, in an order.  If the wireless connection is lost (if it happens) the launching will pause if there were multiple programs.

K thanks for reading.
;-)

---

### Post by tad1073 on 2009-12-21
you can do
```
System>Preferences>Startup Applications>Options>
```

---

### Post by KrazyPenguin on 2009-12-21
> **tad1073 said:**
> you can do
```
System>Preferences>Startup Applications>Options>
```

Ok so if I unplug my computer from an internet connection, than those options will be SMART and not run anything that requires an internet connection???

I took a quick look, i don't see what you are talking about, and is this a user friendly way to implement the idea.

---

### Post by tad1073 on 2009-12-21
> **KrazyPenguin said:**
> Ok so if I unplug my computer from an internet connection, than those options will be SMART and not run anything that requires an internet connection???

I have no idea...

Just a suggestion...

> I took a quick look, i don't see what you are talking about, and is this a user friendly way to implement the idea.

or add the applications to the "Startup Programs"

---

### Post by KrazyPenguin on 2009-12-21
Another example of what I am talking about would occur with Thunderbird and multiple accounts.
If you have it start up automatically, and there is no connection, then there will be popups every saying that the connection for so and so wasn't found.

Then the user has to close all those popups and of course this doesn't look professional and takes away from the user experience.

A timed connection kind of works, but would still launch after that time if a wireless connection (or any connection for that matter including wired) wasn't found.

This is not smart on the part of the software.

Either this needs to be fixed at the program level where a program like thunderbird checks for an internet connection before checking for email, which makes more sense.  Or it is done automatically for the user through a program such as Network Manager.  That makes more sense to me.

Another example is firefox launching only if an internet connection is available.  I don't use  Firefox unless I'm using the internet, so why auto launch if not available??
And if 90% of the desktop experience is the internet then why not have those programs open automatically after a connection is found.
For most people using the computer means using the internet, especially for a desktop environment.

So we need to get people on the internet as fast as possible and that IMO is what the goal of Ubuntu should be.  Should be clean, good looking, and fast like ME!!!! LOL

---

### Post by KrazyPenguin on 2009-12-21
Here is what what Mandriva is doing, so I guess they have the right idea:

[http://distrowatch.com/weekly.php?issue=20091221#news](http://distrowatch.com/weekly.php?issue=20091221#news)

---

### Post by jpeddicord on 2009-12-21
I personally don't care for auto-launching applications anywhere, especially on a sketchy event like a network connection. I don't always want to open the same applications when I boot up my computer or change connections, and I really don't want my computer deciding what to do for me.
> **KrazyPenguin said:**
> Either this needs to be fixed at the program level where a program like thunderbird checks for an internet connection before checking for email, which makes more sense.
This is the real solution, and programs have already been doing this for a few releases. Examples: Firefox will stay in Work Offline mode if it sees that Network Manager does not have a connection and will go online when connected. Pidgin will set its status to "Waiting for connection" when not connected, and connect when ready. Empathy will automatically go online and offline as well.

So in terms of individual applications, this really already happens.

---

### Post by jpeddicord on 2009-12-21
> **KrazyPenguin said:**
> Here is what what Mandriva is doing, so I guess they have the right idea:

[http://distrowatch.com/weekly.php?issue=20091221#news](http://distrowatch.com/weekly.php?issue=20091221#news)

I don't see anything in there about this... all they are doing is working on a fast-booting OS and a Moblin port.

---

### Post by KrazyPenguin on 2009-12-21
> **jpeddicord said:**
> I personally don't care for auto-launching applications anywhere, especially on a sketchy event like a network connection. I don't always want to open the same applications when I boot up my computer or change connections, and I really don't want my computer deciding what to do for me.

This is the real solution, and programs have already been doing this for a few releases. Examples: Firefox will stay in Work Offline mode if it sees that Network Manager does not have a connection and will go online when connected. Pidgin will set its status to "Waiting for connection" when not connected, and connect when ready. Empathy will automatically go online and offline as well.

So in terms of individual applications, this really already happens.

It's customizable, so you could turn it off and on.
What do most people do???
Boot up their computer on go online, check facebook, and email.
Most aren't computer geeks, they don't program, they don't hang out at ubuntuforums.org.
If the internet isn't going in this direction, just look at the phones where people are "always on".   
There is always "cloud" computing, and again take a look at Ubuntu One.  In order to use it you "have to be online".
Also think about how important the internet was to ubuntu, how they wanted to make network manager easier to use.
Why is making things easier to use a bad idea???
I don't get it!?!??!?!?

---

### Post by jpeddicord on 2009-12-21
My point is, 99% of users would not use a feature like this unless it was already set up for them by default. If it was set up by default, then that 99% would complain about it. :P

---

