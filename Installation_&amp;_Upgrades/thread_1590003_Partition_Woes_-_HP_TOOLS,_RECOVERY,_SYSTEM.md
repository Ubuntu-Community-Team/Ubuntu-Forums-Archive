---
title: "Partition Woes - HP TOOLS, RECOVERY, SYSTEM"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Karandr on 2010-10-07
Hi there,
I'm currently in the process of installing Ubuntu 10.10 to my hd, as opposed to the Wubi installation I used to have (which died when I tried updating, funny story).
I'm on a HP Mini 210 netbook which came with Windows 7 Starter pre-installed. I need to keep Windows around because I need iTunes, so I want to install Ubuntu on a separate partition. I shrunk the Windows partition down to about 130 GB, so there's around 100 left for me to install Ubuntu in. 
Anyway, I was about to go partitioning-happy in GParted, when I looked at [this]("http://imgur.com/dMsm0.png") and realized something.
There are already 4 partitions -- HP TOOLS, RECOVERY, SYSTEM and the C:/ drive. After doing some research on the matter (I'm not the most tech-proficient person around) I learnt that I can't make more than 4 partitions on a hard drive unless I get involved with logical partitions. Sadly, I have no idea what that entails, and at this stage I'm horribly afraid I'm going to screw something up tremendously. Is anyone in a particularly charitable mood and willing to help me through this process? I'm sorry if I'm asking something trivial, it's just that I'm really not sure what to do. Should I go about creating a "logical partition" or should I get rid of one of the other partitions? Is it entirely necessary to have HP TOOLS and RECOVERY? I read that SYSTEM is something Windows 7 does by default (curses!), so I am cautious to touch it.
Again, thank you for your time.

---

### Post by viralmeme on 2010-10-07
> **Karandr said:**
> I'm currently in the process of installing Ubuntu 10.10 to my hd .. I need to keep Windows around  ..
[My Successful Install of ubuntu netbook 10.04 on a HP]("http://ubuntuforums.org/showthread.php?t=1556573")

---

### Post by Karandr on 2010-10-07
You're a saint, thank you!
Oh my goodness, I was about to ask for a Windows imaging tool, but then I saw that Grysync is available on Windows, oh bless. 

Again, thank you so much, I'm gonna get on this in the morning. You've really saved me a lot of pain.

---

### Post by Mark Phelps on 2010-10-07
> **Karandr said:**
> Hi there,
I'm currently in the process of installing Ubuntu 10.10 to my hd, as opposed to the Wubi installation I used to have (which died when I tried updating, funny story).
IF what you meant is you tried to update a Wubi-installed 10.04 to 10.10, you could have saved yourself a lot of trouble if you'd simply read the Release Notes.  They clearly indicate that such and update will fail.

In future, if you're going to continue to mess around either with pre-release Ubuntu versions and/or Wubi, you can save yourself a lot of potential grief if you simply read the Release Notes.

---

### Post by Rubi1200 on 2010-10-07
> **Mark Phelps said:**
> IF what you meant is you tried to update a Wubi-installed 10.04 to 10.10, you could have saved yourself a lot of trouble if you'd simply read the Release Notes.  They clearly indicate that such and update will fail.

In future, if you're going to continue to mess around either with pre-release Ubuntu versions and/or Wubi, you can save yourself a lot of potential grief if you simply read the Release Notes.
+1

Also, please ask here on the forums first as well.

The few extra minutes it will take to post a question and get an answer could save you hours of headaches and frustration!

---

### Post by Karandr on 2010-10-08
> **Mark Phelps said:**
> IF what you meant is you tried to update a Wubi-installed 10.04 to 10.10, you could have saved yourself a lot of trouble if you'd simply read the Release Notes.  They clearly indicate that such and update will fail.

In future, if you're going to continue to mess around either with pre-release Ubuntu versions and/or Wubi, you can save yourself a lot of potential grief if you simply read the Release Notes.

Yeah, upon reflection I didn't really think that one through quite enough. Again, I am forever indebted to the saints of the Ubuntu forums.

---

