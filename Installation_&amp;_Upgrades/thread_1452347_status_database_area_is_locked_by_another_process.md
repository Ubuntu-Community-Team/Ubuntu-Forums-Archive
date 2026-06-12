---
title: "status database area is locked by another process"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by vys on 2010-04-11
I tried to install java runtime in the terminal, and I got to the 'contract acceptance' page, and I couldn't find a way to accept and move forward, so I just closed the Terminal, killing the process. later, I went to the ubuntu software center, and tried to install java runtime using that. the status for the installation remained at 0% and said "waiting for other software managers to quit". so I exited out of software center. then update manager popped up, asking me to update several things, including installing java runtime. so I hit yes, and it said this:

E:dpkg was interrupted, you must manually run 'dpkg --configure-a' to correct the problem

so I ran:

sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade

and again got to the 'contract acceptance' page and was stuck.

so I then ran:

sudo apt-get -f install

and the readout was:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

so then I ran:

sudo dpkg --clear-selections

and the readout is:

dpkg: status database area is locked by another process

I gave up and shutdown my computer. before it would shut down, it said the program 'File Manager' was unresponding, so I clicked to kill it and my computer shut down. I started it up again, and tried to run Update Manager again, and I went through the whole process over, with the same result.

I'm brand new to ubuntu & linux but I did a lot of research and I still can't solve the problem. can somebody help me?

---

### Post by ggearth on 2010-06-12
Unfortunately, I do not have a solution, but a similar occurrence.
"[COLOR=Red]Status database area is locked by another process[/COLOR]"
following $ [COLOR=Blue]sudo dpkg --configure -a[/COLOR]
when Synaptic could not bring the necessary packages together for any attempt to install an application.  Hopefully, an answer has been found but not posted.  Thanks.

---

### Post by noncul on 2011-09-03
I ran into the message on 10.04.2 LTS when installing debian packages and got the message
"dpkg: status database area is locked by another process"
Then closing Synaptic manager solved the issue. There might be other situations leading to this and solution could be different. Please share your experience if any.

---

