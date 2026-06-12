---
title: "apt-get lost: cant fetch some archives"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by JustBCoz on 2008-11-24
I just got Ubuntu, and the first thing I did was install skype. The sound didn't work. Someone around here suggested I remove PulseAudio so I did and skype worked. I was stoked to solve my first linux problem all by my little self.

Later I restarted and found the problem described here:
[http://ubuntuforums.org/showthread.php?t=989141](http://ubuntuforums.org/showthread.php?t=989141)

I couldn't reinstall it though because it was "unable to fetch some archives. maybe run apt-get update or try with --fix-missing?"

I tried apt-get update and it seems to be unable to connect to any of the repositories. What is --fix-missing and how do I try something with it?

I'm reposting because I suspect I'm having multiple problems here. I think the lack of Pulseaudio is locking me out of GNOME, but something else may be keeping me offline while in recovery mode. 

Side note: How do y'all post your exact error messages from things? Are you actually retyping or is there a nice quick way to basically copy and paste even though I'll have to reboot and get back into vista to check this forum?

---

### Post by taurus on 2008-11-24
Can you post the whole error message when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by JustBCoz on 2008-11-24
Without copy and paste ability (I dont know how in recovery mode since I'm dual booting back to vista to type this) Here is a paraphrase for you for what comes back when i run sudo apt-get update.

could not resolve [some ubuntu url i'm guessing is a repository]
could not resolve [some non-ubuntu url i'm guessing is a repository]
[then it gives me several warnings:]
W: could not fetch [url 1]
W: could not fetch [url 2]
W: could not fetch [url 3]
W: could not fetch [url 4]
W: Some index files failed to download they have been ignored or old ones used instead. You may want to run apt-get update to correct these problems.

:|

---

### Post by JustBCoz on 2008-12-02
Reinstalled ubuntu. problem solved.

---

