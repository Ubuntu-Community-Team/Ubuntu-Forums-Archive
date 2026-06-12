---
title: "Freshly installed 10.04 doesn't recognize /home partition"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by aquifer on 2010-10-06
I just did a fresh install of 10.04 into my root partition last night, formatting both root and swap while leaving my /home partition untouched. That part worked great &#8212; my files all seem to be intact. (I had done a backup, of course.)

However, the system no longer recognizes /home as my /home directory. What had been /home shows up now as a separate 200GB drive. While I can mount the drive and see my old files, it's not a terribly convenient structure. I really would like it to be /home again.

A couple potential complications:


[LIST]
[*]The /home partition is still in the ext3 filesystem, but I chose to format root and swap as ext4 this time around.
[*]I also said yes to the option of encrypting /home.
[/LIST]
Do I need to redo the install, keep root in ext3 and say no to encryption? Would that solve the problem automatically? What else could I do?

---

### Post by ronparent on 2010-10-06
I believe that in step 5 of 8 (manually partition) you may have omitted designating /home as the mount point for /home, not formating it of course. You may go through a process for establishing a separate home after the fact in which you would have to reclaim ownership, but, reinstalling would probably be as easy at this point. Follow this for setting up a separate home if that is what you want to do: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by aquifer on 2010-10-07
You were right -- I'd forgotten to designate the mount point for /home. 

I just went ahead and reinstalled it, making sure to take that extra step, and that did the trick. I was shocked when I rebooted to find my old screen wallpaper staring back at me -- it was my computer again, just with a more up-to-date OS. (The advice elsewhere on this forum about saving then importing the markings in Synaptic also helped speed that process along.)

Thanks for the help!

---

