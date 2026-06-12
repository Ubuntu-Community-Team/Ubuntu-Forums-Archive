---
title: "installed trusty,had no swap"
date: 2014-07-08
forum: Installation &amp; Upgrades
---

### Post by a-you on 2014-07-08
I now have swap, though it's not encrypted.

It seems to be a common problem that after installing trusty the swap is disabled. I tried various solutions offered in various posts but none worked for me (I went through many but didn't keep notes, sorry).

What got swap at least working again for me was simply editing /etc/fstab, uncommenting the line that starts with "UUID=" (which was commented out by default) and commenting out the line that says "/dev/mapper/cryptswap1 none swap sw 0 0"

But please note that if you do this you should do

```
sudo swapoff -a
sudo mkswap /dev/sdXX
```

where "XX" should be changed to match your swap partition. You have to use the UUID that's then output in the line you uncomment in fstab.

```
sudo blkid
```

should give the same UUID for the swap partition.


```
sudo swapon -s
```

to check if it's working.


I'm calling it "solved" because probably it's not too hard to get it to be encrypted. Maybe. I'm guessing that tools from the ecryptfs package can probably do it. But for me a non-encrypted swap is fine. I think I may actually prefer that, because when I'm working with big files (eg video) then I'd rather have the system be as nimble as it can be. And then if I'm doing something with a file I would consider encryption worthy (not so many of those) they're typically tiny by today's standards---text files bacially---and in those situations every time I check there's no swap being used. Just a thought ;-)

---

