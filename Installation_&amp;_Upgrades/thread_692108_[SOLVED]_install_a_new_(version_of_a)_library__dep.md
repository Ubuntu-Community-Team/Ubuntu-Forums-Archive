---
title: "[SOLVED] install a new (version of a) library / dependency issue"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2008-02-09
Hello,

it 's not so uncommon when we want to install something in linux and the one or the other dependency is not satisfied. The (easy) solution to this is to go to synaptic and install all the necessary files, libraries e.t.c. that are needed in order for the installation to be accomplished. 

My version of ubuntu is dapper drake 6.06. I wasn' so fortunate so as to be able to install the latest versions of amsn and skype without any problem. Even though I have the libraries that are needed, I do not have the latest versions, which are by default installed in feisty fawn 7.04 or gutsy gibbon 7.10. 

For example skype asks for libasound2. I searched in synaptic and I found out that the library in question is indeed installed. Searching the forums I found out that those who upgraded their version of ubuntu didn't have any problem at all and that even though the library exists also in dapper, its version is not the latest one that is needed. The installation in feisty was flawless.

Yet, ubuntu, and linux in general, is an operating system that someone can modify. Or at least it gives the freedom to one who wants to modify it in such a way so as to cover one's needs. 

I think that if I downloaded the library in question (libasound2 for feisty fawn) and in some way installed it in dapper drake, then skype should be installed without any problems. Do you think that my thought is correct? And if the answer to the previous question is affirmative, can someone tell me how I will be able to install this library?

Thank you for any help,
Regards!

---

### Post by mikewhatever on 2008-02-09
The problem is that libsound2 is not the only dependency required. Have you got the rest of them installed? [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
    *  Software requirements
    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libsigc++ 2.0.2
    * libasound2 1.0.12

---

### Post by Claus7 on 2008-02-09
Hello,

I tried to downoad the library from here:
[https://launchpad.net/ubuntu/feisty/i386/libasound2-dev/1.0.13-1ubuntu5](https://launchpad.net/ubuntu/feisty/i386/libasound2-dev/1.0.13-1ubuntu5)

It is a debian package so the installation is done easily (the command line is not needed). Yet, when I tried to install it, it said that it had confilicts with the previous version of libasound2 and it wasn't installed.

I tried to remove libasound2 completely from my system via synaptic. Yet, I saw that I had to unistall many other packages that depended on that library.

For the other dpendencies that you mention I do not know If I have them. During the installation of skype it didn't mention anything else, other than libasound2. I think that the new version of ubuntu might be the only solution.

Regards!

---

### Post by mikewhatever on 2008-02-09
I pretty much have the idea of what happened from here [http://blog.charlvn.za.net/2007/06/skype-14074-on-ubuntu-dapper.html](http://blog.charlvn.za.net/2007/06/skype-14074-on-ubuntu-dapper.html).
If you feel stuck with the old 1.13 version, I can attest that, functionality wise, 1.14 is not all that much better. It took them ages to finish it, but I really failed to see why they even bothered.

---

### Post by Claus7 on 2008-02-09
Hello,

I just wanted to see if it was working. Skype works very nice in dapper. I also wanted to know what it will happen if I wanted to change another library for something else. Would I be able to do so? I see that it is not an easy task. I also downoaded all the new version of alsa. I tried to install it, yet to no avail.

Apart from that I wanted to see if I would be able to install the newest version of amsn. The 0.97b is nice and very stable, yet it lacks some things that the windows counterpart has. Anyway, thank you for your time. I 'll stick for now with what I have. 

Regards!

---

### Post by Claus7 on 2008-02-10
Hello,

'cause I messed my alsa sound with all these installations I tried, I went in synaptic and reinstalled everything that had to do with alsa, especialy the library libasound2. After that I was able to hear without problems. Just FYI.

Regards!

---

### Post by Claus7 on 2008-04-19
Hello,

this post has to do with the solution of the problem of installing the new version of skype, which is 2.0.0.68, and which has a very nice feature for linux users:
audio and video support simultaneously.  

If someone goes to the skype web site and wants to download the latest version for ubuntu, he or she will see that beside the ubuntu sign, there is 7.04+ version. If dapper drake users try for example to use this package, then they will be disappointed, because that error arises : skype needs libasound2.

The "weird" thing is that 6.06 has that library and also all the other dependencies that skype needs. So, what someone should do in order to have both video and audio in skype?

I downloaded the **static oss** (open sound system) version. I opened a terminal and I typed :
```
./skype
```
and voila! I was able to have the newest version of skype. The pros vs amsn and msn is that the video is smooth (very much!) and of course it supports both video and audio, the cons is that the file transfer is slow (it was always).

I didn't have to unistall the previous version of skype, which I had installed via synaptic. Hope this helps a little...

Regards!

---

