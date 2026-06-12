---
title: "help: how to prevent removal of older kernel versions on update"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by euux on 2010-07-28
Hi, 
I need to prevent that the latest kernel update removes the only kernel that still works in my computer. how can i do this?

Currently I have 3 linux kernels versions:
```
Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
```
But only the oldest works. 
With the new update there is a new kernel version (2.6.32-24) that possibly will not boot (like previous 2.6.32-* kernels) and also I expect that, as in previous updates, the oldest kernel will become inaccessible, thus rendering my ubuntu unbootable.

Can anyone help me with this, please? :popcorn:

PS: unsolved threads on the underlaying problem: 
_[Can't boot default kernel after upgrading from 9.xx to 10.04 lucid]("http://ubuntuforums.org/showthread.php?p=9631721")_
_[Upgrade to 10.04 freezes on the Ubuntu screen ]("http://ubuntuforums.org/showthread.php?p=9629876")_

---

### Post by Sub101 on 2010-07-28
In my experience an Update would not remove an older Kernel?

---

### Post by euux on 2010-07-28
> **Sub101 said:**
> In my experience an Update would not remove an older Kernel?
honestly I would have to remember how did it go with the last kernel upgrade before 10.04 (when the list was "reseted"). 
But I have this idea that the list of available kernels to boot does not grow indefinitely.

thanks for the reply :)

---

### Post by rollin on 2010-07-28
I normally just use Synaptic: 

Open it up and select the "Installed" section. In the search bar type "linux-image.." you should then see a list of the images and kernels that are showing in your grub menu. Make sure you choose the right one and select "Lock" from the Package Menu.

Edit: Sorry updated the post with correct info.

---

### Post by euux on 2010-07-28
> **rollin said:**
> I normally just use Synaptic: 

Open it up and select the "Installed" section. In the search bar type "linux-image.." you should then see a list of the images and kernels that are showing in your grub menu. Make sure you choose the right one and select "Lock" from the Package Menu.

Edit: Sorry updated the post with correct info.

thanks, will try that!

---

### Post by rollin on 2010-07-28
> **euux said:**
> thanks, will try that!
No problem! I think it should work but it'd be good if you can post an update or with any problems. Good luck ;)

---

### Post by euux on 2010-07-28
> **rollin said:**
> No problem! I think it should work but it'd be good if you can post an update or with any problems. Good luck ;)
I've done it and the safe kernel (old 2.6.31-21) was kept available. 
On the better than nothing news, the new kernel (2.6.32-24) works better than his 2 predecessors - it's able to boot on my machine if I follow the _recovery mode_ with _failsafeX_. 

Thanks for the help and the time spared.
:D

---

### Post by rollin on 2010-07-28
> **euux said:**
> I've done it and the safe kernel (old 2.6.31-21) was kept available. 
On the better than nothing news, the new kernel (2.6.32-24) works better than his 2 predecessors - it's able to boot on my machine if I follow the _recovery mode_ with _failsafeX_. 

Thanks for the help and the time spared.
:D

Awesome! :D You're welcome too and thanks for posting with the update. It's a good question so I'm sure your thread will help someone in the future.

---

