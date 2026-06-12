---
title: "Black screen when I try to install"
date: 2016-10-31
forum: Installation &amp; Upgrades
---

### Post by vasskalinin on 2016-10-31
My computer's processor (AMD E1 2500 1.4 GHz) is very very limited and slow, and according to what I googled, the best options for me are installing Xubuntu or Lubuntu. I decided for Xubuntu and tried both 16.04.1, 16.04 for 64 bits AMD via USB or DVD, burning with x4. It only shows a screen with few options like installing or using without installing, but whenever I choose any of them, it turns completely black and stays there. Why should I do?

---

### Post by Bashing-om on 2016-10-31
vasskalinin; Hello; Welcome to the forum.

A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a black screen or show corrupted splash screen. See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter .

Once the operating system is installed, then an appropriate driver can be installed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by vasskalinin on 2016-10-31
> **Bashing-om said:**
> vasskalinin; Hello; Welcome to the forum.

A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a black screen or show corrupted splash screen. See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter .

Once the operating system is installed, then an appropriate driver can be installed.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
 I added the nomodeset parameter, but I'm still getting the same black screen :/

---

### Post by Bashing-om on 2016-11-01
vasskalininl Well ...

Now it has become a head scratcher.

1st up is can you boot the installer - live l/xubuntu in the "try ubuntu" mode?
As It is no !!
> 
It only shows a screen with few options like installing or using without installing, but whenever I choose any of them, it turns completely black and stays there.

Then is this a old laptop OR desktop machine; laptop  such that perhaps ACPI settings plays into this ? 
Did you verify the .iso file ? 
Did you verify that copy as an image to the install medium ?

Let's find what it takes to boot up " try ubuntu" .

[INDENT][INDENT][INDENT]get a firm footing
[INDENT][INDENT][INDENT][INDENT]and push
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vasskalinin on 2016-11-01
> **Bashing-om said:**
> vasskalininl Well ...

Now it has become a head scratcher.

1st up is can you boot the installer - live l/xubuntu in the "try ubuntu" mode?
As It is no !!

Then is this a old laptop OR desktop machine; laptop  such that perhaps ACPI settings plays into this ? 
Did you verify the .iso file ? 
Did you verify that copy as an image to the install medium ?

Let's find what it takes to boot up " try ubuntu" .
[INDENT][INDENT][INDENT]get a firm footing[INDENT][INDENT][INDENT][INDENT]and push
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

  
Nevermind. I had the option "secure boost" activated. I'm typing from xubuntu :)

---

### Post by Bashing-om on 2016-11-01
vasskalinin; Good deal ..

Let us know how goes, and when installed remember:
mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

