---
title: "test driving Lucid"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by catonano on 2010-04-08
Hello people,

I'd like to test Lucid. How do I install it ? In a virtual machine ? Or on its dedicated partition ?

Are there any virtual machine images usable out of the box anywhere ?

This is the firt time I ever do such a thing so I don't know how to proceed.

Thanks
Cato

---

### Post by lisati on 2010-04-08
Moved to "Lucid Lynx Testing and Discussion"

---

### Post by phillw on 2010-04-08
> **catonano said:**
> Hello people,

I'd like to test Lucid. How do I install it ? In a virtual machine ? Or on its dedicated partition ?

Are there any virtual machine images usable out of the box anywhere ?

This is the firt time I ever do such a thing so I don't know how to proceed.

Thanks
Cato

Hi Cato, 

I'd suggest a partition of its own, Virtual Machines are okay but you are putting something between the operating system you are testing and your computer; if you have a problem is it the beta version or the virtual machine environment.

Also do take the time to have a read of the stickies regarding beta testing, it will save you heartache & headaches :)

Regards,

Phill.

Regards,

Phill.

---

### Post by ratcheer on 2010-04-08
I agree, you will get the truest experience if you install it in its own partition. Create an ext4 partition of about 4 GB and you should have ample room. When you want to move on, you can just delete the partition.

Tim

---

### Post by catonano on 2010-04-08
Thank you, folks.

I'll let you know.

I'm preparing a partition right now and I will read the stickies about beta testing.

Thanks

---

### Post by catonano on 2010-04-09
Guys,

I installed Lucid on its partition, it works !

The installer wanted to resize the Karmic partition so I had to pick up the empty one by hand; after that it was a breeze, it even set up the new Grub correctly for the dual boot !

Well, there's no support for the Youtube videos in Firefox and I'll have to get used to the new Gwibber and Empathy, but overall I like the new environment

Also I'll have to try Weave, the Firefox add-on, to move all my registered accounts, browsing history, cookies based things to the new Firefox installation.

Thank you, guys
Cato

---

### Post by randomizer101 on 2010-04-09
You can view Youtube videos in Firefox, you just need Flash.

---

### Post by catonano on 2010-04-12
> **randomizer101 said:**
> You can view Youtube videos in Firefox, you just need Flash.

Yes, you're right. I installed it and it's alright.

Also I installed a couple of Firefox add-ons I am used to and I was missing them.

Now, for a new question: (should I open a new thread ?)

I think I spotted a regression. Sometimes, when waking up from a suspension, the monitor is scrambled and I just can see a square instead of the cursor pointer. I'm forced to shut off and boot again. While Karmic suspends and wakes up smoothly.

Where am I supposed to report this ? Launchpad is huge and I get lost in it.

Maybe here ? [https://bugs.launchpad.net/ubuntu/lucid](https://bugs.launchpad.net/ubuntu/lucid)

Is that the right place ?

Thanks
Cato

---

### Post by ranch hand on 2010-04-12
You really should start a new thread for a different topic so that folks that are smart enough to do a thread search can easily find the thread.

Use the command;
```

ubuntu-bug xxx

```
where xxx = the offending package.

Every thing is automatic after that.  You will need a LP account that is simple to set up when you get there.

---

### Post by catonano on 2010-04-12
Ranch Hand,

thank you, I posted this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561623)

and now I'm gonna open a new thread about it

---

