---
title: "Feisty to Gutsy upgrade hangs. What to do?"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by Threlkeld on 2007-12-31
I have a fairly standard dual-boot desktop (XP & Feisty)
I made sure that Feisty was up to date and then started the upgrade from Update Manager. After the first step ('Preparing the upgrade') the process puts up a notification screen about  support for some apps. being ended. When that is closed the progress indication has moved to the next step ('Modifying the Software channels') and shows an almost complete progress bar with 'Asking for confirmation'. There, it just hangs.
After I terminated the process I found that Ubuntu booted OK but the Update Manager offered me 571 updates. If I try to install these I'm warned that only a partial update is possible, and in fact the process stalls without any update being installed, as far as I can tell. Both these failures, upgrade and update, reproduce on each attempt in the same way.
So, I can no longer update 7.04, nor can I upgrade to 7.10.
Can I return the system to 7.04 (I wish I'd left it well alone), or can I unblock the upgrade process in any way? Or am I looking at a reinstall to get off this hook?

---

### Post by taurus on 2007-12-31
Check your /etc/apt/sources.list to make sure you don't have any 3nd party repos in there.  If there are, you need to comment them out by placing a # in front of them.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Threlkeld on 2008-01-01
I've now tried that suggestion.
Alas, the upgrade still fails in the same way.
I notice that most of the entries in that file, including the only one not commented-out, refer to gutsy.
Does any kind soul have any idea what I should try next?

---

### Post by PmDematagoda on 2008-01-01
This is not a real solution, but in my opinion, I believe the best thing that you can do is to do a clean reinstall of Ubuntu, that would be less troublesome than trying to fix the broken upgrade.

---

### Post by Threlkeld on 2008-01-01
Ouch! but I can see the logic of your suggestion. Thing is, this desktop is (or rather, was) an almost straight  7.04 install with no elaboration, and even so the upgrade process just broke. I think if I'm going to reinstall I might reinstall 7.04 and leave 7.10 to mature for a while, say until 8.10   :-)   
I'm certainly not about to try to upgrade any laptop after this experience; my life has enough boring and pointless hours in it already.
Is there any reason to upgrade? I'm not a geek nor do I like fancy eye-candy effects, so perhaps I shouldn't have even thought about 7.10?

---

### Post by PmDematagoda on 2008-01-02
```
Is there any reason to upgrade?
```
A few reasons are:-
1) More updated software and core.
2) To get more features.
3) Usually being more stable and faster.

But these reasons are not really significant factors to consider when upgrading since it is your own thinking and uses of the OS that really count. So in a nutshell, if Ubuntu 7.04 suits your needs and you are happy with it, then it is really not essential to upgrade to Ubuntu 7.10 until support for Ubuntu 7.04 runs out which is not until the October of 2008.

---

### Post by Em-Buntu on 2008-01-02
I upgraded from Feisty to Gutsy, but had I known what I know now, I would have stayed with Feisty, skipped Gutsy and awaited for Hoary.
There is definitely not a performance or stability enhancement from Feisty to Gutsy.

---

