---
title: "Popfile not working after installation trough package manager"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by hansdezwart on 2006-06-09
About a week ago I have finally made THE switch: gone are the days of Windows XP on my laptop. I am all Ubuntu now.

I would love to have popfile available. I have installed it using Synaptic (version 0.22.2-3). The popfile.pl file is in /usr/share/popfile/. I see a script in /etc/init.d which should start popfile as deamon everything I start my computer.

When I run: ```
ps aux | grep "popfile"
```, I do see a process:

> popfile   4656  0.0  3.0  17384 14560 ?        Ss   08:46   0:00 /usr/bin/perl /usr/share/popfile/popfile.pl --set config_piddir=/var/run/popfile/ --set logger_logdir=/var/log/popfile/

If I try to load [http://localhost:8080](http://localhost:8080) or [http://127.0.0.1:8080](http://127.0.0.1:8080) I get nothing! When I try to load popfile manually by running "sudo perl popfile.pl" from the popfile directory, the scripts sees the other process, tries to contact it but fails and then popfile loads normally and is accessable trought the web-interface.

Does anybody now what my problem could be and how I could solve it?

---

### Post by hansdezwart on 2006-06-13
Well, I had some contact with the very pleasant and knowledgable maintainer for the Debian popfile package.

I seem I was checking the wrong port. The webinterface for popfile runs on port 7070 and the pop server (that your e-mail client needs to check in with) runs on port 7071.

Good luck to anyone else in using this great anti spam utility!

---

### Post by NZ-Wanderer on 2006-11-11
Forgive me for being a little confused here...
I ttried what you said in a pervious message about sudo from within popfile itself, and it worked when I did the [http://127.0.0.1:8080/](http://127.0.0.1:8080/) aftrwards.. - Now you say that I supposed to use another port??

Anyway, are you still using popfile?? - I just installed it using Synaptic, then got stuck and couldn't figure out what was happening until I came across your message above..
I like the sound of Popfile, but am a little hesitant cause of manually having to start it in terminal all the time..

Ohwell, off to try to figure out the next step :mrgreen: (buckets)

> **hansdezwart said:**
> Well, I had some contact with the very pleasant and knowledgable maintainer for the Debian popfile package.
I seem I was checking the wrong port. The webinterface for popfile runs on port 7070 and the pop server (that your e-mail client needs to check in with) runs on port 7071.
Good luck to anyone else in using this great anti spam utility!

---

### Post by hansdezwart on 2006-11-11
Hello NZ-wanderer,

I still use popfile (with great joy!). I find it when I run:

[http://localhost:7070/](http://localhost:7070/) :-k 

Anyway wherever you find it as long as you configure it and it works, why be worried ;)

---

### Post by NZ-Wanderer on 2006-11-11
Too true :) :)

It runs perfectly for me under [http://localhost:8080](http://localhost:8080), took me about 3 hours to get everything setup (got 8 different email addresses I had to reconfigure and have 14 buckets to fill up...
Can't wait for the day when I can just let Popfile take care of everything for me..

One thing the notes didn't mention, do we have to turn off the "junk" settings in Thunderbird since we use Popfile, or just leave them turned on??

Am a little annoyed that I have to turn it on via terminal each time and then leave terminal open.. - So far I have accidentally closed terminal 4 times and have then had to open it and re-run Popfile again.. Bit of a pain in the butt..

Apart from that, it is running perfectly as far as I can tell, and am very impressed with it so far...

> **hansdezwart said:**
> Hello NZ-wanderer,
I still use popfile (with great joy!). I find it when I run:
[http://localhost:7070/](http://localhost:7070/) :-k 
Anyway wherever you find it as long as you configure it and it works, why be worried ;)

---

### Post by hansdezwart on 2006-11-11
The popfile website has some very good documentation on how to set things up for Thunderbird:
[http://popfile.sourceforge.net/cgi-bin/wiki.pl?HowTos/Mozilla_Netscape](http://popfile.sourceforge.net/cgi-bin/wiki.pl?HowTos/Mozilla_Netscape)

I have the auto junk-labelling turned of in Thunderbird. I have a filter set up that moves the messages that popfile marks as junk into a folder called junk and then also mark it as junk. This makes them easier to delete out of the trash can later on...

---

### Post by NZ-Wanderer on 2006-11-13
well mostly everything is going great, after only a few days I have the following:

Classification Accuracy
Messages classified: 	146
Classification errors: 	47
Accuracy: 	67.8%

which isn't too bad methinks :D 

My only problems now, is that:

1) I have the same problem you mentioned above whereas I have to start it in terminal and then get the Other process message before it starts the new process after 10 secs (could you possibly explain in noob terms how you fixed it please :mrgreen:  )

and 

2) Having to have terminal open all the time... (I keep forgetting and close it)

---

