---
title: "Upgade freeze at kernel 2.6.38-15"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by kuifje09 on 2012-06-22
When I try to upgade my system using the upgrade tool, the download starts and some packages arrive. But now for several times the download of the kernel 2.6.38-15 freezes.
After cleanup, restart it,  then freez  at 41%   4 %  31 % and so on. Seems random.
Never comes to an happy end.

How can I solve this?

(some days ago I upgraded an other sytem with no problem to the same level.)

---

### Post by dino99 on 2012-06-22
you can change to the main server into synaptic

---

### Post by kuifje09 on 2012-06-22
Well, not much luck.
Changed to several servers, but all the same problem.
At last I ran the "best server" test and came to the dutch nl3.archive again.
Still the same problem.  a freez when downloading the generic kernel. at random size...

Just tried an ftp server in germany, then it stops when kernel is at 44%.

I have read some time ago the provider at the user side was the problem.
If it is the problem in this ( mine ) case, how can we prove that?

Switched back to the main server, did a apt-get -clean. Started over and several packages get loaded,
then it stops at 36% in the linux kernel image again.
This is not just coincidence, I just can't believe it !

---

### Post by kuifje09 on 2012-06-22
At last it finished downloading all files.
The kernel was the problem , why ?,  it came in bursts,  just like the download freezes, there came in another fewhundred bytes.  and again......
Took about 5 minutes I think, then all other files rushed in , in one stream.

Very strange I never had this experience before.

Update has finished and system rebooted and is up again.
But if someone knows what happend in this download, I like to know.

---

