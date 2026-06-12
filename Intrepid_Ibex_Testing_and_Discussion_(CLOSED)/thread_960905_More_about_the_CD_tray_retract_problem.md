---
title: "More about the CD tray retract problem"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2008-10-27
I'd think most of us know there is/was a problem regarding the CD tray retracting so quickly that it was difficult to remove a CD/DVD.

I applied this patch:

[https://bugzilla.redhat.com/attachment.cgi?id=312742](https://bugzilla.redhat.com/attachment.cgi?id=312742)

This way:

sudo gedit /etc/udev/rules.d/60-persistent-storage.rules

Today I read this:

"I would like to add that there is no need to put the patch under
/etc/udev/rules.d/ dir. It's ok to put it for ex under ~/."

I don't understand!

I'm out of my league! Help!

BTW, the patch worked fine for me, the reason I want to know is to NOT give bad info to others!

RE: [http://ubuntuforums.org/showthread.php?t=942553&page=3](http://ubuntuforums.org/showthread.php?t=942553&page=3)

---

### Post by exploder on 2008-10-27
The Developer's need to come up with an upgrade to install the patch. It would be ridicules to leave this bug because of all of the eject buttons that are supposed to be a new feature.I would expect to see a package update soon that will address this issue.

---

### Post by kansasnoob on 2008-10-27
> **exploder said:**
> The Developer's need to come up with an upgrade to install the patch. It would be ridicules to leave this bug because of all of the eject buttons that are supposed to be a new feature.I would expect to see a package update soon that will address this issue.

I get that. I'm just trying to learn and understand, so I'd like to know what this means:

"I would like to add that there is no need to put the patch under
/etc/udev/rules.d/ dir. It's ok to put it for ex under ~/."

I understand that "dir" means directory but I'm clueless as to what "ex" means (I thought executable was out in Linux) and totally dumb-founded with ~/.

I'm just trying to understand.

The more you learn the more dangerous you are, eh?

---

### Post by mc4man on 2008-10-27
ex - means 'for example'

It's referring to running the patch which in any event isn't written for ubuntu.
Manually editing the file as you did is fine, though technically you would replace the '- line' with the '+ line'

---

### Post by mcallenSchmee on 2008-10-27
> "I would like to add that there is no need to put the patch under
/etc/udev/rules.d/ dir. It's ok to put it for ex under ~/."
I think that means: 
> the patch doesn't need to go in the /etc/udev/rules.d/ directory, you could for example put it in the home directory. 
A "~" means the current user's home directory.

---

### Post by kansasnoob on 2008-10-27
> **mc4man said:**
> ex - means 'for example'

It's referring to running the patch which in any event isn't written for ubuntu.
Manually editing the file as you did is fine, though technically you would replace the '- line' with the '+ line'

I get that.

In this case it was only +.

---

### Post by kansasnoob on 2008-10-27
> **mcallenSchmee said:**
> I think that means: 

A "~" means the current user's home directory.

You're talking over my head! Maybe!

The point is that in just a few days we'll have tons of people installing Intrepid. I'll be one of the first to catch a copy.

Hopefully this will be fixed in the final release, but if it's not I'd like to know what I'm talking about beyond just:

I did this and it worked!

I like to have some idea what I'm doing. Or recommending.

---

### Post by panda726 on 2008-10-28
The tilde or ~ is simply a shorthand variable for the home directory of the user you are logged in as.  For example, if you were logged in as "kansas", then ~/ would be (typically the default) a shorthand way of writing /home/kansas/ .  Just a way of referencing something that is often used, and exists often many times per install, making the absolute path impractical for giving advice (among other things).

Tor

---

### Post by ad_267 on 2008-10-28
Wow I don't use my CD drive much so I hadn't noticed.

That's ridiculous they really should fix this!

---

