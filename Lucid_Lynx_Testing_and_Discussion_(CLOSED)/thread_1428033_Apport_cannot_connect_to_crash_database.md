---
title: "Apport cannot connect to crash database"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2010-03-12
Apport itself crashed yesterday, but was able to report the crash still. I was impressed. Today apport will not send any crash reports and I get a dialog titled "Network Problem" with the text, "Cannot connect to crash database, please check your internet connection." This is despite the fact that I am currently signed into launchpad via my working internet connection.

Any apport problems for you other users?

---

### Post by kansasnoob on 2010-03-12
Yep, we were posting at the same time :D

---

### Post by kansasnoob on 2010-03-12
I sure hope 23meg is around.

---

### Post by kansasnoob on 2010-03-12
Well this really stinks. I just ran "apport-cli -f -p apport" in Lucid and saving the report to /tmp. I then copied it to Jaunty's /home, booted into Jaunty and tried filing that report from Jaunty and I get the same error.

So Apport at the moment is just about as handy as a pay toilet in the diarrhea ward of a hospital :P

---

### Post by tekstr1der on 2010-03-12
Filed:
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097)

@kansasnoob: Please confirm/affects me too

---

### Post by ikt on 2010-03-12
Yep, this seems like a fairly big issue.

---

### Post by Yofel on 2010-03-12
Hit me too on a Kubuntu live disk. I confirmed the bug.

---

### Post by kansasnoob on 2010-03-12
> **tekstr1der said:**
> Filed:
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097)

@kansasnoob: Please confirm/affects me too

Done, I was trying to file and found yours, I'm Erick there, added my 2 cents :D

Thanks for filing that.

---

### Post by kansasnoob on 2010-03-12
> **ikt said:**
> Yep, this seems like a fairly big issue.

Huge issue! I was trying to file a bug about Lucid's Nautilus reading file sizes wrong and couldn't.

---

### Post by cpmman on 2010-03-12
+1

[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/537891]("http://https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/537891")

---

### Post by dino99 on 2010-03-12
i've reported today without problem, so it might be a "time out" problem or else on launchpad side and not a problem of apport itself.

But still wonder why all the crashes are "silent" and half of them are owned by root, strange.

---

### Post by tekstr1der on 2010-03-12
I wonder how widespread this issue is today? So far, 9 people on the bug report. If this affects most users, the triagers can take a vacation. Lucid is bug-free, yay!:)

EDIT: Oh, on the flip-side, I've got 2 additional crash reports queued up to submit once apport is operational again.

EDIT2: @dino99: It's good to hear apport is working for you. It does not appear to be a timeout issue as the failure is quite immediate. While it's good to report that it doesn't affect you here on the forums, why would you comment in a bug report about a bug that doesn't affect you? That's confusing!

---

### Post by marshmallow1304 on 2010-03-12
Same problem here.  System Testing (checkbox-gtk) also fails to connect to server.

---

### Post by Didius Falco on 2010-03-13
affects me as well. Added confirmation of that to the bug.

---

### Post by victor9098 on 2010-03-13
+1

I get the same error message saying that it can not connect to the internet, seemed to work fine the last time I used (11th March?). Hopefully there will be an update soon.

---

### Post by tekstr1der on 2010-03-13
Yeah, this is really bad timing for apport to be busted. It's critical to get bugs filed pronto. I guess I'm going to start attaching crash reports to manually filed bugs. I now have 4 reports queued up waiting for a fix on this.

EDIT: Looks like this may start getting some attention. Not only are there now 38 people "affected", but the importance has been switched to High by a dev.

---

### Post by Yofel on 2010-03-13
I added a Launchpad task to the bug, apport failing with 'HTTP Error 500: Internal Server Error' seems more like a bug in launchpad than in apport.

---

### Post by Rob2687 on 2010-03-13
Is it possible to recover the most recent apport report? 

I have been getting kernel panics and each time there was no apport popping up on the next reboot. Just now it kernel panicked and a miracle happened when I boot up again but then it couldn't connected. =(

---

### Post by Yofel on 2010-03-13
> **Rob2687 said:**
> Is it possible to recover the most recent apport report? 

I have been getting kernel panics and each time there was no apport popping up on the next reboot. Just now it kernel panicked and a miracle happened when I boot up again but then it couldn't connected. =(
Apport stores it's crash information in /var/crash/ 
check if you have any linux .crash files there. If yes, run 'sudo ubuntu-bug /var/crash/<crashfile>' once apport works again.

---

### Post by bclintbe on 2010-03-13
I'm having the same problem when it tries to report that telepathy-butterfly crashed (happens each time I start empathy). +1 on the bug report. I want this solved fast, since the whole reason I'm using an Alpha release is to squash bugs!

---

### Post by dcstar on 2010-03-13
> **bclintbe said:**
> I'm having the same problem when it tries to report that telepathy-butterfly crashed (happens each time I start empathy). +1 on the bug report. I want this solved fast, since the whole reason I'm using an Alpha release is to squash bugs!

Yeah, you try to spend some time on the weekend to make 10.04 better when it gets released and you hit this wall...

I have found that the "saved" option does not work in Grub, but I can't get in to report it.

---

