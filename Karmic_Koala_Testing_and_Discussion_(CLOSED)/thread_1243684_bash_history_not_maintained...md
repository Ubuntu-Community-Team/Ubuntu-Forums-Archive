---
title: "bash history not maintained.."
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-08-18
whenever i close the terminal
i lose my bash history.. what is going on?

---

### Post by taavikko on 2009-08-18
have you touched your .bashrc in any way?

---

### Post by puccaso on 2009-08-18
no not at all..

---

### Post by jpeddicord on 2009-08-18
In your terminal, after you've run a few commands, run:```
history | tail
```

Does that show your last ten commands?

---

### Post by nikopol on 2009-09-13
same problem here. history | tail works only as long as you don't kill the terminal.
Seems like it is not saving it to file when you exit terminal. Strangely it works fine for root - the bug is only for the main user

---

### Post by nikopol on 2009-09-17
had another look at this - it would seem that both sudo and normal user are
accessing the same file meaning that .bash_history was unwritable to the user. chmodding it does not really resolve the problem as you end up with a mixed history of the sudo commands and the normal user commands. I guess that there used to be two distinct .bash_history files for this? Not sure what's happened exactly though.

---

### Post by GokuH12 on 2009-09-18
yeah! now that explain whats going on with the history for normal user

---

### Post by amano on 2009-09-18
Is there a bug filed for this?

---

### Post by dino99 on 2009-09-18
> **amano said:**
> Is there a bug filed for this?

i've filled one but for different things: i hate all these duplicates in it.

---

