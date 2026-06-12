---
title: "Why up until now Lucid Lynx still doesn't support metadata &quot;date created&quot;"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubfu on 2010-03-13
Up until now , why ubuntu doesn't support date created ? [http://brainstorm.ubuntu.com/idea/6013/](http://brainstorm.ubuntu.com/idea/6013/)
[http://brainstorm.ubuntu.com/idea/8763/](http://brainstorm.ubuntu.com/idea/8763/)
[http://brainstorm.ubuntu.com/idea/22777/](http://brainstorm.ubuntu.com/idea/22777/)

I am wondering , why can't it be implement ? 
As I know the most basic timestamp is 

date modified
date created
date accessed
date transfer

It's really important to know which file is my last transfer , last created and last modified.Why no one really care much about it ?

---

### Post by VMC on 2010-03-13
If I'm reading you right, add it here, correct?

If that's what your referring to, then I'm all for it. I would rather see the date created than anything else, to be honest.

---

### Post by slakkie on 2010-03-13
Creation date, why would you want to have that?

Last modified is enough.
Date transfered? Why would one implement that? 
And you can have a look at the last time a file was accessed:

```

$ stat -c "access: %x modified: %y change:%z" .env.local
access: 2010-03-12 17:40:19.000000000 +0100 modified: 2010-03-03 10:20:54.000000000 +0100 change:2010-03-03 10:20:54.000000000 +0100

$ stat -c "access: %X modified: %Y change: %Z" .env.local
access: 1268412019 modified: 1267608054 change: 1267608054

```

---

### Post by ubfu on 2010-03-13
> **slakkie said:**
> Creation date, why would you want to have that?

Last modified is enough.
Date transfered? Why would one implement that? 
And you can have a look at the last time a file was accessed:

```

$ stat -c "access: %x modified: %y change:%z" .env.local
access: 2010-03-12 17:40:19.000000000 +0100 modified: 2010-03-03 10:20:54.000000000 +0100 change:2010-03-03 10:20:54.000000000 +0100

$ stat -c "access: %X modified: %Y change: %Z" .env.local
access: 1268412019 modified: 1267608054 change: 1267608054

```

Seems like you didn't read the link of brainstorm.Here I post again 
[http://brainstorm.ubuntu.com/idea/6013/](http://brainstorm.ubuntu.com/idea/6013/)
[http://brainstorm.ubuntu.com/idea/8763/](http://brainstorm.ubuntu.com/idea/8763/)
[http://brainstorm.ubuntu.com/idea/22777/](http://brainstorm.ubuntu.com/idea/22777/)

I am sure everyone really wanted a file to be sort accordingly with those timestamp , even window xp year 2001 have it.Now is 2010 .

---

### Post by Longinus00 on 2010-03-13
> **ubfu said:**
> Up until now , why ubuntu doesn't support date created ? [http://brainstorm.ubuntu.com/idea/6013/](http://brainstorm.ubuntu.com/idea/6013/)
[http://brainstorm.ubuntu.com/idea/8763/](http://brainstorm.ubuntu.com/idea/8763/)
[http://brainstorm.ubuntu.com/idea/22777/](http://brainstorm.ubuntu.com/idea/22777/)

I am wondering , why can't it be implement ? 
As I know the most basic timestamp is 

date modified
date created
date accessed
date transfer

It's really important to know which file is my last transfer , last created and last modified.Why no one really care much about it ?

If you read the links you'd have seen that this is due to the underlying file system. You can see a list of filesystems that support such a feature here. [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Metadata](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Metadata)

Even if you're running a file system like ext4, which supports creation timestamps, you still need the underlying tools and system calls to support it (e.g. stat). Basically, you're going to want to talk to the kernel and gnome people if it's not implemented yet.

---

### Post by slakkie on 2010-03-13
> **ubfu said:**
> Seems like you didn't read the link of brainstorm.Here I post again 
[http://brainstorm.ubuntu.com/idea/6013/](http://brainstorm.ubuntu.com/idea/6013/)
[http://brainstorm.ubuntu.com/idea/8763/](http://brainstorm.ubuntu.com/idea/8763/)
[http://brainstorm.ubuntu.com/idea/22777/](http://brainstorm.ubuntu.com/idea/22777/)

I am sure everyone really wanted a file to be sort accordingly with those timestamp , even window xp year 2001 have it.Now is 2010 .

I read them, I just don't agree with them. Creation date is not important information to me. Transfered date, I would like to know how you would implement that, cp'ing is transferring, ftp, rsync, etc etc. And why would you want to update something to show you when a file was last transferred? I don't get it.

---

