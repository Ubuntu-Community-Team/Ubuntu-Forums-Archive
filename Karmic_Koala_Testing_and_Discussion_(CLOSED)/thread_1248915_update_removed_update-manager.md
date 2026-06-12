---
title: "update removed update-manager"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-08-24
Just updated and below is the result... 

Removed the following packages:
ubuntu-desktop
update-manager
update-notifier

Upgraded the following packages:
update-manager-core (1:0.124.7) to 1:0.124.8

---

### Post by philcamlin on 2009-08-24
is ubuntu runnign fine or what ?
or do you have any issues ith using it becaus eif it removed ubuntu-desktop you would be at a blackscreen :)

---

### Post by taavikko on 2009-08-24
> **philcamlin said:**
> is ubuntu runnign fine or what ?
or do you have any issues ith using it becaus eif it removed ubuntu-desktop you would be at a blackscreen :)

?

ubuntu-desktop is just a meta-package that install the ubuntu's "image" of gnu/linux. That particular package has nothing to do with desktop functioning or not.

For OP, never do partial upgrades unless you're certain that the packages that are going to be removed are ok to be removed, this time, it isn't.

---

### Post by slakkie on 2009-08-24
You can still upgrade with update-manager-core installed, you will then use do-release-upgrade

Guess the repo's are a bit off, since there is no package for either update-manager and update-manager-kde (and probably -gnome as well).

---

### Post by bapoumba on 2009-08-24
Upgraded with aptitude, which offered to keep update-manager at lower versions.

---

### Post by chronosMark on 2009-08-24
> **rednus said:**
> Just updated and below is the result... 

Removed the following packages:
ubuntu-desktop
update-manager
update-notifier

Upgraded the following packages:
update-manager-core (1:0.124.7) to 1:0.124.8

I've had the same issue tried reinstalling it and no joy. Not to much of a problem but a strange thing to get completely removed.

---

### Post by taavikko on 2009-08-24
> **chronosMark said:**
> I've had the same issue tried reinstalling it and no joy. Not to much of a problem but a strange thing to get completely removed.

It's no strange thing, it happens when all the dependencies isn't available yet.
 ```
update-manager: Depends: update-manager-core (= 1:0.124.7) but 1:0.124.8 is to be installed
```
this means that update-manager package hasn't yet been uploaded with correct depends.

---

### Post by alphacrucis2 on 2009-08-24
> **taavikko said:**
> It's no strange thing, it happens when all the dependencies isn't available yet.
 ```
update-manager: Depends: update-manager-core (= 1:0.124.7) but 1:0.124.8 is to be installed
```
this means that update-manager package hasn't yet been uploaded with correct depends.

I can't even get that far. Apt-get update is getting a 404 karmic/universe not found for me. I'll wait till it reappears before I even look at doing an upgrade.

---

### Post by alphacrucis2 on 2009-08-24
Looks like the issue is sorted. the upgrade doesn't want to remove update-manager any more.

---

### Post by autocrosser on 2009-08-24
Yes--the update just came thru---but still the answer to partial upgrades......only do them IF you REALLY know the results.

---

### Post by Aries K on 2009-08-24
How do you get these packages it removed back? I'm sure if i restart I'll probably end up with a black screen which I want to avoid. :(

---

### Post by autocrosser on 2009-08-24
Read Taavikko's post--Ubuntu-desktop is just a Meta-package that can be removed without harm--I do prefer to have it there for testing---just look for the packages in Synaptic & reinstall them--no problem........

---

### Post by bikethetam on 2009-08-24
The same thing happened to me a few minutes ago, but then I ran 'aptitude update" followed by 'aptitude install update-manager ubuntu-desktop' and everything came back to normal.

---

### Post by Paqman on 2009-08-25
> **alphacrucis2 said:**
> Looks like the issue is sorted. the upgrade doesn't want to remove update-manager any more.

Might still be propagating. My morning update just stripped out update-manager & co.

Not a biggy, it still leaves Synaptic and the command line. Nice to know the fix is in the pipeline though.

---

### Post by jppr on 2009-08-25
why people don´t believe in simple thing... NEVER DO PARTIAL UPGRADES :confused:

---

### Post by taavikko on 2009-08-25
> **jppr said:**
> why people don´t believe in simple thing... NEVER DO PARTIAL UPGRADES :confused:

It's not about believin, it's lazyness to learn about the system they're testing.
Too many just wants to use "the newest and shiniest" without really giving back to it.

There's in harm in doing partial upgrades, **if you know what you're doing**.

---

### Post by skazi21101 on 2009-08-25
I have only one question: When new update-manager or fix will be?

---

### Post by taavikko on 2009-08-25
> **skazi21101 said:**
> I have only one question: When new update-manager or fix will be?

It's already in, use "main servers".

---

### Post by skazi21101 on 2009-08-25
Thanks.

---

### Post by jppr on 2009-08-25
there is repos new update-manager, updated this morning

---

