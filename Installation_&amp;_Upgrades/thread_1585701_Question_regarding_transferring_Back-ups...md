---
title: "Question regarding transferring Back-ups.."
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2010-09-30
Greetings..
Having installed Ubuntu 10.04 onto my Mum's laptop, I decided it would be a good idea to do a back-up. No probs there, but when I tried to transfer the tar file over to my ext. hard drive, I got the message in the pic provided.

I notice the transfer stopped @ 4gb. This doesn't happen on my PC with Ubuntu installed. What gives, and what can I do to resolve this issue?

Seems pointless to me to have a back-up that can only reside on that PC...

Any help would be much appreciated!

---

### Post by Baldrick_NZ on 2010-09-30
D'oh! Done it again. Here's the pic promised from above..

---

### Post by cj.surrusco on 2010-09-30
> **Baldrick_NZ said:**
> Greetings..
Having installed Ubuntu 10.04 onto my Mum's laptop, I decided it would be a good idea to do a back-up. No probs there, but when I tried to transfer the tar file over to my ext. hard drive, I got the message in the pic provided.

I notice the transfer stopped @ 4gb. This doesn't happen on my PC with Ubuntu installed. What gives, and what can I do to resolve this issue?

Seems pointless to me to have a back-up that can only reside on that PC...

Any help would be much appreciated!

Is your external hard drive formatted in FAT32? If so, the max file size is 4GB. You would need to format it in something like ext4 or NTFS (If you need it to be easily compatible with Windows).

If it needs to be on a FAT32 filesystem for whatever reason, you may want to compress it into pieces. You are able to do that with 7zip compression.

---

