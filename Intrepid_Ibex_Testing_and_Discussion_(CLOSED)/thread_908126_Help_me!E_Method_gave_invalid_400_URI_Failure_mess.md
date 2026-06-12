---
title: "Help me!E: Method gave invalid 400 URI Failure message"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chun79 on 2008-09-02
when i used command: apt-get update 
I get an error message:E: Method gave invalid 400 URI Failure message 

so I can't update my ubuntu8.10.

I'm using ubuntu 8.10.

please tell me how to ?

thanks.

[email]guo.chunliang@gmail.com[/email].

---

### Post by overdrank on 2008-09-02
Hi and welcome, 8.10 Intrepid is still in the testing phase and you are likely to run into issues. Have you tried changing the location of the server in software sources? 

Moved to intrepid :)

---

### Post by isthisusertaken? on 2008-09-09
chun79,


I was having the same issue as you starting about 4 days ago. Well today I found the culprit. :)

I installed the following BETA software, since I use Ubuntu as the OS of choice for my gaming. 

[http://www.playdeb.net/available_games.html](http://www.playdeb.net/available_games.html)

It added an extra directory with a software list, well this interfered with the updating /etc/apt/sources.list file. 
A simple sudo rm -rf of /etc/apt/sources.list.d/ directory that the had been installed by the program, will allow apt/aptitude package manager to update once again.

Since that directory is similar to the "real" repository list, please make sure your commands are correct, and first but fore most backup /etc/apt/sources.list so you don't lose your previous software repositories in the event of a mistake.

I'm not sure how long you have been using Ubuntu, but I tried to make this post brief and useful.

Hopefully this fixes your issue, it dine mine.

---

### Post by kseise on 2008-09-10
Before using the rm -rf command, try just doing:
> cd /etc/apt/sources.list.d
ls

If you see the playdeb.list file, delete just that one.  The Medibuntu sources are listed in the same directory and the rm -rf command will delete them and potentially stop you from being able to play DVDs.

Hope that helps.  If fixed mine.

---

### Post by Vadi on 2008-09-12
What version of Ubuntu did you install Playdeb on?

---

### Post by furthur on 2008-10-05
Same problem here, and once again, playdeb was the culprit. 

I must add that simply deleting everything in your /etc/apt/sources.list.d directory is a little silly. In fact, I had my playeb repository posted in my /etc/apt/sources.list file. (sudo gedit /etc/apt/sources.list and remove or comment out playdeb line... or simply use a modern package manager to do the same)

Hope this sheds a little more light on the matter... it certainly is an odd error message to get from apt. (and quite disabling)

---

### Post by jimmah6786 on 2008-10-17
Same problem in Ubuntu 8.04. Removal of the playdeb source list works.

Thank You!!

---

### Post by Vadi on 2008-10-17
The issue lies in apt, which has this bug. So hopefully Ubuntu will fix this issue soon - until then, either disable playdeb and re-enable it later when the server is up or just wait and try again later.

---

### Post by Vadi on 2008-10-27
OK, we found the issue (sort of). Apt caches things for 6 hours by default, so even when Playdeb is fixed, apt won't bother to check that and still remember the "old" stuff.

We'll have an updated .deb that removes the caching, but meanwhile if you removed playdeb 6+ hours ago, you can now add it back safely :)

---

### Post by scrooge_74 on 2008-10-28
Well I had that same error message, but I have another one which is a bit interesting:

501 Tor is not an HTTP Proxy

Have no clue why is doing that since tor being working on this PC for weeks before this ever showed up

EDIT: seems I solved, for some reason apt and synaptic were trying to use the proxy without me telling them to do it, so I set it to use the proxy, then told to connect directly to the internet.

Seems that solved it

---

### Post by Vadi on 2008-10-29
Glad you got it sorted out

---

