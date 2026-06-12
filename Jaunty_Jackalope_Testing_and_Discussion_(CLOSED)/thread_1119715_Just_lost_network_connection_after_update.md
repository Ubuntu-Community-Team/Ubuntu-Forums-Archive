---
title: "Just lost network connection after update"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by joewski on 2009-04-08
I have just lost my network connection.
ethO says I have a connection but from command line I can't ping anything.

I running from my laptop which is also running 9.04 but it hasn't upgraded yet.

Any clues how to restore network connection?

---

### Post by DougieFresh4U on 2009-04-08
What were the updates? Did you notice anything pertaining to 'network'?
I am gonna check updates now.

EDIT: Yes, I see one for 'network manager. Maybe reinstalling 'network manager'?
Not sure about this and I 'aborted' update

---

### Post by joewski on 2009-04-08
There was a huge list, and I wasn't paying attention.

I'm checking the laptop now to see what is in the pipeline.

I can see libnm-glib0 and libnm-util1 being updated, as network management framework Glib shared library.

Also network-manager framework deamon updating

---

### Post by DougieFresh4U on 2009-04-08
> **joewski said:**
> There was a huge list, and I wasn't paying attention.

I'm checking the laptop now to see what is in the pipeline.

'network manager' was in there.

---

### Post by sbrandon on 2009-04-08
I am able to get out on the Internet from mine after the morning update.

---

### Post by joewski on 2009-04-08
I've just starting to report the bug over at launchpad. 

Is there anyway to reverse the updates? (I never done that)

---

### Post by joewski on 2009-04-08
> **sbrandon said:**
> I am able to get out on the Internet from mine after the morning update.

How long ago did you update? in hours please?

Are there any more updates in your pipeline?

---

### Post by joewski on 2009-04-08
For the record I don't know what went wrong. 

I ended up reinstalling the operating system again cleanly.
It now works with the hardware again.

It must have been a software conflict or something.

---

### Post by linuksamiko on 2009-04-10
Does anybody know what caused this problem? I had the same issues about two days ago (networkmanager was one of the updates).
For some reason this update even deleted my imigrd-file but I could solve this problem (finally).
I certainly don't want to reinstall the whole system. So if anybody got an idea why network is gone please let me know.

Maybe this gives you a hint:
ifconfig shows no network cards (exept of 127.0.0.1 of course)

---

