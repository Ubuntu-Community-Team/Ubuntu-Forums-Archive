---
title: "Dual Boot with Windows?"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by qrrbrrbbl on 2011-04-16
I currently have Windows 7 Starter installed on my netbook, and will be installing Ubuntu alongside it. What would be the best way to install it and keep my Windows installation unharmed?

---

### Post by Rubi1200 on 2011-04-16
First, make backups of all important data.

Next, use the built-in function in Windows to create a restore disk (unless you already have one) just in case.
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Finally, read about safe dual-booting in this guide:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Good luck :-)

Feel free to ask more questions before starting.

---

### Post by qrrbrrbbl on 2011-04-16
What would be worst-case scenario here? Or, what's the likelihood of something going wrong?

---

### Post by dino99 on 2011-04-16
what you need:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by qrrbrrbbl on 2011-04-16
Actually, is there a Wubi installer available for the 10.10 netbook edition?

---

### Post by Blasphemist on 2011-04-16
Worst case is that somehow you end up needing to keep running Windows, most likely only because of some hardware limitation.

The link to the dual boot information from Herman above provides you a great resource. Provide more detail and people can provide you more detail. For example, will you need install from USB or do you have a CD/DVD? More specifics gets more specifics. Let us know if we can be of more help. Good planning and attention to detail and you will be dual booting in now time, and then asking how to kill Windows.

FYI, with the new version of Ubuntu to be released in about 2 weeks the netbook edition and desktop edition have been combined. The Unity interface is the default but Gnome can be chosen at any time during use. You will see many pro's and con's on Unity in these forums but I use it and very much like it.

---

### Post by qrrbrrbbl on 2011-04-16
I would have to install from USB, as my netbook lacks an optical drive. I want to make sure my Windows installation stays okay because I have some Steam games and Diablo II on there that I like to play. Unless they work well through Wine.

---

### Post by Rubi1200 on 2011-04-16
> **qrrbrrbbl said:**
> What would be worst-case scenario here? Or, what's the likelihood of something going wrong?
The worst case scenario is that you overwrite the Windows install, losing all data.

I don't mean to put you off, but you need to know this:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

However, if you plan in advance and use manual partitioning to install, chances are nothing will go wrong.

As to the Wubi question, I believe there is a 10.10 netbook edition (can't find the link right now, will post it later for you).

---

### Post by theozzlives on 2011-04-16
> **qrrbrrbbl said:**
> I would have to install from USB, as my netbook lacks an optical drive. I want to make sure my Windows installation stays okay because I have some Steam games and Diablo II on there that I like to play. Unless they work well through Wine.

As long as you use Windows Disk Manager to resize your Drive C:\ to make room for Ubuntu, you should be okay. Be sure to backup cause worse case, you will lose everything. That's unlikely, however.

---

### Post by qrrbrrbbl on 2011-04-16
So create a new partition in Windows and install Ubuntu onto that? The guide above creates a recovery disc on a DVD. Can one be created on an external hard drive in the same way?

---

### Post by qrrbrrbbl on 2011-04-16
> **Rubi1200 said:**
> The worst case scenario is that you overwrite the Windows install, losing all data.

I don't mean to put you off, but you need to know this:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

However, if you plan in advance and use manual partitioning to install, chances are nothing will go wrong.

As to the Wubi question, I believe there is a 10.10 netbook edition (can't find the link right now, will post it later for you).

There is a bug listed there that says certain applications can overwrite GRUB. I'm confused. If this happens, will I only be unable to boot into Ubuntu, or both Windows and Ubuntu?

---

