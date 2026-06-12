---
title: "Frequent Freeze-ups"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by rdking on 2005-04-05
ok, so not a noobie or anything, but do have a question.  I have had a return to ubuntu, after a slackware (my first attempt at no gui configurable distro), started be become unstable.  I had recently run warty for about 5-6 months and ugraded it without problems to hoary.  However, as I don't treat my cd's well, i needed to burn a new copy and opted for hoary.  

So my question is this.  my computer has been crashing roughly every half hour, regardless of wm, though usually when a network connection is in use.  I have an Nvidia card with the drivers from the ubuntu hoary repos.  I have read that there are instability problems with this on a number of posts, but am trying to identify the actual reason for the crashes, to see if I am in the same boat.  What logs should I be looking at, and is there a way to simply log the errors, to save me going through 300 lines of code looking?

any help would be great.  And I just want to add, happy to be back.

---

### Post by Nis on 2005-04-05
Try disabling the nvidia driver:
```

sudo nvidia-glx-config disable

```
Restart X and see if the problem goes away.  If so then it's the Nvidia driver.

If the problem persists, try removing the network cable since you said it usually happens during a network connection.  If the problem goes away then try a different network card (borrow one from a friend if possible) and see what happens.  You might have a defective network card if the lockups stop happening when you use a different card.

On an off chance, how much RAM do you have and how many DIM slots have you filled?  I ask because when I filled all three DIM slots on my motherboard I was getting hard lockups.  As soon as I removed some RAM from a DIM the lockups stopped happening.

---

### Post by rdking on 2005-04-06
after some more chrashes, I have realized that resizing windows is often the activity which crashes the system.  If I leave things as is, the number of crashes diminishes.  What logs should I look at, and how do I evealuate the actual problem?

---

### Post by Leif on 2005-04-06
As said before, try switching to nv instead of nvidia. Also, what programs do you have open when it crashes ? One bug going around right now is firefox and nvidia.

---

