---
title: "apt-get upgrade killed my computer"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by beach_defender on 2008-11-03
Hi,
I recently installed 8.04 on my desktop machine.

On Fri, I used the update manager to 'try' to upgrade.

After a number of hours, I got a message (that I haven't saved, sorry) to the effect that it had failed and I needed to do

dpkg --configure -a

So I did that and it falls over, So  I did

dpkg --configure -a >& update_errors.txt. (see attached)

Now when I try to connect I get an Error Message 
"Your session only lasted ..." -

I have attached a copy of the .Xsession-errors files.

I was going to try to simply install 8.10, but this machine has no DVD drive anymore.

Is there an upgrade that works?

What do you do when the fix (apt-get --configure -a ) seems to break more things.

How do I get back, forward to a point of some stability?

I use NIS here and that was also broken during the update.

I am currently using ssh to log onto the machine to fix things.

I had hoped that this would be relatively painless, guess we're not there yet.

---

### Post by beach_defender on 2008-11-03
I have been looking some more.

I tried 
 dpkg -C >& broken.txt

I have attached the output:



I guess my biggest problem is knowing where to start.

---

### Post by kerry_s on 2008-11-03
have you tried sudo apt-get -f install

---

### Post by beach_defender on 2008-11-04
Hi Kerry,

Yes I have tried that.

I get the same dpkg error - telling me to run 'dpkg --configure -a',

But that of course is the problem, it fails with the errors above.

Not sure what to try next, still looking,

Thank you for your idea,
Barry

---

### Post by cdtech on 2008-11-04
I take it your using "sudo"
```
sudo dpkg --configure -a && sudo apt-get -f install
```

Just need clarification......

You also said you are running this command via remote?

---

### Post by beach_defender on 2008-11-04
Hi,
Yes, sorry.

I normally do an "sudo su [-]" before I start - saves typing

Sorry for confusion.

I still haven't seen anything that makes sense to cure dpkg.

---

### Post by cdtech on 2008-11-04
Here is a link I'm reading up on about the upgrade from 8.04 LTS to 8.10 and may be of some help.
[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html)

Let me know if this gets you any further.

---

### Post by beach_defender on 2008-11-04
Thanks,
Looking now

Barry

---

### Post by cdtech on 2008-11-04
Be sure and read the comments posted by others. Some it worked for and others had problems that seem to have a fix for.

I'm thinking of doing the upgrade but nothing is broke on my system. I'm doing a full backup before I do the plunge. lol

---

