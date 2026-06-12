---
title: "what's the wrong?!!"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Ba7r on 2010-01-21
[FONT=Tahoma][SIZE=3][COLOR=Blue]Hi,

how are you all? .. I've installed [COLOR=Red]_UBUNTU 9.10_[/COLOR] on ( [COLOR=Red]_windows 7_[/COLOR] ) when I was interested to discover Linux, now I began to understand this [AWESOME]("http://google-yahoo-user.blogspot.com") system and I began to get ride of Microsoft " Windows " .. But I face a problem that when I installed It I created only one account with a password, but It's not the root, when I tried to login as root, I didn't success, It tells Failure authentication because of the wrong password, because I enter my account password which I entered when I installed the system, Now I want to know how to solve this ISSUE, how to get the root password or how to reset It 

Regards
[FONT=Arial Black]Muhammd[/FONT]
[/COLOR][/SIZE][/FONT]

---

### Post by presence1960 on 2010-01-21
> **Ba7r said:**
> [FONT=Tahoma][SIZE=3][COLOR=Blue]Hi,

how are you all? .. I've installed [COLOR=Red]_UBUNTU 9.10_[/COLOR] on ( [COLOR=Red]_windows 7_[/COLOR] ) when I was interested to discover Linux, now I began to understand this AWESOME system and I began to get ride of Microsoft " Windows " .. But I face a problem that when I installed It I created only one account with a password, but It's not the root, when I tried to login as root, I didn't success, It tells Failure authentication because of the wrong password, because I enter my account password which I entered when I installed the system, Now I want to know how to solve this ISSUE, how to get the root password or how to reset It 

Regards
[FONT=Arial Black]Muhammd[/FONT]
[/COLOR][/SIZE][/FONT]

It is against forum policy to tell how to over ride the ubuntu security feature of the root account being locked. If you need to do something which requires root priviledge preface the command with sudo or for a graphical app (such as gparted or gedit) gksu. It will ask for your password and you will have root access once you supply the password.

Those who really need to do something in the root account have figured out how to enable it, but we are not allowed to discuss it in here.

---

### Post by CharlesA on 2010-01-21
Just use sudo -i if you need to be root to run something. Otherwise use sudo <command>

---

### Post by Ba7r on 2010-01-21
[FONT=Tahoma][SIZE=3][COLOR=Blue]thanks Guyz I did It :)[/COLOR][/SIZE][/FONT]
 [ sudo -i ]

---

