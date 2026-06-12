---
title: "Using wubi and no luck installing.  Screen goes weird."
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by jameslcrabtree on 2012-03-29
Hello.  I am really looking for some help from the sages.  Here is my situation:

I had the fortune of getting an old computer circa 2004 a few days ago from a friend that had it sitting in his closet.  I was able to reinstall XP just fine, but my goal has been to make it my personal Linux box.  However I am not have any luck getting any distro I ahve tried on this computer and have gone through four DVD-Rs and formatting of the same flash drive about four times as well.


I have tried everything I can think of and been trolling this forums for a couple days and cannot find a resolution.  I have tried booting Ubuntu, Kubuntu, Lubuntu  and Mint from discs and no luck. The last straw before coming to this forums is that this happens:

I rig wubi to install Lubuntu as a dual boot, I get the Boot from CD propmt I set into BIOS.  However after it starts installing, the screen goes all weird.  I get no prompts and the screen fades in different places.  


I can post and specs if requested.  Maybe this computer is too old (has 512 MB ram), but something isnt right.

Suggestions?

---

### Post by Rex Bouwense on 2012-03-29
With only 512 Mbs of RAM, Ubuntu might be a problem.  However, installing Lubuntu should be a snap.  You can install Lubuntu directly without using WUBI if you want.  WUBI is generally used by people who are trying out an OS and still want Microsoft Windows.  It is much easier to install direct rather than doing it inside of XP with WUBI.  That will still give you the dual boot option.
Did you download the distos that you are trying out?  If you did did you check the md5sum of each download and then burn the image at the slowest possible speed.  That gives you the best chance of having a good burn.

---

### Post by critin on 2012-03-29
> **jameslcrabtree said:**
> Hello.  I am really looking for some help from the sages.  Here is my situation:

I had the fortune of getting an old computer circa 2004 a few days ago from a friend that had it sitting in his closet.  I was able to reinstall XP just fine, but my goal has been to make it my personal Linux box.  However I am not have any luck getting any distro I ahve tried on this computer and have gone through four DVD-Rs and formatting of the same flash drive about four times as well.


I have tried everything I can think of and been trolling this forums for a couple days and cannot find a resolution.  I have tried booting Ubuntu, Kubuntu, Lubuntu  and Mint from discs and no luck. The last straw before coming to this forums is that this happens:

[COLOR=Red][B]I rig wubi to install Lubuntu as a dual boot, I get the Boot from CD propmt I set into BIOS.  However after it starts installing, the screen goes all weird.  I get no prompts and the screen fades in different places.  
[/B][/COLOR] 

I can post and specs if requested.  Maybe this computer is too old (has 512 MB ram), but something isnt right.

Suggestions?


[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

What do you mean by "rigging wubi"?  If you download wubi, you will choose your version of OS and it will do the downloading and installing of the OS.  You don't have to burn it to cd's if you do it with Wubi.
It sounds like you're trying to burn and boot from the cd in order to install it.

512 ought to run a light version okay.  It's always better to have more, but it will work.  The latest ubuntu requires more.

---

### Post by bcbc on 2012-03-29
What graphics card does it have? If it's ATI or Nvidia you should use 'nomodeset' to boot first time: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (post 8 is wubi specific, but you can just boot a CD in live mode and see whether that helps based on the instructions in post #1)

---

### Post by jameslcrabtree on 2012-03-29
[SIZE=2][B]nomodeset did it!   thank you guys so so much!   I feel stupid now :(
[/B][/SIZE]

---

