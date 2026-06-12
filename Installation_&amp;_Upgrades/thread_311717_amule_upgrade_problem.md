---
title: "amule upgrade problem"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by Corvair on 2006-12-03
I have listed a thread on general help without any solution for my problem.

I got a request for upgrading AMULE which I acknoledged.
After the upgrade was completed I could not launch AMULE.
I tried launching it from a terminal without any success either.
I removed AMULE using sudo apt-get and reinstalled it without any success, also did the same using Synaptic with the same result.
I had no problems before this, so what is the problem and what is the solution?

Here is what I get back from Terminal:

Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

---

### Post by syrleb on 2006-12-03
try removing everything to do with amule from your computer, everything you can find, then reinstall
go through all your folders you can and delete anything with amule in it, i had a similairr problem with a different program a while ago

---

### Post by Corvair on 2006-12-03
Thanks for the tip, but nothing doing, it wont launch.

---

### Post by marselluswallace on 2006-12-03
i have the same problem. today i decided to follow the auto update suggestion and updated my amule from 2.1.2 to 2.1.3, now everytime i try to start it i get the same error:

Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

how can i solve this? i tried the complete uninstall plus other suggestions from other threads but nothing seems to work :(

---

### Post by Corvair on 2006-12-03
marselluswalace,

Welcome to the club, hopefully someone will come up with a solution.

---

### Post by Corvair on 2006-12-03
marselluswallace,

I just remembered I had similar problems when I upgraded from amule version 2.1.0 to 2.1.3 and then I was able to solve the problem on the following thread. This time it is of no help to me but it may help you, so check it out.



[http://forum.amule.org/thread.php?threadid=10437&sid=91bf094e6157cbfadf7b982253d61303&threadview=0&hilight=&hilightuser=0&page=1](http://forum.amule.org/thread.php?threadid=10437&sid=91bf094e6157cbfadf7b982253d61303&threadview=0&hilight=&hilightuser=0&page=1)

---

### Post by marselluswallace on 2006-12-04
no.. it did not helped me :(
still have the same problem, and everything is correct according to that thread.

---

### Post by Dragineez on 2006-12-09
Yup, me too. "Upgrade" killed amule. I'm pretty sure this is a wxGTK generated problem - but I haven't figure out how to solve it yet.

---

### Post by Corvair on 2006-12-23
For anyone interrestsed or who had the same problem,
I went on aMule forum and found out that the problem was with wxGTK.

So I went to Synaptic and completely removed wxGTK.

Now I am able to launch aMule.

At first it would not connect so I loaded wxGTK from the site wxgtkwidget.org and installed it in tmp file.
Now everything seems to work fine.

---

### Post by marselluswallace on 2006-12-27
thank you corvair.
i uninstalled the wxGTK and my amule started to run again, but i get low-id. maybe is just because of my router? i haven't re-installed wxGTK again though, 'cause that site is not working... isn't it wxwidgets.org instead of wxgtkwidgets.org ?
will my ubuntu freakout without the wxGTK, or is it just needed to amule?
i'm dealing with this as i type.

---

### Post by Corvair on 2006-12-28
Marselluswallace,

You are  right about the site address.


I could not reinstalle wxGTK either an it does not seem to make a differnce anywhere else.
aMule works fine also.

---

