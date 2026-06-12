---
title: "Incorrect Ram Asus 1201N"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by GlasGhost on 2010-10-27
On 64 bit Lynx, I've got a wrong amount of detected ram:

it says around 750Mb

when it should be around 2048Mb

---

### Post by Iowan on 2010-10-29
Moved to Installation & Upgrades by request.

---

### Post by psusi on 2010-10-29
What do you mean "it" says 750mb?  What does free -m say?

---

### Post by GlasGhost on 2010-10-29
> **psusi said:**
> What do you mean "it" says 750mb?  What does free -m say?

```
glas@1201N:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           745        725         19          0          9        142
-/+ buffers/cache:        573        171
Swap:         1953         72       1880
glas@1201N:~$
```

kinda scary I only go 20mb free, also dont get confused I made my swap 2gb.

---

### Post by psusi on 2010-10-30
What does your bios say when you boot up?  Also try running a memtest.

---

### Post by GlasGhost on 2010-10-30
> **psusi said:**
> What does your bios say when you boot up?  Also try running a memtest.

System Memory:
Installed Size: 2048Mb

---

### Post by psusi on 2010-10-30
Then run memtest86.  Most likely you have some bad ram at the 750 mb mark so the bios limits what it tells the kernel so it doesn't use the bad ram.

---

### Post by GlasGhost on 2010-10-30
Found the problem [here]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/HPMini311#Additional%20Notes")

Just turn off all visual effects, they apparently use 1gb of your ram on this machine.

---

### Post by psusi on 2010-10-30
> **GlasGhost said:**
> Found the problem [here]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/HPMini311#Additional%20Notes")

Just turn off all visual effects, they apparently use 1gb of your ram on this machine.

No, it is reporting 750 mb of total ram, not free ram.

---

### Post by Drewvt on 2010-11-01
It is part of the bios reset that is a well-known problem with this machine. All you have to do is go into the bios, choose "restore default settings", save and exit. You will have 2gb ram instead of 750mb again.

---

### Post by GlasGhost on 2010-11-04
> **Drewvt said:**
> It is part of the bios reset that is a well-known problem with this machine. All you have to do is go into the bios, choose "restore default settings", save and exit. You will have 2gb ram instead of 750mb again.

There was a farmer who had a dog and bingo was his name oh!
B-I-N-G-O
B-I-N-G-O
And Bingo was his name oh!

thx Drewwt!

---

