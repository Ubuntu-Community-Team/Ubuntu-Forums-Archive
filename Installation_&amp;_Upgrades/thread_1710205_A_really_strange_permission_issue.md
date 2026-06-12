---
title: "A really strange permission issue"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by NexusN on 2011-03-19
Hi everyone, 
I am here to seek a solution to a strange permission issue that have been suffering me for weeks.

As study need, I have to install MatLab on my ubuntu 10.10 x64.
I downloaded the latest version and tried to install, I found this.
As root I ran ./install,

Installing ...
eval: 1: /tmp/mathworks_3035/java/jre/glnxa64/jre/bin/java: Permission denied
Finished

And this is what ended up to be.

The permission denied problem exists not only for MatLab installation but also some other software like VMware.

I have searched for the solution but maybe I don't have that luck to get it.
May you please kindly share your ideas or experience in dealing with this?
Much appreciated.

---

### Post by falko on 2011-03-19
What's the output of ```
ls -la /tmp/
```?

Do you have enough free disk space?

---

### Post by NexusN on 2011-03-19
On keeping the search,
not only guys sharing the same roaring the denied issue, 
I actually find a solution for that!
I thought it was about Java but I don't know where to change the permission.

[http://www.mathworks.com/matlabcentral/newsreader/view_thread/292020](http://www.mathworks.com/matlabcentral/newsreader/view_thread/292020)

From this post I get it, and hope this also helps you from the dark if this applies to you.

---

### Post by NexusN on 2011-03-19
> **falko said:**
> What's the output of ```
ls -la /tmp/
```?

Do you have enough free disk space?

Thank you for your reply but I think I have just got it.

---

