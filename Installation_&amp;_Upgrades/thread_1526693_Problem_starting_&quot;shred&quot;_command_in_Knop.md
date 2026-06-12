---
title: "Problem starting &quot;shred&quot; command in Knoppix"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by finsyourfriend on 2010-07-08
Greetings all.

I have used Knoppix several times before to wipe some drives but for some reason it's not working as planned this time. I am able to successfully boot into Knoppix and open up a shell from the ADRIANNE screen reader, but when I try to shred the drive by typing the following for the SATA hard drive:

```
shred -vfz -n 5 /dev/sda
```

or 

```
shred -vfz -n 5 /dev/sda0
```

or 

```
shred -vfz -n 5 /dev/sda1
```

(You get the idea) the blinking cursor prompt just goes down one line and keeps blinking; nothing happens.

Any enlightenment would be much appreciated.

Thanks!

---

### Post by PcNeumo on 2010-07-08
You may want to try asking this question in the Knoppix forum .....

[http://www.knoppix.net/forum/forums/6-General-Support](http://www.knoppix.net/forum/forums/6-General-Support)

 This being an ubuntu forum and all, just a thought

---

### Post by finsyourfriend on 2010-07-08
You are exactly right! ;) I actually just figured it out on my own. 
Thanks for the Knoppix forum reference.

---

### Post by PcNeumo on 2010-07-08
Glad to hear you got it resolved,
Now that you've piqued our curiosity, what was the problem / solution?

---

### Post by finsyourfriend on 2010-07-19
Greetings,

Actually, the problem was that the hard drive I was trying to shred wasn't mounting at all.
Shredding a different drive worked like a charm.

Ciao for now! ;)

---

### Post by powell on 2010-07-20
Wait, what? Why the hell were you trying to ask a question about Knoppix in the Ubuntu forums...

---

