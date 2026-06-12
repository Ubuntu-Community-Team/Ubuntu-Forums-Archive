---
title: "Network Manager"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by Rickyk on 2008-07-12
Hey everyone i am trying to get online with my Ubuntu OS. I accidentally deleted my Network Manager app. I cannot connect to the internet to get the app back so i am using my other computer to get it. I need to find out how to download it on my working computer (windows xp) and i can transfer it useing a flash drive. so where can i get it and how do i download it once its on my ubuntu computer?? Sorry if it sounds complicated cause its hard to explain...

Thanks
Ricky.:KS

---

### Post by SkonesMickLoud on 2008-07-12
It's easy to do from inside Ubuntu.

First, boot into your existing install.  Once you're at the main screen, go ahead and insert your Ubuntu CD into the drive.  While your drive is spinning up and figuring out what you just loaded go to System >> Admin >> Software Sources.  Enter your password.  Tick the box marked "CD-ROM Ubuntu...".  Then click "Close".  A box will pop up asking you if you want to reload your sources.  Click Yes or Reload.  Then, open up a terminal and copy/paste this:

```
sudo apt-get install network-manager
```

Now, go to System >> Preferences >> Sessions.  Look through the list for "Network Manager".  See it?  You're good to go.  

**If not:**

1) Click "Add"
2) In the box marked "Name" enter:  Network Manager
3) In the box marked "Command" _**copy/paste**_:  nm-applet --sm-disable
4) In the box marked "Comment" enter:  Network Manager applet
5) Click "OK".

Log out, Log back in.  Check the Sessions menu you were just in to ensure that Network Manager is running.

---

