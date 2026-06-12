---
title: "Update trouble"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Ewingo401 on 2009-04-01
Hey guys, I'm having trouble running updates in 9.04 on both my laptop and desktop.  It seems to be installing all updates except for one (its an Ekiga update) that it just leaves on my list.  I'm providing a screen shot in case that may help.  But I was wondering if there is anyway to make it do that update or at least to remove it from the list (I'm kinda OCD that way lol).  Thanks in advance for any help you can give.

---

### Post by 73ckn797 on 2009-04-01
I have had similar issues with some regular updates not installing or update manager not completing or doing anything.

Open a terminal and enter:

```
sudo apt-get update
```

Then after that finishes enter:
```
sudo apt-get upgrade
```

See if that works.

---

### Post by Ewingo401 on 2009-04-01
> **73ckn797 said:**
> I have had similar issues with some regular updates not installing or update manager not completing or doing anything.

Open a terminal and enter:

```
sudo apt-get update
```

Then after that finishes enter:
```
sudo apt-get upgrade
```

See if that works.

Thanks for the advice, but that didn't quite do it.  It did install some updates that I didn't previously see in the update manager, but the Ekiga one is still there, refusing to install.

---

### Post by 73ckn797 on 2009-04-01
Do you use Ekiga?

Maybe try and logout or restart.

---

### Post by Ewingo401 on 2009-04-01
Wow...I didn't even think to remove Ekiga since I don't even use it.  I removed it, rebooted, and its gone!  Haha, why is it the easiest solutions that always evade me?  Thanks for all your help.

---

### Post by 73ckn797 on 2009-04-01
That is why these forums are so helpful. One may not have the answer(s) but can ask questions which stir others on to a solution.

---

### Post by ktp on 2009-04-01
> **Ewingo401 said:**
> Hey guys, I'm having trouble running updates in 9.04 on both my laptop and desktop.  It seems to be installing all updates except for one (its an Ekiga update) that it just leaves on my list.  I'm providing a screen shot in case that may help.  But I was wondering if there is anyway to make it do that update or at least to remove it from the list (I'm kinda OCD that way lol).  Thanks in advance for any help you can give.

this is known. something about dependency not being there or something.

---

