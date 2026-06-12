---
title: "help! use of home partition - user ID problems"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-11-23
I have just done a new install of ubuntu 10.10  into a machine which has a separate partition for /home. The advanced selections for partitions seemed ok, the install went ok afaik also and /home does seem to be correctly in fstab.

However, the machine has (had) two users, both currently were admin users, 'user1-admin' and 'user1'.

I did the new install and used the (new install) ID of 'user1-admin' with the existing password. However, I have missed something because after login I get error messages suggesting things are not set up, at least for the install user. 

And anyway, I now realise I do not know how to arrange correct recognition of the pre existing users with this type of install, when /home is nominated for the install target.

I am on a live CD just now..... help would be much appreciated!
tia

---

### Post by arubislander on 2010-11-23
Boot in recovery mode... choose the root terminal selection (I think it's called something like that) and type
```

# chown -R yourusername.yourusergroup /home/yourusername

```

where *yourusername* should be replaced by your user name and *yourusergroup* by your user group name (which is most likely the same as your username)

---

### Post by candtalan on 2010-11-23
> **arubislander said:**
> Boot in recovery mode... choose the root terminal selection (I think it's called something like that) and type
```

# chown -R yourusername.yourusergroup /home/yourusername

```

where *yourusername* should be replaced by your user name and *yourusergroup* by your user group name (which is most likely the same as your username)

Thanks for your reply! I seem to have recovered the situation. I used a terminal to add a new user2 making an intended total of now 3 users. not ideal because the user2 by default happened to get allocated the same uid as my legacy user1 (1001). However, at least I could log in fully ok with the new user2.

I then used gui admin users to modify the legacy user to use the correct uid (1002) which made legacy user functionl ok, and I logged into it. 

I was then able to edit the newly created user2 to have a different uid from my legacy user1, the new uid for user2 set to 1003.
legacy user1 uid was/is 1001

Both legacy users uid 1001 and 1002 are now functional and I intend to delete the unwanted user2 (1003) soon.

It seems I should have used a completely different user name during the install process? Maybe I got complications because I have two users in this system, and it has been previously upgraded too.

I guess the installation user was uid 1000.

Thanks again

---

