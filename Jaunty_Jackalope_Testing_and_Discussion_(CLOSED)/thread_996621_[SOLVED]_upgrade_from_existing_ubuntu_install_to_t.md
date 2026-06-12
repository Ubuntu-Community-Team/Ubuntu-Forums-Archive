---
title: "[SOLVED] upgrade from existing ubuntu install to testing possible"
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cmay on 2008-11-29
hi.
i have wanted to test jaunty and burned a pair of cd but the disks turn out corrupt. the langauge pack for gnome has a wrong md5 sum i cant install from them. i try one more fresh iso then i am out cd. can i upgrade to testing from hardy or intrepid. over the internet.
thanks.

---

### Post by autocrosser on 2008-11-29
Well at this point you could just change all your sources from intrepid to jaunty or try a sudo update-manager -d

Things are not changed enough from Intrepid at this point to really have "too" many problems......that being said--the first minor breakage was yesterday---was a easy fixed break....

I would expect quite a bit more breakage after the UDS--the run to alpha 3 should be fun :)

---

### Post by cmay on 2008-11-29
thanks. i am going to have to try that. i have for some reason  very very much problems getting a iso file that is not corrupted or an cd that can install with ubuntu. the last 3 times i have installed ubuntu it cost me more than 7 cd to get it burned. i found out that there is a shop that has burned cd so i have to buy them now. all ohter cd i burn works fine. anyway i am going to install jaunty over internet from hardy on my old computer i use for beta testing.

thanks for the time.

---

### Post by ktp on 2008-11-29
I always have CD+RW for these things.  I have seen bad burns when burnning full speed..so I try to burn at little lower speed.

---

### Post by Gina on 2008-11-29
I found DVDs more reliable than CDs generally, though a brand new multi-format drive works well enough with either.  I use DVD+RWs for testing.  And DVDs are faster than CDs.

---

### Post by ktp on 2008-11-29
Yes I agree...DVDs are great this days...got few of them also since most of the good stuff takes a DVD now.

---

### Post by dakkar9999 on 2008-11-29
> **autocrosser said:**
> Well at this point you could just change all your sources from intrepid to jaunty or try a sudo update-manager -d

Things are not changed enough from Intrepid at this point to really have "too" many problems......that being said--the first minor breakage was yesterday---was a easy fixed break....

I would expect quite a bit more breakage after the UDS--the run to alpha 3 should be fun :)

Yes, I did the upgrade path instead of the CD and it worked fine.  Plus saved burn coasters!

---

### Post by agurk on 2008-11-29
The CD images are currently oversized, hence the clear warning written in red letters...

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by autocrosser on 2008-11-29
> **dakkar9999 said:**
> Yes, I did the upgrade path instead of the CD and it worked fine.  Plus saved burn coasters!

Glad to be of help---Make sure you backup regularly--we had a minor bump a couple of days ago that was a "gentle" reminder--I was out of my main testing install for several hours whilst everyone looked for the problem--froze the desktop due to a gtk update.

---

### Post by dakkar9999 on 2008-11-29
Well, this install is just to play around.  No real sensitive info in there.  Not too worried as long as it doesn't crash and burn my other drives... :-)

---

### Post by cmay on 2008-11-30
i really really really need to get a new dvd-drive :(

but i been playing around with the sources list and i cant get it to accept it. 
how should it look exactly ?.

---

### Post by Eclipse. on 2008-11-30
> **cmay said:**
> i really really really need to get a new dvd-drive :(

but i been playing around with the sources list and i cant get it to accept it. 
how should it look exactly ?.

Replace "intrepid" in your sources.list with "jaunty" then run "sudo apt-get update && sudo apt-get upgrade"

OR

Run "update-manager -d" from a terminal.

Before you go any further, things will break and blow up and eat babies so when it happens...dont complain!:lolflag:

Also you should have a look at this thread: [http://ubuntuforums.org/showthread.php?t=996538](http://ubuntuforums.org/showthread.php?t=996538)


ps..the alternative cds will fit onto a cd: [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by cmay on 2008-11-30
> 
OR

Run "update-manager -d" from a terminal.this i already tried and it wont work. i try this source replacement scheme instead..

ps
i use a computer that is for testing so as long as it do not blow up i care less about some breakage. i still have a stable set up. in fact i am going to try break something if i can :)

---

### Post by cmay on 2008-11-30
ok. 
i am about to reboot into jaunty now. 
wish me good luck. :)

---

