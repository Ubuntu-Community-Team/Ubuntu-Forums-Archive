---
title: "Upgrading From 8.04 to 9.10"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by gxthekird on 2010-03-04
Hi to all Members =) I'm new here. I've just installed 8.04. and I was googling on the net and saw that there's a more new version 9.10 is it? So I tried following the guide on [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)
Can some one tell me basicly what do I need to do? I'm still so new that I know nothing about Ubuntu.

---

### Post by wojox on 2010-03-04
If you just installed 8.04 then back up anything you want as far as documents and such in your Home Folder and do a fresh install of 9.10 to take advantage of Grub2 and ext4. ;)

---

### Post by Elfy on 2010-03-04
To upgrade from 8.04 to 9.10 you'd need to do 9.04 first, but as 8.04 was a LTS release in a month or so you would be able to directly upgrade from 8.04 to 10.04.

I'd be inclined towards either waiting or downloading 9.10 and doing a clean install of that.

---

### Post by gxthekird on 2010-03-04
> **forestpiskie said:**
> To upgrade from 8.04 to 9.10 you'd need to do 9.04 first, but as 8.04 was a LTS release in a month or so you would be able to directly upgrade from 8.04 to 10.04.

I'd be inclined towards either waiting or downloading 9.10 and doing a clean install of that.
Can I know more about LTS? And are u trying to say that if I wait for a month or so,I can updrage 8.04 to 10.04 without going throught 9.04 and 9.10?
And thanks to everyone who is helping me so far! =)

---

### Post by Sef on 2010-03-04
> Can I know more about LTS? And are u trying to say that if I wait for a  month or so,I can updrage 8.04 to 10.04 without going throught 9.04 and  9.10?
And thanks to everyone who is helping me so far! =)

LTS = Long Term Support.   NonLTS support is good for 18 months for servers and desktops; LTS support is good for 5 years on the server and 3 years on the desktop.   The next LTS will be Lucid Lynx which will be released in about 7 weeks.   And you will be able to upgrade directly from Hardy to Lucid.

---

### Post by maddg3241 on 2010-03-04
ya 9.10 is a lot better in my opinion :p

---

### Post by adam22 on 2010-03-04
I would not recommend upgrading. You don't get the biggest advantages like the newer filesystem and it's "messy" in my opinion. The best thing to do is plug in a flash drive or external hard drive and drag your important documents over to the drive. Then, pop in the new CD and delete the old partition and install the new one.

Keep in mind: 
The numbers reflect the date. 10.04 means it's coming out in April, then 10.10 comes out in October (every six months there's a new version). LTS releases come out every four releases.

Also, when you partition:

If you want to install new versions when they come out, you'll save some time making separate partitions instead of the default "bundle" Ubuntu chooses.

You need a 2 GB SWAP partition, a 20 GB / (root) partition...this is the one you will delete and install with the newest version. A separate /home partition of at least 30 GB is also helpful as it will not be deleted, and all documents, themes, etc. will remain in tact when installing or reinstalling the operating system. Obviously if you have a smaller drive you can adjust these numbers accordingly, but I have a 320 GB drive, so I would use these amounts as minimum for a drive that big.

---

