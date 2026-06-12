---
title: "Ubuntu on Asus Eee 900"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by shade82000 on 2010-10-12
Hello people.

What do you think is the best way to install Ubuntu on an EeePC 900?
It's the one with a 4GB primary and 16GB secondary HDD.

I have been running 10.04 on all of my other computers since April without any serious problems but it seems a bit difficult with the way the HDD's are set up on the Eee.

I set it up originally with the 4GB mounted as / and the 16GB mounted as /home.

This seemed like the obvious way, but after a few software packages and updates the 4GB quickly filled up to the point where I cannot run any more updates, it just tells me there is not enough space.

I have tried running 'apt-get clean' and the trash is empty but I can't seem to free any more space.

The thing is that I have just upgraded all my other computers to 10.10 but I think I might have to do a clean install of 10.10 on the Eee.

I was thinking of just mounting the 16GB as / and letting /home sit on that partition as well but then what would be a good use for the 4GB partition?  I don't want to use it as swap because the drives are SSD's.

Has anyone found a nice way of utilising all the space on this drive setup without running out of space?

I would prefer to be able to keep it as it is and do a 10.10 upgrade if that is at all possible.

Thanks in advance for any help!

---

### Post by mörgæs on 2010-10-12
I would do a clean install and use the 4 GB drive as /home. Good to have this one separate for future installs.

---

### Post by sgosnell on 2010-10-12
4GB isn't much for /home.  My 900 isn't set up the way the OP's is, I don't have the separate 4GB drive.  I would partition the 16GB drive at about 7GB for /, and the rest for /home.  You can also mount individual directories on the 4GB drive, for instance you could put /bin, /etc, or whatever there.  If you do that, I would suggest only about 4GB for the rest of /, and the rest for /home.  Look at your current installation, the sizes of each directory, and see what makes sense on your system.  You certainly don't have to mount the entire / hierarchy on one drive.

You could also use the 4GB drive for data storage, perhaps /Documents, /Music, /Pictures, or whatever, or maybe just a general-purpose data drive.

---

### Post by shade82000 on 2010-10-13
That's great, thanks.

I think I will use the 16GB for / and use the 4GB initially for /home.

Then I can always shrink the 16GB and create some space to mount an empty folder in /home if I ever need to.

I did try using 'filelight' to see where the largest directories are currently, but I think relocating some of these directories with their contents is a bit beyond me at the moment.  I would rather do it with empty directories!

Thanks for your help.

---

