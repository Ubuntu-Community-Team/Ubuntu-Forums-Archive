---
title: "Dualboot scenario, 2 SATA drives, Windows drive not plugged in when installing Ubuntu"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by chrilleh on 2006-06-17
I can't get my Windows xp pro x64 to boot when selected from the Grub menu.
This is the scenario:

I had Windows installed on my 200gb sata drive plugged in at SATA1.
I removed this drive completely, plugged in my 300gb sata drive at SATA1 and installed Ubuntu 6.06. Ubuntu works flawless! 

Now the problem. I can't boot windows. I tried with this in my menu.lst
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title              Windows XP Pro
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
root               (hd1,0)
chainloader        +1

### BEGIN AUTOMAGIC KERNELS LIST

```

But that gave me "NTLDR missing" error when trying to boot Windows.


I have seen alot of people talking about where to install grub, on the mbr or somewhere else etc? I dont even know where I installed it? Did I even get a change to choose that? But i guess it's on my 300gb drive then, because thats the only one plugged in when installing ubuntu?
Now is this is a problem for me? where its installed or so?


How should i solve this? should i physically rearrange the drives? what should i put in my menu.lst? I'll be glad for any help i can get :)

Thanks

---

### Post by confused57 on 2006-06-17
You might want to change your menu.lst to look like this:
```
title              Windows XP Pro
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

It might make a difference to have the root line just below the title.  You'll need to keep Ubuntu on SATA1 & boot to it 1st.

---

### Post by chrilleh on 2006-06-17
I got it working! with the following:

```

title              Windows XP Pro x64
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
root               (hd1,0)
chainloader        +1

```

I had not understood that the root should still point to the "original" hd1.

---

