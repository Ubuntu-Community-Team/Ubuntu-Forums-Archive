---
title: "Can´t edit visudo file"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-08-15
After having a few problems installing Ubuntu Studio Hardy, I got there. Trouble is, no privileges. I tried to work this out on another thread and have been getting somewhere. Problem now is this. This is what I have tried and posted from my last thread which can be found here:

[html]http://ubuntuforums.org/showthread.php?t=890786[/html]

> I have been booting into the recovery kernel, going to a terminal shell and plugging in;

```
visudo
```It shows me the file but won´t let me edit it. I am wanting to try adding;

```
ustudio ALL=(ALL) ALL
```under the line that says;

```
root ALL=(ALL) ALL
```... an idea from this page ...

[html]http://www.pendrivelinux.com/2007/10/05/how-to-add-a-user-to-the-sudoers-list/[/html] ustudio is my username, naturally. Seems obvious I need to put myself on the sudoers list, but no matter what I try, can´t seem to edit that file to do that. Getting very close and have come far with this but not quite there yet .... any ideas?

---

### Post by wilbbe01 on 2008-08-15
You do know how to use vi right?

---

### Post by iaculallad on 2008-08-15
On your terminal:

```
sudo visudo
```

---

### Post by Bucky Ball on 2008-08-15
That is the point I am trying to make, iaculallad. This is the result ...

```
$ sudo visudo
[sudo] password for ustudio: 
ustudio is not in the sudoers file.  This incident will be reported.
$
```Boot into recovery and run ´visudo´ as root and can´t edit that file to put myself in sudoers list. Is there some other way of doing this? I am presuming I am on the right track. There seems to be no other problem apart from the fact I can´t access any drives. A rather big problem ...

[quote=wibbe01]You do know how to use vi right?[/quote]

Is there something I am missing here, wibbe01? Any tips gratefully accepted.

---

### Post by jerome1232 on 2008-08-15
You are pressing 'i' to get into insert mode right?

---

### Post by kevstar31 on 2008-08-15
nano /etc/sudoers

---

### Post by Bucky Ball on 2008-08-15
> **jerome1232 said:**
> You are pressing 'i' to get into insert mode right?

In recovery boot you mean?

---

### Post by jerome1232 on 2008-08-15
yes when you boot into recovery mode, then type visudo, that launches vi, inwhich you have to hit 'i' to actually start editing.

---

### Post by wilbbe01 on 2008-08-15
Sorry I didn't say more earlier, I wanted to try and figure out where you were getting stuck before I tried to help much more than that.

I'm not sure how the recovery mode works as I've never used it.  When you tried visudo without the sudo were you able to get to the editing window?  What I was asking innitially about understanding vi, and what that post above this one is saying is once you type "visudo" you are given the sudoers file in vi.  In order to enter things in vi you have to hit the i key (there are others, but i is all you need to know).  Once you press i you should be able to type what you want where you want it.  After you have finished typing you can hit the escape key, followed by a ":wq" (without the quotes.  After you type the colon you should see a colon in the bottom left of the window.  After typing the ":wq" you hopefully are sent out and the file is saved.  If it tells you it couldn't save the file, also at the bottom of the screen (usually in red) then you don't currently have permission to edit the file.  I can't imagine the sudo is necessary when in the recovery, but I'm not really sure how that works.  Tell me if you can get any editing working, and I'll be back in a bit.


Edit: And fyi the wq stands for "write quit"

---

### Post by jerome1232 on 2008-08-15
> **kevstar31 said:**
> nano /etc/sudoers

nano doesn't work for the sudoers file, you have to use visudo.

---

### Post by Bucky Ball on 2008-08-15
> **wilbbe01 said:**
>  In order to enter things in vi you have to hit the i key (there are others, but i is all you need to know). 

Thanks for that. That is where I am missing I think. Is the line I am wanting to insert the way to go, before I do it?

ustudio ALL=(ALL) ALL

Underneath the line that says:

root ALL=(ALL) ALL


Duh, might check on my laptop which is working perfectly and see what the settings are on that for comparison (this is happening on my desktop just to refresh memories). :)

---

### Post by wilbbe01 on 2008-08-16
> ustudio ALL=(ALL) ALL

If your username is ustudio then yes that is accurate.

Also, to save and quit you need to hit escape, then type ":wq"

---

### Post by Bucky Ball on 2008-08-16
I am going to mark this as solved for the moment and post again if I have trouble later.

adding the 

```
ustudio ALL=(ALL) ALL
```

line seemed to have worked as I can now open from inside terminal on my regular desktop using

```
sudo visudo
```

whereas I couldn't before. Now seems I need to mount my hard drives and set some permissions there. I can also launch nautilus GUI whereas I couldn't before.

Rather than change subjects mid-stream and confuse people, as I say, will post again if I experience any more probs but this bit should be cool ... (he said! lol), so, for now, thanks once again all ... :))

---

### Post by wilbbe01 on 2008-08-16
I'm glad to hear you got it working, good luck with the rest of your project.

---

