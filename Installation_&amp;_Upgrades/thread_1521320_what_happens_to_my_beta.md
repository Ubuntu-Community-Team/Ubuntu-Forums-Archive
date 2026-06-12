---
title: "what happens to my beta?"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by wideyes on 2010-06-30
Kind of noobish question here, but I'm currently running a beta install of 10.04. I needed a new OS and didn't want to wait for the official 10.04 release. I am in no way actually qualified to beta test any piece of software - I just did it for my own convenience. My question is, once the official release came out, and I continued to install my updates as usual, did my beta automagically catch up with and become the official release? Is the official release just the version of the beta that they finally put out to the public? I'm a little hazy on this. Clarification would be appreciated!

BTW, for me and my uses, I've found 10.04 to be the best Ubuntu yet, with many improvements that I had been wanting. Thanks a bundle!

---

### Post by vegetarianshrimp on 2010-06-30
Go to System->About Ubuntu to see exactly what version you're running. Hope this helps! :D

---

### Post by wideyes on 2010-06-30
Thanks! It did list 10.04 LTS as my version, with no mention of Beta. Would it be listed as a beta version if it were?

---

### Post by howefield on 2010-06-30
> **wideyes said:**
> My question is, once the official release came out, and I continued to install my updates as usual, did my beta automagically catch up with and become the official release?

Yes.

Open a terminal and type

```
cat /etc/lsb-release
```

if it doesn't say Development release anywhere in there, you have full release.

---

### Post by vegetarianshrimp on 2010-06-30
> **wideyes said:**
> Would it be listed as a beta version if it were?
I'm not sure...try howefield's method above.

---

### Post by wideyes on 2010-06-30
Thanks Howefield, that did it! I'm "official"! This gives me some peace of mind knowing that my prerelease version is now up to date. You guys are great.

---

