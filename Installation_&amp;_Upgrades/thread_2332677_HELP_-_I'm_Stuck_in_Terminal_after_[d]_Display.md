---
title: "HELP - I'm Stuck in Terminal after [d] Display"
date: 2016-08-02
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-08-02
Upgrading UbuntuStudio from v16.10 from v14.10 and saw some file to be replaced. It asked did I want to;

1. Keep the file [n]
2. Use Maintainers Version of file [y]
3. or Display [d]

I chose [d] to display, and could not get back to the prompt. So, not knowing what I was doing, I went to the Top Menu Bar and chose "Clear Scrollback and Reset".

Now to keep the Upgrade going, and not corrupt it, HOW do I get back to where it was???

Thanks!
Rick

---

### Post by Bucky Ball on 2016-08-02
Are you really using 16.10? It's not released until October. 

Unsure how an upgrade from the out of support 14.10 to 16.10 is possible ... :-k

---

### Post by Rick St. George on 2016-08-02
Bucky, I guess it is 14.04 to 16.04 (LTS).

---

### Post by brilyant on 2016-08-03
I just can't wait to hear the answer to the original question, having been there in identical circumstances.

I blundered through with CTL-C, but I never quite what, if anything, this will bring down in flames.  Should there be a prompt to exit from this post-[d]Display state?

---

### Post by howefield on 2016-08-03
If there is still a task running in the terminal, try Ctrl + z to suspend it, then 

```
jobs
```

to list them and 

```
fg jobnumber
```

to bring them to the foreground.

---

### Post by brilyant on 2016-08-03
Thanks, that answers my query.

---

### Post by Rick St. George on 2016-08-03
OK Howefeld, Now I'm back to where I was before, and it shows (END).
But it seems nothing I press - Enter, Escape, etc. gets back to the prompt. It is still in "display" mode. 

Any Suggestion?
Thanks.

---

### Post by steeldriver on 2016-08-03
It's just using the 'less' pager AFAIK - hitting the Q key should quit and send you back

---

### Post by Rick St. George on 2016-08-03
Thanks! That worked SteelDriver. Back in business and case closed.

---

