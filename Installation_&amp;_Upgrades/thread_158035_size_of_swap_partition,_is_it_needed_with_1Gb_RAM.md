---
title: "size of swap partition, is it needed with 1Gb RAM"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by MarkHn on 2006-04-10
Typical advice for a swap partition is create one about 1 or 2 times the size of RAM you have.
If you have 256Mb of ram you could create a 500Mb swap partion.

With larger amounts of RAM, at what point should you not create a swap partition at all.
Is it OK NOT to create a swap partition?

With 1Gb of RAM would it improve performance not to use a swap partition? Remove the overhead of pageing out to a swap partition. 
It would simplify the memory managment process.

After-all typical computers, when you add ram and swap partition together still often have less than 1Gb of memory available in total. 
So with a Gb of RAM doesn't this do away with the need for a swap partition.

---

### Post by Paulo Wageck on 2006-04-10
with 1gig i still use it all....

with 2 gig... i dont need a swap... but i still have it.. btw...

---

### Post by John.Michael.Kane on 2006-04-10
Speaking for myself as a test i ran ubuntu with no swap on just 512meg's of mem. it worked as long as nothing heavy was running. with 1gig of mem you could lower the swap to say 256-512. On systems with with 2gigs of mem or more you could in theory run swapless, however i must note there are those will say you can't, and should not run a swapless system. you the enduser have to test for yourself if running swapless is a viable option.

---

### Post by ubernoob on 2006-04-10
I have 2 GB ram. I think my max usage has been 1,3 gb for a very short while. So i would be perfectly good without swap. But since i have 500 GB storage stealing another 2 GB for swap wouldn't make a diffrence, althou i have never swapped on my system.

Back to your question: it depends what you are doing whith your computer and how many simultanous users there is. (remote login, switching desktops, vnc, ssh, ftp, and other services and so on)

---

### Post by xenmax on 2006-04-10
If your machine has lots of users, lots of processes and uptime is large, yeah i can see you needing a swap partition even with 2GB of RAM... will come in handy to flush some stuff to swap to make way if any process is dealing with large files or has a large snapshot to write to disk

---

### Post by greenpenguin on 2006-04-10
Working on the assumption that you have a large hard drive (since you have so much ram) i would say why not have one - if you run out of swap you're buggered (excuse my french) but if you have too much swap, you're always OK.  Saying that, I have 384Mb RAM and 512 Mb swap, and I rarely use more than 1/2 of my swap. I suppose If you have a memory leak a big swap partition would give you more time to notice though ;)

---

