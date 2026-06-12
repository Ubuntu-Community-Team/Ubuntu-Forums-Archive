---
title: "How to add all PPAs at once"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kenny_Strawn on 2010-03-20
How do you add all PPAs recursively? I was wondering, since they all come from the same place.

---

### Post by 23meg on 2010-03-20
Could you clarify, in different words if possible? What exactly do you want to do? I'm sure you don't want to add *every PPA that exists*.

---

### Post by kurros on 2010-03-20
:-o

There are close to 4000 ppa's on launchpad, and many would certainly conflict with each other or lucid.

Or do you just want a way to add your favorites in one step?

You can add them using the command *sudo add-apt-repository ppa:<repository-name>* ... easy enough to make a shell script

---

### Post by Kenny_Strawn on 2010-03-20
Something like this:

```
sudo add-apt-repository ppa:*
```

I tried this already, without much luck. What I am trying to do is recursively add all PPAs on Launchpad.net, not necessarily all that exist.

---

### Post by Kenny_Strawn on 2010-03-20
What I specifically want to be able to do is create a whole Linux distro using nothing but PPAs, using nothing but PPAs for the OS's repos.

---

### Post by 23meg on 2010-03-20
The PPAs on launchpad.net *are* all PPAs that exist, since the PPA service is part of Launchpad. 

If what you're trying to do worked, you'd end up with a messed up system full of package conflicts. There's simply no practical use case for doing it, hence there being no practical way to do it.

---

### Post by VMC on 2010-03-20
EDIT:Never mind, the link was for adding all you PPA's keys.

---

### Post by Uncle Spellbinder on 2010-03-20
I would really like to hear Kenny's clarification. Because adding 4,000+ PPA's borders on insane.

---

### Post by Kenny_Strawn on 2010-03-20
> **23meg said:**
> The PPAs on launchpad.net *are* all PPAs that exist, since the PPA service is part of Launchpad. 

If what you're trying to do worked, you'd end up with a messed up system full of package conflicts. There's simply no practical use case for doing it, hence there being no practical way to do it.

[http://ubuntuforums.org/showpost.php?p=8997026#post8997026](http://ubuntuforums.org/showpost.php?p=8997026#post8997026)

This is what I intend to do: create a Linux distro using nothing but PPAs.

---

### Post by Anduu on 2010-03-20
> **23meg said:**
> The PPAs on launchpad.net *are* all PPAs that exist, since the PPA service is part of Launchpad. 

If what you're trying to do worked, you'd end up with a messed up system full of package conflicts. There's simply no practical use case for doing it, hence there being no practical way to do it.

+1

Very bad idea.

All it takes is one PPA that offers a conflicting package version.I tried out the GIMP testing PPA a while back and it caused enough problems that I had to remove it.

---

### Post by 23meg on 2010-03-20
> **Kenny_Strawn said:**
> [http://ubuntuforums.org/showpost.php?p=8997026#post8997026](http://ubuntuforums.org/showpost.php?p=8997026#post8997026)

This is what I intend to do: create a Linux distro using nothing but PPAs.

I see, but that won't work, at least with the existing PPAs. You'd have to build everything you need specifically, and that wouldn't be very courteous use of build daemon resources.

---

