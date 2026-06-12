---
title: "Current Kernel is: 2.6.31-14.46-&quot;Latest Stable Kernel&quot; is: 2.6.31.4. ?"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-14
[http://www.kernel.org/](http://www.kernel.org/)
[http://www.linuxhq.com/kernel/v2.6/31/index.html](http://www.linuxhq.com/kernel/v2.6/31/index.html)

Ok, I am guessing that the "-14" somehow includes ".4", but...
Anyone got a link, FAQ or a simple answer?
Thanks!

---

### Post by dabl on 2009-10-14
The changelog is clear enough:

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.31.4](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.31.4)

it is 2.6.31.4.  Newer than that are not yet approved for stable.

---

### Post by emarkay on 2009-10-14
> **dabl said:**
> The changelog is clear enough:
[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.31.4](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.31.4)
 it is 2.6.31.4.  Newer than that are not yet approved for stable.

Thanks - I really wasn't looking for the details, I just wanted to know WHY the nimbering scheme is different.  

Take a look at your Synaptic", under "Linux" and you will see the "-14".  Alternatively, then why is Ubuntu omitting the ".4"?

---

### Post by seeker5528 on 2009-10-14
> **emarkay said:**
> Thanks - I really wasn't looking for the details, I just wanted to know WHY the nimbering scheme is different.  

Take a look at your Synaptic", under "Linux" and you will see the "-14".  Alternatively, then why is Ubuntu omitting the ".4"?

Don't know what the Ubuntu devs are doing exactly, but if you look at Debian.....

As you go through the 2.6.31 releases the modules should theoretically be compatible, so if you included the teeny version number as part of the package name every time, the kernel would get installed in a new directory every time, and all modules would have to be rebuilt every time.

To combat this a package name like '2.6.31-1, 2.6.31-2, etc...' is used where the '-X' is only incremented when there is an ABI change that would cause modules built with the previous release to break. 

This way the teeny updates that are binary compatible can be installed, updating only the package version so they upgrade your existing kernel. Upgrades that break compatibility in some way increment the ABI causing them to be installed as a new package in a new directory.

Looking at the Ubuntu versioning it would seem they use some kind of parallel logic, but the ABI part of the number seems to get updated excessively, possibly to reduce the chance of leaving you without a bootable kernel.

Later, Seeker

---

### Post by emarkay on 2009-10-15
OK, but then why is it not "2.6.31.4-14.46"?  :)

---

### Post by VMC on 2009-10-15
I think your confusing ubuntu's kernel with with stable kernel.
Most distros patch vanilla kernels for their user space.

I think Slackware is one that uses "over the counter" stable kernels.

---

### Post by Amaranth on 2009-10-15
The -14 is the ABI version and the .46 is how many revisions of the 2.6.31 kernel we've had (like the ubuntuX versions for other packages).

---

### Post by JoseReyes on 2009-10-15
> **Amaranth said:**
> The -14 is the ABI version and the .46 is how many revisions of the 2.6.31 kernel we've had (like the ubuntuX versions for other packages).


Any idea as to why my machine still shows kernel 2.6.31.12

I have downloaded all the updates and everything seems to be okay, however, evey time I try to see if it took the newest kernel it still shows the same 
2.6.31.12

Am I missing something?

---

### Post by emarkay on 2009-10-15
> **JoseReyes said:**
> Any idea as to why my machine still shows kernel 2.6.31.12

I have downloaded all the updates and everything seems to be okay, however, evey time I try to see if it took the newest kernel it still shows the same 
2.6.31.12    Am I missing something?

Please don't "hijack" threads with information that has NOTHING to do with the original post - at least it's annoying and at most, your question will be ignored as no one will see it.

But FWIW, did you actually SEE a newer kerned appear in the list when you upgraded?  If so, you may need to update GRUB.

---

### Post by JoseReyes on 2009-10-15
> **emarkay said:**
> Please don't "hijack" threads with information that has NOTHING to do with the original post - at least it's annoying and at most, your question will be ignored as no one will see it.

But FWIW, did you actually SEE a newer kerned appear in the list when you upgraded?  If so, you may need to update GRUB.



My appologies, could not find a threat....

I have seen kernels up to 2.6.31.14 appear and installed.

---

### Post by NCLI on 2009-10-15
Just make a new thread next time. ;)

Anyway, just run sudo update-grub2 for now. If it doesn't solve the problem, make a new thread.

---

### Post by dabl on 2009-10-15
> **emarkay said:**
> OK, but then why is it not "2.6.31.4-14.46"?  :)

Prolly here is a place to start your research on that one:  :P

[http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html](http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html)

---

### Post by seeker5528 on 2009-10-15
> **emarkay said:**
> OK, but then why is it not "2.6.31.4-14.46"?  :)

My best guess would be....

Not expected to have changes that are all that huge between one 2.6.31 release and the next.

In the bigger picture the changes between one 2.6.31 release and the next may often be less significant than the differences between the stock kernel and the Ubuntu kernel that result from the patches being applied to the Ubuntu kernel.

Easier to review the history of changes/patches if you don't have an extra number in there preceding the -XX.XX.

Later, Seeker

---

### Post by emarkay on 2009-10-15
> **dabl said:**
> Prolly here is a place to start your research on that one:  :P
[http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html](http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html)


What was in there behind those asterisks?

---

### Post by VMC on 2009-10-15
> **emarkay said:**
> What was in there behind those asterisks?

Here it is:
[**Kernel package version rules**]("http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html")

---

### Post by emarkay on 2009-10-15
> **VMC said:**
> Here it is:
[**Kernel package version rules**]("http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html")

I get:
[http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html](http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html)

Is this some swear word that some overaggressive "Message Board Nanny Program" is filtering????

---

### Post by trulan on 2009-10-15
Try searching for the rest of what VMC posted.  For some reason the forum doesn't like the name, and filters it out when I try to post it too.   (it's not obscene - just a privacy thing or something.) Google brought it right up when I copied/pasted his link and searched.

---

### Post by VMC on 2009-10-15
> **emarkay said:**
> I get:
[http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html](http://www.******************/ubuntu-kernel-team/326478-kernel-package-version-rules.html)

Is this some swear word that some overaggressive "Message Board Nanny Program" is filtering????

That's weird. It was okay when I posted it. I have to put it this way for it to stick. Remove the CR's. Strange indeed

Edit: replace the "[FONT="Courier New"][COLOR="red"]DASH[/COLOR][/FONT]" with '-' below.
[www.linux](www.linux)[FONT="Courier New"][COLOR="Red"]DASH[/COLOR][/FONT]archive.org/ubuntu-kernel-team/

---

### Post by dmizer on 2009-10-16
> **VMC said:**
> That's weird. It was okay when I posted it. I have to put it this way for it to stick. Remove the CR's. Strange indeed

At one point we were getting over run with spam bots from that site. We filtered it to limit the spam's effect.

---

### Post by dabl on 2009-10-16
Deleted -- redundant to VMC's reply.

---

