---
title: "[SOLVED] No username in /home directory"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-08-15
Hi all. Something kinda bizarre ...

Just installed UbuntuStudio Hardy on the desktop and after a bit of screwing around, finally got it booting okay. With feelings of pride and achievement, I checked out the cool new logon screen. Time to explore, so I type in my username and password and ... wrong. But I just wrote them down? Try again. Try some variations even though the correct ones are staring back at me from the page. Hmm.

Boot into recovery and open shell. Type in

```
 ls /home
```

All that is in there is ```
lost+found
```. No user directory. Took me a second to realise what was missing, and before I did, I also tried:

```
passwd mycorrectlogin
```

All to no avail, because that user directory should be in /home.

I really need some help with this puzzle as I can't log in and can seem to find no info so far in my searching. When I formatted the partitions, I created 10GB / and 50GB /home. That is it. Didn't think I needed to create any more than that (I have another 80GB fat32 in the machine for storage and swap with XP).

Little help? :confused:

---

### Post by Bucky Ball on 2008-08-15
I input this in a shell;

```
 useradd -m newusername -p yournewpassword
```

and successfully created

```
 /home/newusername
```

so the directory looks like

```
 dir /home
lost+found  newusername
```

... but still won't let me log in with new details.

?

---

### Post by iaculallad on 2008-08-15
Try this, on your terminal:

```
sudo usermod your_user_name --home=/home/your_user_name
```

---

### Post by Bucky Ball on 2008-08-15
Hmm. That is just giving me a list of options to use with 'usermod', but getting closer I think. Maybe syntax ...

Checked for accuracy. Any other thoughts?

---

### Post by Too Late on 2008-08-15
Well, "man usermod" says that the correct syntax is:
```
sudo usermod --home /home/your_user_name your_user_name
```

---

### Post by Bucky Ball on 2008-08-15
> **Too Late said:**
> Well, "man usermod" says that the correct syntax is:
```
sudo usermod --home /home/your_user_name your_user_name
```

That is throwing this:

```
/home/username does not exist
```

Yet when I input dir /home, directory looks like;

```
lost+found  username
```

I tried

```
usermod username -m /home/username
```

and received the same response.

---

### Post by Bucky Ball on 2008-08-15
> **Bucky Ball said:**
> I input this in a shell;

```
 useradd -m newusername -p yournewpassword
```and successfully created

```
 /home/newusername
```so the directory looks like

```
 dir /home
lost+found  newusername
```... but still won't let me log in with new details.

?

I think it was when I performed this step that I then should have created a new password to go with it. It was as simple as;

```
 useradd -m newusername -p yournewpassword
passwd newusername
```

then you get to set a password then you're in! Success. Thanks for your ideas people. :KS

---

