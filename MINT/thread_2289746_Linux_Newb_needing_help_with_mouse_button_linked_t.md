---
title: "Linux Newb needing help with mouse button linked to Passwords"
date: 2015-08-06
forum: MINT
---

### Post by Nick_Otto on 2015-08-06
I have been working towards getting myself moved from windows 7/10 to linux mint 17.2 x64.  No real issues with windows other than the looking over your shoulders and so forth, but it is time for a change.

I have gotten all my required apps worked out except one.  

I wear a lot of hats at my job.  I manage a hyper v server cluster for the company I work for and spend my days logging into and out of many different machines / shells / internal webpages / shares, with more than one username to do multiple tasks on the network.   As I am sure a lot of you know that means I have 7 different passwords 3 of which I use daily about 40 or 50 times throughout the day.  A typical password manager won't work ( that I know of) due to logging into the same ip/dns multiple times with different users etc.  

I had gotten used to it, but then I stumbled upon the Logitech G series mouse.  Their windows software allows me to record keystrokes and assign them to a button on the mouse.   I had my 3 more common users/ passwords assigned to 3 different buttons.  Needless to say this saved me a TON of time throughout the day, not to mention the frustration of my fingers not hitting the right key etc.  

In the below example the macro was set for entering and username then tabbing and entering a password.  In this case user is "123" and Pass is "123"
[[IMG]http://i879.photobucket.com/albums/ab360/me78569/Capture_zpsukbgc4os.png[/IMG]]("http://s879.photobucket.com/user/me78569/media/Capture_zpsukbgc4os.png.html")

I have read and read and read, tried multiple different apps without luck.  I have tried btnx , xev for mapping, gestures , autokey, etc etc but I can't seem to reproduce this function.  

Any thoughts on this?  Doesn't have to be assigned to a button on the mouse, I am fine with a keyboard key combo IE: "alt+a" =user/pass 1 

Thanks

Nick

---

### Post by howefield on 2015-08-06
Thread moved to the "*MINT*" forum.

---

### Post by TheFu on 2015-08-06
Using a mouse for password replay is completely inappropriate, and insecure.
Use a better password manager where you control when the fill-in happens. KeePassX is one like that. It doesn't auto-fill in passwords - you have to tell it when to type.

BTW, if you are using passwords to login to systems, you have already failed from a security perspective. You should be using keys and PKI.  Fire your security team, they have failed.

---

### Post by Nick_Otto on 2015-08-06
Thanks for the heads up on Keepassx.

---

### Post by tomasrey88 on 2015-08-10
Oh, man, a mouse app for passwords?! Please do not tell me where you work or I may be tempted.... 

Let me put it to you this way, a modern computer can crack a password very easily with brute force, even more easily if the password's length is known and you've used words that you can find in an online repository such as; dictionary, phone numbers, zip codes, area codes, common passwords (m0misgr8, bestg1rl, etc). The only passwords that are not hackable have to be 40 to 50 characters long, made of random numbers, letters, capitals, small case, and symbols. 40 characters to be impervious to private sector password cracking and 50 characters to be impervious to state level password cracking. 

To save passwords as a mouse stroke, it can be hacked by an antique pentium computer in a second. 

To save time not having to type passwords, try a physical key. In lieu of a physical key, you'll have to use 40-50 character passwords. Hardware key that unlocks software: 
 [http://www.matrixlock.de/english/index.htm?gclid=CIPBz7PRnccCFQ-raQodAtEGtw](http://www.matrixlock.de/english/index.htm?gclid=CIPBz7PRnccCFQ-raQodAtEGtw)

I think they're made in Germany? And for some odd German reason, they call them "dongles" instead of keys. So, just do a Startpage search engine search for "dongles". Many companies sell / manufacture these "dongles". 

This password analyzer will tell you exactly how many hours (or days) it will take to brute force your password. Don't type your actual password into the analyzer for obvious reasons. Just type a very similar password to your actual password. 
[URL="http://www.passfault.com/"]http://www.passfault.com/
[/URL]
Shameless Plug, answer my question please: 
[http://ubuntuforums.org/showthread.php?t=2288606](http://ubuntuforums.org/showthread.php?t=2288606)

Thanks!

---

### Post by TheFu on 2015-08-10
tomasrey88 - do you have sources for the 40+ statement?  

Last time I spoke with professional password cracking teams, they were stuck on random 16 character passwords. Adding 1 more random character from a 96 character alphabet makes a password exponentially harder.  Of course, these must be random characters - not words to add length. OTOH, any 12 character password was crackable in 24 hours with about $2K in equipment.  

Did something change recently with password attack technology?

BTW, there are multiple methods for non-password authentication. gpg-keycards tends to be the most popular in a corporate environment. For home users, there is ubikey. Sadly, most of these things are just too hard for most home users to use effectively or to setup without making a security-sucking mistake.  It is generally accepted that if you are using a password as authentication, you've already lost the battle.

I looked over your other question - seems answered to me.

---

### Post by tomasrey88 on 2015-08-10
The problem with random character passwords is that nobody uses them because humans have problems remembering them. Even seemingly random yet easily remembered passwords are on most hackers' lists of passwords that can be recombined by a computer for guesses of longer passwords. Given the right algorithm, you can use a computer to guess almost any password that can be remembered by a human. I have personally witnessed a gpu cluster hack a complex 20 character strong password in a matter of hours at a technology convention. They use similar rigs to that used in bitcoin mining. Using liquid cooled rigs gpu clusters, Mind you, professional (not hobbyist) bitcoin mining rigs now are capable of petahashes of computing power and consume megawatts of electricity. They generate millions of dollars worth of bitcoin per month. Yes, it is possible to crack very strong <40 character passwords, but if it is memorizable by a human, then it could be hacked, but it would take hundreds of thousands of dollars to hack, in TODAY"s computing power due to the lost opportunity cost of not bitcoin mining due to the computer hacking a password instead. Governments have more computing power than even the bigggest bitcoin mining rigs and can hack <50 character passwords. 

In other words, with today's technology, you can protect $200,000 with a 40 character password and a 50 character password can protect millions. Anything more valuable than that, I wouldn't protect with any password. Use a dongle guarded by a battalion of troops on a system with zero internet access. That's what uncle sam does.

btw, use what "the fu" suggested that i wasn't aware of:  **gpg-keycards tends to be the most popular in a corporate environment. For home users, there is ubikey.**

---

### Post by CantankRus on 2015-08-10
This may be of interest to you.
I use a python script to save and retrieve passwords in seahorse.

I can then use the script with easystroke and xdotool to print my admin password when needed
with an assigned mouse button or gesture.
What I like about seahorse is you can only access it when graphically logged in.

You can install the python script using [**_[COLOR="#B22222"]pip[/COLOR]_**]("https://python-packaging-user-guide.readthedocs.org/en/latest/current.html").
```
sudo apt-get install python-pip
```

Install gkeyring...
```
sudo pip install gkeyring
```
**More info----->** [http://ubuntuforums.org/showthread.php?t=2125918](http://ubuntuforums.org/showthread.php?t=2125918)

---

### Post by TheFu on 2015-08-10
I'd really like references for the current cracking performance.  
 
[https://www.schneier.com/blog/archives/2014/03/choosing_secure_1.html](https://www.schneier.com/blog/archives/2014/03/choosing_secure_1.html) is a good intro from a reputable source in the security community. He actually wrote the book on security - literally.

The old XKCD meme for passwords doesn't work anymore. [http://xkcd.com/936/](http://xkcd.com/936/)

Always lie in those password reset questions.

Here's a password cracking class video from May 2015: [https://archive.org/details/ISSAKentuckianaPasswordCrackingClass](https://archive.org/details/ISSAKentuckianaPasswordCrackingClass) If you are into security training - Adrian (IronGeek.com) has been cataloging conference videos for years. Haven't watched it myself yet. 

Bitcoin mining gets harder and harder. I don't think **anyone** is making millions of BTC in a month. According to [https://blockchain.info/charts/total-bitcoins?showDataPoints=false&timespan=30days&show_header=true&daysAverageString=7&scale=0&address=](https://blockchain.info/charts/total-bitcoins?showDataPoints=false&timespan=30days&show_header=true&daysAverageString=7&scale=0&address=) - in the last month, about 100K in new bitcoins have been created/calculated world-wide. 

Anyway - there is much to learn, much to re-learn and much to know related to all of this stuff.

---

