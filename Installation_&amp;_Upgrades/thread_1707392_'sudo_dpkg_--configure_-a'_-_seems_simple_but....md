---
title: "'sudo dpkg --configure -a' - seems simple but..."
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by jardin-de-cocagne on 2011-03-15
Hello!

On Ubuntu 10.04 LTS - the Lucid Lynx
I had troubles updating, since I shutted down the computer while an update seemed 'stuck'. Like, the computer stayed on all night and was still updating something.

But now, what I understood is that I can't update any program. It gives me this message:

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]
I learned that Sudo gives permission to users. I searched with Google for answers and found a forum thread written in chinese and japanese language. I translated approximately with Google too and tried this simple string of code.

I tried using ''Aptitude' to find the problem. I discovered that there was ONE 'Obsolete and Locally created Package'. I cannot delete it because it is 'read-only'. I think I need more permissions as a user in order to repair the problem.

But how, since there's only one user?

I was searching for the answer and I'm pretty sure it happened to someone but I didn't found any complete help.

If you can help me, it will be really appreciated!

---

### Post by dabl on 2011-03-15
In a terminal window, issue this command:

```
sudo apt-get clean
```

Does it give an error -- if so, please post it?

---

### Post by jardin-de-cocagne on 2011-03-15
Hello!

I tried the string of code and then it seems to work.
I tried to update or download something else and it didn't worked. The same error occured.
Oups!

I was thinking about 'forcing' with a code to cancel the unfinished installation. I don't know too much how to do this.

---

### Post by dabl on 2011-03-15
> **jardin-de-cocagne said:**
> Hello!

I was thinking about 'forcing' with a code to cancel the unfinished installation. I don't know too much how to do this.

Try

```
sudo apt-get -f install
```

then if there is no error

```
sudo dpkg --configure -a
```

then if no error

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by rizky_ghardoe on 2011-03-16
> **dabl said:**
> In a terminal window, issue this command:

```
sudo apt-get clean
```Does it give an error -- if so, please post it?

yeah, nice share bro,
thanks a lot :)

---

### Post by uRock on 2011-03-16
> **jardin-de-cocagne said:**
> Hello!

On Ubuntu 10.04 LTS - the Lucid Lynx
I had troubles updating, since I shutted down the computer while an update seemed 'stuck'. Like, the computer stayed on all night and was still updating something.

But now, what I understood is that I can't update any program. It gives me this message:

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]
I learned that Sudo gives permission to users. I searched with Google for answers and found a forum thread written in chinese and japanese language. I translated approximately with Google too and tried this simple string of code.

I tried using ''Aptitude' to find the problem. I discovered that there was ONE 'Obsolete and Locally created Package'. I cannot delete it because it is 'read-only'. I think I need more permissions as a user in order to repair the problem.

But how, since there's only one user?

I was searching for the answer and I'm pretty sure it happened to someone but I didn't found any complete help.

If you can help me, it will be really appreciated!

Did you run the **sudo dpkg --configure -a** command?

---

### Post by jardin-de-cocagne on 2011-03-19
Hello!

Thank you for all of your support!

A friend visited us and fixed the problem. I did asked him what he has done to repair that problem and he told me that he written in the terminal that simple command I was asked to write.
It's weird, because I've done the same and now the problem is resolved by him, haha.

He did took a look in Aptitude, just before, to verify what problem it was...
And then, he wrote the command : sudo dpkg --configure -a


Everything is working now!


Thank you again.

---

