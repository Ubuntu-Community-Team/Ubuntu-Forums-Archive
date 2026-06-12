---
title: "Can't save changes to sources.list"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by endokrin on 2006-02-18
I'm trying to install Tor... and it kept trying to look for the Ubuntu Install CD Rom.

So I found out it was a problem with my source list.  

```

sudo gedit etc/apt/sources.list
password: XXXXXXXXX

```

The list opens up and I find the entire list was blank.. nothing there!

Anyways, I went to [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) and copied what was there (for Breezy) into sources.list

I hit save, and it gives me a popup: Could not save the file "/home/user/etc/apt/sources.list"

What's the problem?

---

### Post by 5-HT on 2006-02-18
Hi, you are just missing one forwardslash in there.
Try this: ```
 sudo gedit /etc/apt/sources.list 
```

What was happening was that without that first forwardslash, you were trying to create and edit a new file in the current directory (your home directory), not the proper one residing in /etc.

Hope that helps.

---

### Post by endokrin on 2006-02-18
Hey thanks for the help!  I got everything working.

There is one thing I've learned now after switching to Ubuntu.. and that is I need to pay attention to the details.. So I can stop making myself look like an idiot online for forgetting a forwardslash!

Thanks.

---

### Post by 5-HT on 2006-02-18
No worries, I'm always making little typos then spending twenty minutes or so trying to figure out why something isn't working...

Also do you know about TAB completion?

You can start typing a command/filename and press TAB. If what you have entered is unique, after you press tab the rest of the command/filename will automagically appear (if the entry is not unique, press TAB twice and a list will show you all available options matching the string). 

It's great because 1) It saves typing and 2) you don't need to worry about little typos so much.

HTH

---

