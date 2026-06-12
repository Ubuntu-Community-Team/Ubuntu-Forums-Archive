---
title: "missing groups, anyone else missing these?"
date: 2009-06-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-06-05
System->Admin->Users-and-Groups->Manage-Groups just shows 2 groups, myself and root. Is it only me?
Cheers, mike

---

### Post by Gourgi on 2009-06-05
> **mdurham said:**
> System->Admin->Users-and-Groups->Manage-Groups just shows 2 groups, myself and root. Is it only me?
Cheers, mike

it is not only you, same here.

```
$ cat /etc/group | wc -l
63

```

---

### Post by ronacc on 2009-06-05
same here and in addition the first time I click on it , it just tells me I am not authorised to access it , the second time it asks for my password .

---

### Post by mdurham on 2009-06-05
Thanks guys, I guess we just wait for a fix.
Cheers, Mike

---

### Post by lonniehenry on 2009-06-05
I'm confused.  I think that is all you should have - root and user.  I added another user to test something and so I have root and me and the test user.  The lock is part of the policykit to prevent any user from deleting root or changing permissions.  Correct me if I am wrong.

---

### Post by ronacc on 2009-06-05
you , root and new user are users , groups you belong to and establish what you are allowed to do . see screen shot .

---

### Post by lonniehenry on 2009-06-05
Thanks for the response. I was pretty sure that was the way it worked so there isn't really a problem for one user to only have root and user if the computer was only used by one person.

---

### Post by Gourgi on 2009-06-05
> **ronacc said:**
> in addition the first time I click on it , it just tells me I am not authorised to access it , the second time it asks for my password .
confirming this too

---

### Post by ronacc on 2009-06-05
it is ok to only have root and one USER . but you still need the groups to grant privileges . look again at the screenshot the groups are the ones user ron has access to .

---

### Post by ranch hand on 2009-06-06
I am on Jaunty right now and checked and that is all I have.  This is a one user box.

I will try to add a user to 9.10 nest time I am over there.

---

### Post by linux6994 on 2009-06-06
You have to pay extra to see all of the groups LOL

---

### Post by mdurham on 2009-06-06
> **linux6994 said:**
> You have to pay extra to see all of the groups LOL

Would that be a group payment?

---

### Post by ronacc on 2009-06-06
with an exemption for preexisting privlages ?

---

### Post by seeker5528 on 2009-06-06
> **ronacc said:**
> it is ok to only have root and one USER . but you still need the groups to grant privileges . look again at the screenshot the groups are the ones user ron has access to .

Looks like the current philosophy is.....

If you have to mess with groups less than 1000 (system groups) it is a bug.

If account properties doesn't handle your permission giving needs for the normal use cases, it is a bug.

[img]http://home.comcast.net/~seeker5528/Screenshot-AccountProperties.png[/img]

For normal desktop use cases this looks pretty good to me.

If you have other needs, I would expect the traditional methods still work. Kuser looks like it probably still works more or less the same as it ever did, personally it's my prefered user and group management app, no matter what desktop I'm running at the time, when using GUI tools to do this stuff.

Later, Seeker

---

### Post by ranch hand on 2009-06-08
I finally remembered to test this.  I gat a warning that I did not have permissiong to run that app.  Close and retry and unlock worked fine.  Made another user (adminstrative) and logged in as that user.  The only problem was that the Work Space sellector only shows one workspace.  I ctrl+alt+backspaced to log in as the other user and the same to come back to the normal user.  Sometime I will reboot and try it that way.

---

### Post by geojorg on 2009-06-13
This is how it should work, is a better way to avoid broking the system. I like this new setting.

---

### Post by Bucky Ball on 2009-06-13
Or:

```
sudo nano /etc/groups
```

... and add yourself to a specific group.

---

### Post by tekstr1der on 2009-06-16
Regarding the OP's initial observation:

> **mdurham said:**
> System->Admin->Users-and-Groups->Manage-Groups just shows 2 groups, myself and root.

Is this expected behavior? I am seeing this also and I can't really see the point of limiting the GUI user management tool such that groups cannot be shown, modified, etc.

Also add me to the bunch of testers experiencing the denied permission on first run. I could not find a specific bug for this on launchpad. Anyone know if it's been filed?

---

