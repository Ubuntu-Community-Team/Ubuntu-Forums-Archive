---
title: "Can / should I encrypt my /home?"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-04-15
Hi,

In earlier alphas of Intrepid, you had the option to use an encrypted home directory:

[IMG]http://2.bp.blogspot.com/_-mej0A6dVeU/Sahv4yrc2QI/AAAAAAAAAN8/s2J-fJ7Ne7w/s400/desktop.png[/IMG]

I think this has removed in more recent installers, but... can I still do it? and is it a good idea? Imagine I install my /home to a different partition, and then after some time try to re-install the system. How can I get the new install to recognise my old /home then?

EDIT: It seems it IS [possible]("http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html"):

> Boot the LiveCD installer, and preseed a special value:

    * Select your language
    * Press F6
    * Then ESC
    * Add "user-setup/encrypt-home=true" just before the "--".

However, the second question still stands. If I do it and re-install, how will I recover my data? Also, does it take a toll on performance?

---

### Post by gnomeuser on 2009-04-15
I use dm-crypt to do full encryption then I layer the encryptfs on top. This is because I don't really fully trust the implementation in encryptfs and I like to have my swap encrypted to since that is vital to good security.

As for the overhead, in normal desktop use I don't feel it at all. When doing writes considering you have to encrypt everything that does take a hit. I would wager any normal user would be blissfully unaware of it in daily use.

---

### Post by Nullack on 2009-04-15
Personally I dont bother. I dont have any sensitive information on my test systems and I dont want the performance overhead of it.

---

