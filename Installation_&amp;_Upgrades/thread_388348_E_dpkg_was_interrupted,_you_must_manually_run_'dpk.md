---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the.."
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by utnubu1 on 2007-03-19
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

when i do apt-get upgrade i get this error, i can do apt-get update but not upgrade, i also cannot install packages through apt-get or aptitude

Any Ideas???

---

### Post by Arby on 2007-03-19
Have you tried doing what the error message suggests and running the dpkg command? Type the following at the commandline ```
sudo dpkg --configure -a
``` Enter your password when prompted. Then try ```
sudo apt-get update
followed by
sudo apt-get upgrade
``` If you've already tried this or you try it now and it isn't working then post the full output from apt-get here.

What package was being installed when apt-get failed? You should be able to see this in the output just prior to the error message you've shown.

---

### Post by waveslider on 2007-03-19
I am having the same problem. I did what you suggested (i.e ran sudo apt-get update & then sudo apt-get upgrade).

I got the following error messages:

After running sudo apt-get update:
Could not connect to wine.lowvoice.nl:80 (81.171.111.184), connection timed out
Some index files failed to download, they have been ignored, or old ones used instead.


After running sudo apt-get upgrade:
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


I don't know what to do to fix this. Can anyone please help me?

Thanks!

---

### Post by utnubu1 on 2007-03-19
Yes that fixed it

i did try sudo dpkg --configure -a before but it just came up with
> 
but if you put apt-get update it works

it also might have been that i unticked the wine packages from the sources list

---

### Post by Arby on 2007-03-19
It looks as if there is a problem with the Wine website where the packages are downloaded from. I've just tried to get to that site and I am unable to load the pages. So it seems like their site may be down.

utnubu1: glad you got it fixed. I suspect that unchecking the wine packages may have been the key. Although you'd probably still have needed the dpkg command to clear the errors

waveslider: 

It looks like your problems may have the same source. I don't know what virtualbox is. I would try using Synaptic to do your upgrade. I use kde so I'm not that familiar with Synaptic but there should be a preview changes button or similar to show what upgrades Synaptic is about to make. Have a look at that list and remove any wine packages. Then try doing your upgrade.

If you have trouble you might need to run the dpkg command I gave earlier to 'reset' apt-get then try again. If you still have trouble then post the full output from apt-get and we'll have another look

Arby

---

### Post by Styopa on 2008-04-22
One question, and I'm sorry if this is really obvious, but when you have an error message like "you must manually run 'dpkg --configure -a'"

..wouldn't it make sense to say "you must open terminal and run 'sudo dpkg --configure -a' " instead?

I mean, I'm a complete ubuntu n00b, and how would I know that I'm supposed to type 'sudo' in the command line before a command?

---

### Post by Martje_001 on 2008-04-22
Styopa: Correct! You have to typ sudo in front of the command to gain root privileges. If you don't you will get errors, with 'permission denied'.

---

### Post by Joeb454 on 2008-04-22
Now both of you look at the date on post #5 and ask yourselves "why am I reviving a 13 month old thread?"

---

### Post by Martje_001 on 2008-04-22
> **Joeb454 said:**
> Now both of you look at the date on post #5 and ask yourselves "why am I reviving a 13 month old thread?"
I wasn't. I was answering Styopa's question.

---

### Post by Styopa on 2008-04-22
And I appreciate Martje's answer.

However, my question goes to the...obtuseness of Linux.
As I said, I'm a longtime DOS/Win user, and obviously I'm far more familiar with Microsoft's particular flavor of useless 'help' messages.

My point here is that if an error message says "do X to fix this", why wouldn't it say PRECISELY what one has to do to fix the situation, instead of assuming additional knowledge on the part of the user?

And yes, it's a 13 month old thread...so?  Better I start a new thread and then rewrite **everything** that was already stated here again, to ask the same question?  Isn't that WHY threads are kept - for reference?  If not, why not just delete every thread older than 60 days?  Ultimately, it's what came up when I searched for that error message, seemed logical to begin the discussion where it left off, than start another.

---

### Post by jken146 on 2008-04-22
I think it's because the error message could come up if you were running apt-get in a terminal, in which case telling you to open a terminal would be rather silly.  The problem here is probably jut a  consequence of Synaptic being a GUI frontend to apt-get.

---

### Post by LaRoza on 2008-04-22
Also, I believe that the program that is giving that message is used in distros that don't use sudo.

The message it gives is correct no matter the distro. If it said "sudo" it would restrict it to distros that use that security practice. If one is already in a root terminal, running sudo wouldn't help.

---

### Post by Sabeeh on 2008-05-30
Hey i did "sudo dpkg --configure -a" and here's what i get:
> 
dpkg: parse error, in file `/var/lib/dpkg/updates/0079' near line 1:
 newline in field name `piphany/general/remember_passwords"/>'

Any clues?

---

### Post by tommy_kay on 2008-06-10
> **Styopa said:**
> My point here is that if an error message says "do X to fix this", why wouldn't it say PRECISELY what one has to do to fix the situation, instead of assuming additional knowledge on the part of the user?

Because Linux distros are collections of features, and they all work a little differently.  It's just a fact that you will have to thrash around, trying three or four solutions.  (If you are saying that better error messages and user interface in general would make Linux more approachable, then you are of course correct.)

> **Styopa said:**
> And yes, it's a 13 month old thread...so?  Better I start a new thread and then rewrite **everything** that was already stated here again, to ask the same question?  Isn't that WHY threads are kept - for reference?

Exactly true.  I arrived years after the original question because I'm having the same problem, so putting the entire conversation in one place is obviously beneficial.  It helped me solve my problem.

---

### Post by awahid2020 on 2008-06-13
> **styopa said:**
> one Question, And I'm Sorry If This Is Really Obvious, But When You Have An Error Message Like "you Must Manually Run 'dpkg --configure -a'"

..wouldn't It Make Sense To Say "you Must Open Terminal And Run 'sudo Dpkg --configure -a' " Instead?

I Mean, I'm A Complete Ubuntu N00b, And How Would I Know That I'm Supposed To Type 'sudo' In The Command Line Before A Command?


Yes, This Solved My Problem, Otherwise I Was Getting Privilage Error

---

### Post by the_shadowfax_rider on 2008-06-26
> **Arby said:**
> Have you tried doing what the error message suggests and running the dpkg command? Type the following at the commandline ```
sudo dpkg --configure -a
``` Enter your password when prompted. Then try ```
sudo apt-get update
followed by
sudo apt-get upgrade
``` If you've already tried this or you try it now and it isn't working then post the full output from apt-get here.

What package was being installed when apt-get failed? You should be able to see this in the output just prior to the error message you've shown.

This completely solved my problem. Thanks a lot! 
:guitar:

---

