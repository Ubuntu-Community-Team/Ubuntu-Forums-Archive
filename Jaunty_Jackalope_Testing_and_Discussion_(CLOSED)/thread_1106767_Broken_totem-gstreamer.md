---
title: "Broken totem-gstreamer"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by igor4u on 2009-03-26
Can't remove, reinstall or configure totem-gstreamer.
Please help!

FIXED
Manually removed all totem-gstreamer folders etc.

---

### Post by taavikko on 2009-03-26
In what way?

What errors are presented to you when trying to do any of above?

Totem should be removable via
```
sudo apt-get --purge remove totem\*
```
That'll take care of any totem* package...

But maybe before doing that, youll tell what youre trying to achieve?

---

### Post by Taiebot65 on 2009-03-26
Me i can tell you totem takes ages to close....

If you are also affected please confirm this bug..

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/347883]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/347883")

---

### Post by exploder on 2009-03-26
I have Intel graphics and also have problems with Totem playing DVD movies. Not quite the same bug you have linked to though. I have to drag the slider or click on the arrows a time or two to get a movie to start to play....

I filed a bug report but never received the conformation e-mail for it.I think that all of the multimedia related problems we are seeing are directly related to the Intel drivers.

Flash playback in full screen is also a problem if you are using Intel graphics. These types of problems were not present in the last two releases. Hopefully the Intel drivers will get updated and these types of problems will go away.

---

### Post by taavikko on 2009-03-26
> **exploder said:**
> 
Flash playback in full screen is also a problem if you are using Intel graphics. These types of problems were not present in the last two releases. Hopefully the Intel drivers will get updated and these types of problems will go away.

Haven't got this behaviour with Firefox &
945GM [8086:27ae] (rev3) UXA as AccelMethod
And using aspire One (mininotebook)

Totem is also playing fine everyfile I throw at it.
Might suspect that issues are rising that DE's are getting huge and bloated ;) (see the smiley, not starting flame war)


<OT>
Currently using e16 with this laptop.
Blazing fast<OT/>

---

### Post by igor4u on 2009-03-28
> **taavikko said:**
> In what way?

What errors are presented to you when trying to do any of above?

Totem should be removable via
```
sudo apt-get --purge remove totem\*
```
That'll take care of any totem* package...

But maybe before doing that, youll tell what youre trying to achieve?
After this I get messages:
Removing packet totem-gstreamer...
update-alternatives: error or EOF reading /var/lib/dpkg/alternatives/totem for update_mode ()
dpkg: can't process parameter totem-gstreamer (--purge):
 Sub-process pre-removal returned an error code 2
During processing these packets were errors:
 totem-gstreamer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help!

---

### Post by Nullack on 2009-03-28
Very strange. If it were me I would download a new daily iso and repartition the install doing a full cleanout.

---

### Post by Taiebot65 on 2009-03-28
There is definitely a problem with totem the frame are going very fast 2 to 3 times quicker than normally and at the same time the sound is totally normal........Strange..

---

