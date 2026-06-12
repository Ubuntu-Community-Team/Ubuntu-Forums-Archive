---
title: "Can't install applications"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by markling on 2011-07-17
I despair.

I installed Qwit from the Ubuntu Software Center. It didn't work. I searched for help. It seems the version of Qwit in the Software Center is out of date.

I installed Clive from the Ubuntu Software Center. It didn't work. I searched for help. It seems the version of Clive in the Software Center is out of date.

Really, what is a regular user supposed to do?

It seems there are later versions of of both Clive and Qwit that can be downloaded from websites. They don't download as files that can simply be installed by clicking on them. Dumb users like me can't install software that doesn't just just install.

I had a similar problem with Libre Office recently. This is now supposed to be the official office suite. But I can't get it through the Software Center. If I go to the Libre Office site and do the download I just get a load of gobbledegook.

I tried looking for help. The help's no good either:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

It doesn't tell you what you are doing. It would be polite to explain what commands do when you are asking people to enter them. To be fair, the CompilingEasyHowTo is better than most. But it still leaves you behind quickly.

It assumes you know how to create directories, which is about the extent of my command line knowledge.

But then... what the...?

"Step 3... To prepare, install the package apt-file, and then run sudo apt-file update."

Sorry? How do you install the package apt-file?

Try this:

> install apt-file

No. What about:

> sudo apt-get apt-file

No.

What about:

> sudo apt-file

No.

My head's already spinning at this point. Who's this EasyHowTo written for? People who don't need an EasyHowTo? I scan down the page of the EasyHowTo and it starts to look really scary. So I give up.

Why doesn't someone just make sure the Software Center is up to date in the first place so people don't waste their time installing software that doesn't work and then searching to find out why it doesn't work, and then getting bogged down in tutorials written for people who don't need tutorials and then giving up, feeling stupid, inadequate, bitter and like there are lot of things I'd rather be doing.

---

### Post by oldos2er on 2011-07-17
Did you check if either clive or qwit are available from PPAs? [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

To install apt-file from the command line, run **sudo apt-get install apt-file**
Or you can install it from Software Center, assuming you want to pursue compiling source code. Not an exercise for someone new, I agree, but if you're up for a learning experience it might be something to look in to.

---

### Post by markling on 2011-07-17
Thanks oldos2er. I will no doubt look into your suggestions.

But the point of my post is to protest: the Software Center is delivering applications that don't work and are out of date. Something's broken. This is the cause of immense frustration and wasted effort.

Understanding this requires one to use Ubuntu from the perspective of a user that lacks both command line knowledge and time to gain it.

Sure, this sort of user can make a hobby out of learning to administer linux. But if such effort is a requirement of using Ubuntu, then the project has failed in its mission:

[http://www.ubuntu-user.com/content/view/full/2023](http://www.ubuntu-user.com/content/view/full/2023)

---

### Post by oldos2er on 2011-07-17
Both qwit and clive are in the universe repository, which Canonical isn't responsible for. [https://help.ubuntu.com/community/Repositories#Universe](https://help.ubuntu.com/community/Repositories#Universe)

---

### Post by miklcct on 2011-07-20
> **oldos2er said:**
> Both qwit and clive are in the universe repository, which Canonical isn't responsible for. [https://help.ubuntu.com/community/Repositories#Universe](https://help.ubuntu.com/community/Repositories#Universe)

The universe is for unofficial free software applications which most of them are pulled automatically from Debian and no one cares about them in Ubuntu. Therefore, there is no QA for those applications.

---

### Post by markling on 2011-08-06
This talk of a universal repository is gibberish to me. There was a version of qwit in the Software Centre. It didn't work.

---

