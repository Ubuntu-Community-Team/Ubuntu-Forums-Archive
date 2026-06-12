---
title: "Halt at rc.local"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by problems on 2007-06-07
Hi people.

Upgraded dapper to feisty. Everything went just fine. The boot process now halts when calling the rc.local script.

The script itself only reads **exit 0** inside the file.

I can access the filesystem using recovery means, so i dont need help with that. What i need help with is WHAT to edit to get it going in normal boot.

Thanks for your time and hope you can help me.

---

### Post by taurus on 2007-06-07
Can you post it here to see what's wrong with it?  Otherwise, you can move it somewhere else so the system doesn't have to read it when it boots.

---

### Post by problems on 2007-06-07
> **taurus said:**
> Can you post it here to see what's wrong with it?  Otherwise, you can move it somewhere else so the system doesn't have to read it when it boots.



thanks for the reply. What do you need me to post? The contents of the file? Its **exit 0**

Move what somewhere else? the rc.local file? I chmod' it to -x. So it shouldnt run at all. Still halts at the same point when calling it.

I've seen some more posts about the issue in the past. Sadly i cant find them now.

---

### Post by taurus on 2007-06-07
Assuming you are in the directory where rc.local is, run
```
gksudo gedit rc.local
```
and place a # in front of the line to comment it out.

Otherwise, 

```
sudo mv rc.local /root
```

---

### Post by problems on 2007-06-07
i commented the line out, the system gets stuck at the same point.

moved it away too, same results.

im pretty sure there were TONS of posts of people getting stuck at the rc.local line.. why on earth i cant find any..

---

