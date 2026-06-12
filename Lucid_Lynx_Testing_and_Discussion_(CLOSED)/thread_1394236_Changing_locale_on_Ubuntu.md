---
title: "Changing locale on Ubuntu"
date: 2010-01-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by slakkie on 2010-01-30
Hello all,

I've been trying to change my locale on Ubuntu. [The Debian way](http://people.debian.org/~schultmc/locales.html) doesn't work. I copied my Debian locale.gen over to my Ubuntu box, ran locale-gen and it seems it does not look at the file. See: [http://pb.opperschaap.net/166](http://pb.opperschaap.net/166)

According to [this blog](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html) I need to edit the file */var/lib/locales/supported.d/local*, to no avail. The contents of the file:

```

cat /var/lib/locales/supported.d/local
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8

```

As you can see, this is not what locale-gen generated (see the pastebin link above). 

Running dpkg-reconfigure on the locales package solves nothing, it just runs locale-gen. 

While typing, I figured it out :)

There are language packs installed on my system, I removed that one and then ran locale-gen again. It now respects the /var/lib/locales/supported.d/local file. So it is working.

There is still one thing I don't get. Why did they switch from /etc/locale.gen to /var/lib/locales/.. ?

---

### Post by seeker5528 on 2010-01-30
> **slakkie said:**
> There is still one thing I don't get. Why did they switch from /etc/locale.gen to /var/lib/locales/.. ?

My best guess would be because it is easier/less error prone if package maintainers can install remove smaller targetted *.d files in /var/lib/locales to tell the system which locale data should be generated for a certain area, instead of having to parse and add/remove lines from a single locale.gen file as different language packs are installed/removed. Theoretically this should be easier for the user too if the user wants to create a custom list of locales to generate the data for independently of the language packs that are installed because they should be able to create their own file with their own list of locales instead of having to edit locale.gen and later having that file getting over written or failing to get overwritten when updates/new language packs are installed. 


Later, Seeker

---

