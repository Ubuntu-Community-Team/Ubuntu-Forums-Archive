---
title: "Can't install 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by eb sol on 2011-10-15
I've tried to install a fresh Ubuntu 11.10 on my HP All-in-One 200is , and nothing happens. It refuses to initiate.

First the purple screen appears, and I can see that the system is being loaded , then a black/blank screen comes after that. I can hear the sound when I press a button, but nothing on the screen.

I had this problem with the previous version, and I thought it will be fixed on the other one.

On this machine, I used ubuntu 10.04, and I'm now using 10.10 . I've been an ubuntu user since 4 years.. I don't know how to use other systems. So, I NEED YOUR HELP.. :(

related threads :
[http://ubuntuforums.org/showthread.php?t=1799791](http://ubuntuforums.org/showthread.php?t=1799791)

---

### Post by 2F4U on 2011-10-15
What are the specifications of your machine?
If it is a graphics issue, you could try to add nomodeset to the grub kernel boot parameters.

---

### Post by rajwarrior on 2011-10-15
> **eb sol said:**
> I've tried to install a fresh Ubuntu 11.10 on my HP All-in-One 200is , and nothing happens. It refuses to initiate.

First the purple screen appears, and I can see that the system is being loaded , then a black/blank screen comes after that. I can hear the sound when I press a button, but nothing on the screen.

I had this problem with the previous version, and I thought it will be fixed on the other one.

On this machine, I used ubuntu 10.04, and I'm now using 10.10 . I've been an ubuntu user since 4 years.. I don't know how to use other systems. So, I NEED YOUR HELP.. :(

related threads :
[http://ubuntuforums.org/showthread.php?t=1799791](http://ubuntuforums.org/showthread.php?t=1799791)



I had the same problem last night.

This is how I solved it:

I have just done an upgrade last night and was faced with a break and got almost similar situation with 300 odd held back packages.

Solved it by running sudo apt-get dist-upgrade

This throws up a sequence of errors showing 'unable to early remove' some packages.

Removed named packages one by one with sudo apt-get remove (and package name)

run sudo apt-get dist-upgrade after each package is removed. It will show some other problem.

One package gave greater problem - liblcms1. This needed me to remove the named java package when trying to remove it. Once done then all went well.

A good indicator is to see whether linux kernel 3.0.0 is being added to the boot list. Once that is done then restart should work.

BTW first boot does seem very slow. Rebooting after that works fine. 

Cheers

---

### Post by eb sol on 2011-10-15
> **2F4U said:**
> What are the specifications of your machine?
If it is a graphics issue, you could try to add nomodeset to the grub kernel boot parameters.

Thanks for the reply sir.. The There you go : [the specifications]("http://bit.ly/px7vbA")

I don't know how to add nomodeset to the grub kernel boot parameters ..
Thanks Again

---

### Post by eb sol on 2011-10-15
> **rajwarrior said:**
> I had the same problem last night.

This is how I solved it:

I have just done an upgrade last night and was faced with a break and got almost similar situation with 300 odd held back packages.

Solved it by running sudo apt-get dist-upgrade

This throws up a sequence of errors showing 'unable to early remove' some packages.

Removed named packages one by one with sudo apt-get remove (and package name)

run sudo apt-get dist-upgrade after each package is removed. It will show some other problem.

One package gave greater problem - liblcms1. This needed me to remove the named java package when trying to remove it. Once done then all went well.

A good indicator is to see whether linux kernel 3.0.0 is being added to the boot list. Once that is done then restart should work.

BTW first boot does seem very slow. Rebooting after that works fine. 

Cheers

I will do that , and see what happens ,, Thanks Champ

---

### Post by eb sol on 2011-10-23
> **rajwarrior said:**
> I had the same problem last night.

This is how I solved it:

I have just done an upgrade last night and was faced with a break and got almost similar situation with 300 odd held back packages.

Solved it by running sudo apt-get dist-upgrade

This throws up a sequence of errors showing 'unable to early remove' some packages.

Removed named packages one by one with sudo apt-get remove (and package name)

run sudo apt-get dist-upgrade after each package is removed. It will show some other problem.

One package gave greater problem - liblcms1. This needed me to remove the named java package when trying to remove it. Once done then all went well.

A good indicator is to see whether linux kernel 3.0.0 is being added to the boot list. Once that is done then restart should work.

BTW first boot does seem very slow. Rebooting after that works fine. 

Cheers
[B]
Doing this may only update the system, and usually this creates some problems..

So,

is there any way to install a fresh version of ubuntu ? :(

HELP ANYONE ,,[/B]

---

### Post by Quackers on 2011-10-23
Instructions here

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by eb sol on 2011-10-25
> **Quackers said:**
> Instructions here

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


Thank you sir very much ,, problem solved,, Cheers mate .. :popcorn::popcorn:

---

