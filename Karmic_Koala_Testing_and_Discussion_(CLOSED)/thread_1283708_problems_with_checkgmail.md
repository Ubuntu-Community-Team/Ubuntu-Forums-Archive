---
title: "problems with checkgmail"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-10-05
after last set of updates program checkgmail asks for my user name and password then after i enter and hit save goes into loop and repeats same. anyone else or just me

---

### Post by VMC on 2009-10-05
The only time I had a program with gmail that resembles what you described was when I had a weak password.

---

### Post by dreamersbrow on 2009-10-05
I can confirm this error.

---

### Post by Giannis M. on 2009-10-05
Same here

---

### Post by holysmokes on 2009-10-05
I am having the same problem. I did an update.. and whamo. It keeps prompting me for a password.. and after a while I get a 401 unauthorized error. Double checked passwords.. I'm A-OK. No problem logging into gmail from firefox, and my account has not been compromised.. I use really strong generated passwords. Changed them anyways.. Still, checkgmail will not function. Then I attempted to run the program from the terminal command line.. and I get this suspicious error message, and the program even freezes up terminal too.. Here is the error:

Use of uninitialized value in subroutine entry at /usr/share/perl5/Crypt/Simple.pm line 144.


Then it freezes.. I have to do a hard exit on the terminal window to stop the freezing.. :confused:
Did google change their services again to prevent atom browser functionally
for non-proprietary atom browser users? Or did that update just kill our checkgmail? 

I did a reboot on my system and now my boot up graphical window is messed up looking, and the red progress line has moved itself to the lower left hand corner of the ubuntu window..  It reminds me of a virus on windows.. EEKK!! .  This is REALLY STRANGE.. :(

---

### Post by holysmokes on 2009-10-05
And forgot to mention, I'm running 9.04 Ubuntu.. Not the alpha.. :(

---

### Post by holysmokes on 2009-10-05
Okay, now the other problem is gone after another reboot, except checkgmal still won't work normally anymore. I can force it to work when I disable cookies fro the command line..  In Terminal: 

checkgmail -no_cookies

And now it works again. Hy head hurts.. :confused:

---

### Post by dreamersbrow on 2009-10-05
It appears that I am also having the same problem on another machine that I have NOT done any updates on and is running 9.04.  Perhaps Google has made a change.

---

### Post by holysmokes on 2009-10-05
Yes, this looks like a google issue.. The error I was getting was when I trying to start checkgmail from the command line while it was already running..  Everything was working fine this afternoon though. :( The last thing that happened was about 2 hours ago I did a reboot after those updates came down the pike, and then checkgmail started kicking back that 401 error..  I'm just going to run it without the cookies for now.. Thanks.

---

### Post by holysmokes on 2009-10-06
I'm going to change the MAC address in my router to get a different IP address with my dynamic IP connection..  and see that might fix the problem for a while..  I'll be right back.. :popcorn:

---

### Post by holysmokes on 2009-10-06
Yes changing your IP will fix it, if only temporarily (who know!?!). Here is what I just did to get checkgmail to work again :KS:

I uninstalled checkgmail first.. Then I changed the mac address on my router, and then did a power cycle on my cable modem, and then the router itself. Then I checked for connection to the INTERNET. and now have new IP address for my modem, I then reinstalled checkgmail..  And it wouldn't work at first (it fought me at first).. I got some wierd 443 error, and quickly stopped it from checking for a moment, then I opened my gmail from within Firefox. And then I restarted checkgmail again.. Now it works like it did earlier this afternoon. I bet if I restart my computer it will not work.. (just a hunch) 

You'll have to mess with it for a while.. There are lots of possible things that Google might have done to cause this..  It could be a capcha issue with checkgmail itself.. or it could be something google is doing to keep someone from an IP to automatically login after a certain period of time.  If you have a static IP, then I would imagine this will not work for you folks.. Anyone have a suggestion for people with static IP's that can't be changed??? :lolflag:

---

### Post by xfalcox on 2009-10-06
Installed now, and working well!

---

### Post by MacUntu on 2009-10-06
If this happened after an update it's unlikely that Google is to blame. ;)

I guess you'll see the 401 just for security reasons after unsuccessfully trying to log in too many times. Should work with the same IP after a while.

---

### Post by Elswood on 2009-10-06
I also am suddenly having this same problem on two 9.10 beta machines and one 9.04 machine. Google is the target of a phishing attack and may have changed permissions.  I changed my google password because of the attack report and CheckGMail won't log on although I can log on through firefox, etc.  Maybe Google has borked CheckGMail in defense against the phishers.  See this: [http://news.bbc.co.uk/2/hi/technology/8292928.stm](http://news.bbc.co.uk/2/hi/technology/8292928.stm)
I really liked using CheckGMail but will abandon it shortly if it no longer functions!!!

---

### Post by MacUntu on 2009-10-06
**Edit:** Sorry, cannot confirm it, my code had a bug. Ubuntu's checkgmail (1.13+svn37-1) works fine here.

---

### Post by MacUntu on 2009-10-06
[https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/433497](https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/433497)

[http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947/index/page/1](http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947/index/page/1)

---

### Post by Rob-e on 2009-10-06
Updating (by running sudo checkgmail -update) didn't fix it for me, but changing my WAN IP it fixed it, Great Job!

---

### Post by holysmokes on 2009-10-06
Yeah, updating checkgmail when it is it already busted and giving you a 401 doesn't work at all.. I can confirm that. Right now, as of the last IP change, my checkgmail is still working. I'm very happy with it again.  Google was probably trying to cover up the fact that these lists were made public, not to freak out everyone. I read the BBC article about the compromised passwords for certain account of their's listed in that report, and what I believe to be true is that, my own account was probably listed and they responded by making me manually enter in my password (still that is a hunch, but it's a good hunch afaik) .. And so, I highly recommend anyone who uses gmail, yahoo, or hotmail to change their passwords immediately, just to be on the safe side, even though google doesn't want to face up to their customers about it. And just so you know, if my checkgmail stops working again, I will return here to post an update as well..  Cheers. 
:guitar:

---

### Post by holysmokes on 2009-10-06
Awww.. Check it out.. Thanks alot google.

[http://mashable.com/2009/10/06/gmail-accounts-exposed/](http://mashable.com/2009/10/06/gmail-accounts-exposed/)

They could send out a mass email global message letting us know
just exactly what changes they are making in our behalf, right? 
Ugh..  If I get one more problem from google again, I'm going
to restart using my paid POP mail service and use Thunderbird
instead of web based securityless jokes like gmail...  This is nuts.. :confused:  
The developer of checkgmail is like - I'm audi5000 folks! See ya! 
I would be too when google just bails on their users
like this, and does security changes without notifications..  
Users to need to know in advance of changes like what google
just did.. 

How frustrating is that? 

[http://www.bilal.ca/google-fail-gmail-aol-yahoo/](http://www.bilal.ca/google-fail-gmail-aol-yahoo/)

Oh well.. Cheers

---

### Post by MacUntu on 2009-10-06
Don't miss this:

> They also stress that it&#8217;s not a breach of security, but the result of certain users falling for phishing scams.

I can only speak for myself - I don't fall for phishing. ;)

---

### Post by holysmokes on 2009-10-08
Uh.. yeah.. phishing scam.. yeah, right. and then they woke up from that nice dream Google was having..  The number one reason I suggest for people to use Ubuntu over every other reason that I know of to tell anybody, is just one thing, security. I will never go back to windows or anything else for that matter simply for the fact that I truly know I am safer by using this operating system. If you use it too, and Google wants you to believe it is a phishing scam perpetrated again you the linux user, which caused these lists to exist in the first place, and that's why you couldn't use checkgmail because your IP was blocked by them as a "quiet" and "precautionary" security measure, that is a complete crock of horsepucky and I would even go one step further, and ask myself if I were you, how -really- bad was this security breach, and exactly how many people have now been totally compromised, from users of their google desktop applicaiton to their records that contain everything about someone's personal identity, and google never deletes any information they retrieve of their users. Most users who can step back for a moment, and just see it for what it is, it is a catastrophe in the making; if not this week, eventually and especially if they will cover up security issues like they have been experiencing for the last few weeks without informing their commercial audience. Shame on Google, and for driving the creator of checkgmail crazy with these sneaky handling of this problem they obviously covered up to try to save their stock price from plummeting.

---

### Post by TonKi on 2009-10-08
had the problem too, removed the config and everything works again.
rm -rf ~/.checkgmail

---

### Post by ricsi-pontaz on 2009-10-08
> **TonKi said:**
> had the problem too, removed the config and everything works again.
rm -rf ~/.checkgmail

Yes, it's works for me too. Thanks.

---

### Post by Aviendha09 on 2009-10-14
Same problem, started 2 days ago. Using no_cookies makes it work, but....removing configuration did nothing.

I am writing from my still existing Jaunty installation, installing in Karmic coming up soon.

Whoa! What happened to all my sexy settings? (delete, mark as read and clickable urls)This is not-good!

---

### Post by polki@mac.com on 2009-10-15
I used the checkgmail -update and nothing. Then I did it again and actually typed the "Y", which looks very much like default in the "Y/n" dialogue, when asked. Worked after that...

---

### Post by EricDB on 2009-10-15
> **polki@mac.com said:**
> I used the checkgmail -update and nothing. Then I did it again and actually typed the "Y", which looks very much like default in the "Y/n" dialogue, when asked. Worked after that...

Awesome!  That cleared it up for me.  That prompt is definitely wrong:
```
OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)>
```

You shouldn't have to type 'Y', but that's the only way it works.  Thanks!

---

### Post by rburkartjo on 2009-10-16
finally working not sure what fixed it followed all advise on thread plus some messing around by myself

---

### Post by Aviendha09 on 2009-10-16
Yep that ambiguous update dialog whas the obstacle...Fixed, sexy and everything back to normal...phew! soon to test on KARMIC, (halfway installed, needs the sexy tweaking)

---

### Post by oboedad55 on 2009-10-16
> **holysmokes said:**
> Okay, now the other problem is gone after another reboot, except checkgmal still won't work normally anymore. I can force it to work when I disable cookies fro the command line..  In Terminal: 

checkgmail -no_cookies

And now it works again. Hy head hurts.. :confused:

I just changed the menu item to reflect this change and all is well. Thanks for the info! BTW, I just tried the update with the same results, but the kludge works.

---

### Post by EricDB on 2009-10-17
The problem with the "-no_cookies" method is that you can't archive, mark read, or do anything else from the tooltip.  That's a big part of what makes CheckGmail so great for me.

---

### Post by oboedad55 on 2009-10-17
I don't know what's going on. I did the update again and now it seems fine. Computers...

---

### Post by Aviendha09 on 2009-10-17
I did the update after installing on Karmic (allright! Sexy settings are *included*, yes!) and everything was fine, but of course stuck in terminal. So I closed and restarted, and The Problem showed up: no login! I restarted no_cookies and logged-in, but *no sexy*! Arrg! 

Then I linked the new (perl?) script I found in my ~/bin to the /bin folder (Q: is this un-secure?) and restarted (thru alt-f2) and Voilà! It's all allright! CheckGmail rocks! :guitar:

(more than halfway to Karmic now...)

---

### Post by nc_jed on 2009-10-22
> **EricDB said:**
> Awesome!  That cleared it up for me.  That prompt is definitely wrong:
```
OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)>
```

You shouldn't have to type 'Y', but that's the only way it works.  Thanks!

triple on the manual typing of 'Y' at the prompt.  Problems a'plenty up until that.

-- Jed

---

### Post by nixie21 on 2009-10-23
Am I missing something...it works getting email and letting me archive or delete, if i click the icon to open gmail in firefox, i have to type in the pw at gmail...

---

### Post by holysmokes on 2009-10-23
> **nixie21 said:**
> Am I missing something...it works getting email and letting me archive or delete, if i click the icon to open gmail in firefox, i have to type in the pw at gmail...

Affirmative. 

I can confirm this error after doing the update as well. 

It seems whenever I click on the checkgmail taskbar icon to open up gmail
I am stopped at the login in my browser window, and have to manually enter my password
over and over each time I click on the taskbar icon. And when I do finally open gmail
I find the message I was notified about has already marked as read, as if I didn't receive
a password prompt at the gmail login window, and had gone straight
to the email message waiting for me in my inbox. 

Odd. 

I think Google has changed something... without telling anyone about it. :confused:

---

### Post by DizzyC on 2009-10-26
> **nixie21 said:**
> Am I missing something...it works getting email and letting me archive or delete, if i click the icon to open gmail in firefox, i have to type in the pw at gmail...

Yeah! Same here. It's annoying. Google is starting to piss me off Microsoft style... :(

---

### Post by Proton Soup on 2009-10-26
> **DizzyC said:**
> Yeah! Same here. It's annoying. Google is starting to piss me off Microsoft style... :(

i finally got it to appear to work with the no cookies option.

i'm thinking maybe google wants people to be signed in all the time.  not having peoples' searches associated with a username kind of defeats the purpose of giving out free email to datamine users.

---

### Post by chitresh4u on 2009-10-26
I have updated checkgmail. But seems to work only with -no_cookies option. Without this option checkgmail is showing error 500:cannot connect to google.co.in:80(Connect: connection refused).

Any workarounds? checkgmail is almost useless without option like mark as read, delete etc..

---

### Post by holysmokes on 2009-10-27
I changed in checkgmail preferences (command to execute
on clicking the tray icon) to this: 

firefox [http://mail.google.com/mail/#inbox](http://mail.google.com/mail/#inbox)

And so now I have fixed the issue.. And you guys
are right I have to be logged on all the time to gmaiil
for it to work.. But checkgmail is back to working as originally..

On a side note, I'm testing karmic, and if you are running 64 bit
and like adobe flash video,  flash videos are looking flawless now..  its not
choppy anymore with nvidia cards.. they finally fixed it. :D

however there is an bug with the kernel with nvidia users and
64bit, and something to do with memory bios ecc settings (on or off?).. 
I sure hope they fix this because they are going to have thousands
of users bitching about this in a few days time when this is officially
released.  I get like 3 crashes each time I boot up.. but they are just
annoying mostly. :(

It's looks like this in case you would like to see what I am talking about: 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1797674.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1797674.html)

Otherwise Karmic is awesome. \\:D/

---

