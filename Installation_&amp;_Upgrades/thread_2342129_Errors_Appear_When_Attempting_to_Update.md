---
title: "Errors Appear When Attempting to Update"
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by Spencer_Thompson on 2016-11-04
Hello! It's been a while since I've been here as I haven't run into any problems for a long time. However, now I have a new problem. Whenever I try to update, be it through terminal or Software Updater, it gives me several errors. I'm sure there's a way to fix this, but hopefully I don't have an accident like my previous times where I've had to reinstall Ubuntu. Here's the errors I've been encountering below. I'm using Ubuntu 16.04, recently upgraded from 14.04.

```
W:The repository 'cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1) trusty Release' does not have a Release file., 
W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
E:Failed to fetch cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, 
E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bucky Ball on 2016-11-04
Looks like you're trying to use the install CD as a repository. Go to 'Software and Updates'> 'Other Software' tab and make sure it is not enabled in there. 

If it is, untick and all should be well. If it is not, please open a terminal and post the output of this command here between ```
 tags. See green link in my signature below for how to use code tags.

[code]nano /etc/apt/sources.list
```

---

### Post by Spencer_Thompson on 2016-11-04
I'm assuming you're talking about the "Cdrom with Ubuntu 14.04 'Trusty Tahr'" respository. Since I'm disabling it, is it safe to remove? Here's what comes up in the terminal.

```
  GNU nano 2.5.3          File: /etc/apt/sources.list                           

# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ tr$


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
              [ line 1/53 (1%), col 1/100 (1%), char 0/2900 (0%) ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line
```

---

### Post by Bucky Ball on 2016-11-04
Let me get this straight. You have a full install to hard drive? The CD is not enabled in the above file, but have you checked in 'Software and Updates'?

What has me a bit confused is your question 'is it safe to remove?'. Is what safe to remove and from where? The CD from the optical drive? There is no repository to remove as it is on the CD, so removing the CD effectively removes the repository.

PS: That doesn't look like the whole file you have posted. Please add the rest if there's more.

Ding. It just clicked. You are running 16.04 (Xenial) and you have a 14.04 CD ROM causing problems. Do you have a 14.04 install CD in the drive at boot??? I'm also guessing you recently did an upgrade via the net from 14.04 to 16.04. This kind of info should *always* be provided. These kind of upgrades are known to be problematic and some of those problems have known fixes.

---

### Post by Spencer_Thompson on 2016-11-04
I disabled the repository like you said and the errors are gone, but I'm asking if it's safe to remove the repository from Software & Updates > Other Software. I don't have any CD in my drive at the moment.

Screenshot: [https://imgur.com/a/jWWXB](https://imgur.com/a/jWWXB)

---

### Post by Bucky Ball on 2016-11-04
Nothing to remove. Having that enabled just means that when you update the system looks for the 14.04 CD that's not there. There is no repository present on your machine to remove, it's on the absent CD. Have no idea how you would remove the entry altogether from 'Software and Updates' but it's not enabled, does nothing, not an issue. :)

I'm guessing you originally installed 14.04 then upgraded that to 16.04 (please re-read my last post as edited) and that is with you. That will always have an entry for a CD in it and I'm guessing it would be for the one you originally installed with. You don't say, but that's my guess.

As your original issue is fixed, please mark the thread as SOLVED from 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post. This will not close the thread to further discussion but will help others. Thanks.

---

### Post by Spencer_Thompson on 2016-11-04
Well, thanks for the help. I appreciate the fact that I can come to this site whenever I run into any Ubuntu related problems. Solved!

---

### Post by Bucky Ball on 2016-11-04
> **Spencer_Thompson said:**
> I appreciate the fact that I can come to this site whenever I run into any Ubuntu related problems. Solved!

All good and happy to. Wish we could solve them all this quickly. Actually, wish we could solve them all! :)

Hopefully things will be problem free for you for another extended period. Enjoy.

---

