---
title: "Thunderbird 12.0.1 crashes on startup (Ubuntu 12.04, 64bit)"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by emonti on 2012-06-20
hi

It was starting up fine and then I moved some profile data over from an existing installation, on another machine. Now when I start it up it crashes and prompts to send an error report.

I cleared the new profile folder and copied in all the old profile data.

Any ideas?

Thanks in advance.

---

### Post by surfer on 2012-06-20
did you try

```
$ thunderbird -safe-mode
```

---

### Post by emonti on 2012-06-21
> **surfer said:**
> did you try

```
$ thunderbird -safe-mode
```

Thank-you that worked. It is not crashing on startup anymore.

So the next thing is to work out what the cause of the problem is.... presumably I don't have to use TB in safe-mode from now on.

Do you perhaps know what I could start looking at?

---

### Post by johnfrith on 2012-06-21
How about a crude solution. Backup Thunderbird data, and then re-install it?

---

