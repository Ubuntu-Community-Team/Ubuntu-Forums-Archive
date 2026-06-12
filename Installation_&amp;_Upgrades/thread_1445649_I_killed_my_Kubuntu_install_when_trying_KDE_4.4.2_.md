---
title: "I killed my Kubuntu install when trying KDE 4.4.2 can I fix it?"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by Token-Ring on 2010-04-02
Long story short my roommate has been using KDE 4.4.2 for a few weeks and enjoying it, so I figured I would give it a shot when I saw [this]("http://www.kubuntu.org/news/kde-sc-4.4.2") on the Kubuntu front page. I added ppa:kubuntu-ppa/backports to my software sources and asked kpackage kit to look for updates, it found a bunch, plus around 25 blocked updates. I figured they were blocked because they depended on some other update I was about to install. I told it to start updates and left it on its own for a while. About halfway through KDE crash handler popped up saying the network manager crashed, so I told it to restart, plugged into my wired connection, and continued updates. Once it finished, their were still 25 blocked updates to I figured a restart was in order. Once I restart I get to the log in screen, log in, and then I am prompted with this message by the KDE Crash Handler:

```
We are sorry, Plasma Workspace closed unexpectedly.
Details: kdeinit4 PID: 2580 Signal: 11 (segmentation fault)
```

If I close the dialogue box I just get a black screen.

I tried ctrl+alt+F4 to get to a terminal and did an apt-get update then apt-get upgrade, but it claims their are no new packages for installation. 

What can I do to restore my computers functionality.

Info:
Acer AspireOne Netbook
Kubuntu 9.10

---

### Post by sau99ms on 2010-04-03
> **Token-Ring said:**
> Long story short my roommate has been using KDE 4.4.2 for a few weeks and enjoying it, so I figured I would give it a shot when I saw [this]("http://www.kubuntu.org/news/kde-sc-4.4.2") on the Kubuntu front page. I added ppa:kubuntu-ppa/backports to my software sources and asked kpackage kit to look for updates, it found a bunch, plus around 25 blocked updates. I figured they were blocked because they depended on some other update I was about to install. I told it to start updates and left it on its own for a while. About halfway through KDE crash handler popped up saying the network manager crashed, so I told it to restart, plugged into my wired connection, and continued updates. Once it finished, their were still 25 blocked updates to I figured a restart was in order. Once I restart I get to the log in screen, log in, and then I am prompted with this message by the KDE Crash Handler:

```
We are sorry, Plasma Workspace closed unexpectedly.
Details: kdeinit4 PID: 2580 Signal: 11 (segmentation fault)
```

If I close the dialogue box I just get a black screen.

I tried ctrl+alt+F4 to get to a terminal and did an apt-get update then apt-get upgrade, but it claims their are no new packages for installation. 

What can I do to restore my computers functionality.

Info:
Acer AspireOne Netbook
Kubuntu 9.10

I had this exact same problem yesterday. Here's what I did:

- Close the dialogue box and you'll have the black screen

- Alt + F2 and search for Konsole - open Konsole

- Enter sudo apt-get install plasma-desktop 

- Enter your password

- Plasma desktop will install

- Then once that's finished in terminal enter sudo reboot

You should then be able to log in and you'll have a new plasma desktop but all your files/folders are preserved. I found that mine was upgraded to KDE 4.4.2 -to check this, go to system settings and at the top click help and go to About KDE and select that. This should tell you what version of KDE you're running.

I also suggest checking for any updates in KPackage Kit as I think there were quite a few in there after I'd installed the plasma desktop again.

Please post back and let me know if this worked for you - I certainly hope this helped.

Best wishes,

Mark

---

### Post by Token-Ring on 2010-04-03
Ha! That worked perfectly! the only hitch with the upgrade was that I ended up with two panels at the bottom over each other, so I just had to remove one. Thank you very much Mark you saved me a lot of time reinstalling and fixing all the settings back how I want them.

---

### Post by sau99ms on 2010-04-25
> **Token-Ring said:**
> Ha! That worked perfectly! the only hitch with the upgrade was that I ended up with two panels at the bottom over each other, so I just had to remove one. Thank you very much Mark you saved me a lot of time reinstalling and fixing all the settings back how I want them.

My pleasure - glad to be of help!

All the best,

Mark

---

