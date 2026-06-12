---
title: "Disable Recent Documents in Places"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2010-04-08
I am a little stumped here. It used to be as simple as:

```

rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
sudo chattr -i ~/.recently-used.xbel
```

Unfortunately, due to an issue involving ecryptfs_ioctl, chattr/lsattr is not working with an encrypted home as detailed in this bug:

Inappropriate ioctl for device while reading flags on
[https://bugs.launchpad.net/ecryptfs/+bug/469664](https://bugs.launchpad.net/ecryptfs/+bug/469664)

Setting read-only permission &/or changing ownership on the file does not do anything to help the situation.

Can anyone think of a crafty way around this? And yes, the ability to do this should simply be exposed as a UI option somewhere!

---

### Post by tekstr1der on 2010-04-08
Forgot to mention another old trick. Deleting the file and replacing it with a directory of the same name is also a dirty workaround, but generates GTK errors on any future .recently-used.xbel file operations. Not a good solution.

---

### Post by emarkay on 2010-04-08
I thought Bleachbit took care of this and more...

Though it would be nice to make "history" items like this "save optional".

---

### Post by tekstr1der on 2010-04-08
Well, bleachbit can clear the recent document list. But this can be accomplished a number of easy ways. The question here is how to disable it entirely whilst using ecryptfs?

---

### Post by tekstr1der on 2010-04-27
Anyone have any insights?

---

### Post by wojox on 2010-04-27
I use this in karmic haven't upgraded yet:

```

rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel

```

---

### Post by crjackson on 2010-04-27
I have mine disabled without any issues.  However, I always install Ubuntu-Tweak and let it take care of the dirty work.  I really like this app. It has saved me a boat load of time.

[http://www.ubuntu-tweak.com](http://www.ubuntu-tweak.com)

Here is the repository entry.

[http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) for your software sources

---

### Post by wojox on 2010-04-27
There's also:

```

touch ~/.gtkrc-2.0
sudo gedit ~/.gtkrc-2.0

```

Then add:

```
gtk-recent-files-max-age=0
```

---

### Post by tekstr1der on 2010-04-27
> **wojox said:**
> There's also:

```

touch ~/.gtkrc-2.0
sudo gedit ~/.gtkrc-2.0

```

Then add:

```
gtk-recent-files-max-age=0
```

Uh-huh. Thank you wojox. This workaround is almost as good as what I had used previously and does not depend on the filesystem. Hopefully the kernel bug which is the root cause of my question gets fixed and SRU'ed for Lucid. Immutable files have more uses than just the issue discussed in this thread!

---

### Post by x-shaney-x on 2010-04-27
Argh!  I remember seeing a solution something like this ages ago and have never been able to find it since.

Though you wouldn't really use sudo to edit a file in your home directory would you?

---

### Post by tekstr1der on 2010-04-27
> **x-shaney-x said:**
> Though you wouldn't really use sudo to edit a file in your home directory would you?

True. Since I did mark this as solved perhaps I should add that I simply did:

```
gedit ~/.gtkrc-2.0
```

this creates the file. No need to touch prior. Then add:

```
gtk-recent-files-max-age=0
```

---

