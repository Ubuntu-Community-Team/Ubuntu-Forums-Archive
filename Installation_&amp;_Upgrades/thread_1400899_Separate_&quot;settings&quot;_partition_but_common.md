---
title: "Separate &quot;settings&quot; partition but common home partition on system with 2 Linux distro"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by mauricep on 2010-02-07
I was surprised not to find an existing thread on this anywhere, as I would expect this to be a common problem:

I have the following partitions on my eee PC 100HE:

10GB Windows XP
5GB Linux Mint 8
5GB Ubuntu 9.10 NBR (awesome distro by the way!)
130GB Home partition shared by Linux Mint and Ubuntu NBR
2GB Swap partition shared by Linux Mint and Ubuntu NBR

I installed Ubuntu NBR after Mint. Immediately after install, the panel layout, menus and colour scheme were slightly messed up - presumeably because they had been "adopted" from the Mint settings in the home folder. I corrected them easily, but now I have the same problem in Mint.

Is there any way I can get both distros to use the same /home folder, but different settings (i.e. the /home/username/. folders)? Can I get these settings folders put on a different partition for example?

And is this problem due only to the fact that these are 2 Ubuntu-based distros? Or will I have the same problem if/when I replace Mint with another distro, such as Fedora or Moblin?

Thanks!

Maurice

---

### Post by NCLI on 2010-02-07
No, not to my knowledge. The /home/*username* directory is made for storing account settings, so what you're asking is impossible. Just make separate usernames for the two distros, then they'll use the same partition, but different folders.

You can then make shortcuts in the new folder to your documents and stuff in the old folder.

---

### Post by mauricep on 2010-02-18
> **NCLI said:**
> No, not to my knowledge. The /home/*username* directory is made for storing account settings, so what you're asking is impossible. Just make separate usernames for the two distros, then they'll use the same partition, but different folders.

You can then make shortcuts in the new folder to your documents and stuff in the old folder.


Thanks for the reply. A bit disappointing, because it reduces the user-friendliness of running 2 distros on one computer - but I guess I'll be able to live with it....

M.

---

### Post by SecretCode on 2010-02-18
You might be able to get half-way there by having separate /home partitions for each distro - but mounting the main subfolders to shared locations.

E.g. /home/name/Documents -> /media/bigsharedpartition/Documents
/home/name/Music -> /media/bigsharedpartition/Music
etc

I haven't done this but it should work.

---

### Post by tom4everitt on 2010-02-18
I guess everyone have their own solution to this problem. Mine is:

Have the same username on both systems (and shared partition), but choose a different home folder for them. My user is called everitt in both fedora and ubuntu, but I've named the home folder for the ubuntu-everitt ubuntu, and the home folder for fedora-everitt fedora. 

Then they are safely separated. If I wanted to I could make links from these two folders to /home/everitt, like a previous poster suggested, but I actually haven't bothered yet.

---

### Post by oldfred on 2010-02-18
I put all my data into a separate partition with the data partition having all my folders from my old install. I then linked them into home so home only actually has the hidden settings. If the distros are similar you can copy setting but you need to keep them separate.

Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents

---

### Post by mauricep on 2010-03-02
Thanks for the tips. I think the seperate data partition is certainly the cleanest solution. 

Maurice

---

