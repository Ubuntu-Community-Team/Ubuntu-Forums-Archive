---
title: "A3 fine at first. Now, &quot;Networking Disabled&quot;"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-03-01
Since I last booted up (could have been from hibernation - not sure) I have no network. The NM tool-tip says "Networking Disabled".

Under System-> Preferences -> Network Connections, the Auto eth0 entry is gone, and there are no wired connections there anymore. But the wireless entry is there (which I can't use)

Anyone else got this?

---

### Post by odysseusjak on 2010-03-08
I have the same issue.  It worked at one point but now it's not working and hasn't worked for a while.

Perhaps someone can explain 'simple' kernel stuff to me.  It's almost like, when a new kernel comes out, it's made from scratch.  Things that work in the previous version *should* work in the new version.  But, alas, it doesn't.  I don't understand it.  I have *never* had a problem with wireless and Ubuntu - until now.  I can't figure it out.  It uses the Intel GM965 chipset.  Anyone have any ideas on how to get this working?

---

### Post by Wheelsner on 2010-03-08
Hmm, had something similar happen to me (not on Ubuntu but on Arch) following a failure to resume post-hibernation.  Network manager got somewhat confused re what state it should be in. 

 Have you tried the following?

```
sudo rm /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by HalfEmptyHero on 2010-03-08
The same thing happened to me, but when I right clicked on the networking icon it had Enable Networking unchecked. When I checked it again, all was good. Hopefully it is as simple with you.

---

### Post by odysseusjak on 2010-03-08
Not for me.  Mine is grayed out.  And it says, 'disabled'.

---

### Post by syphr42 on 2010-03-14
I just hit this problem. Wheelsner is correct about the state, but you do not need to delete the file. It's a simple text file and you will probably find the following line:

```
NetworkingEnabled=false
```

Just change that false to true and then restart Network Manager:

```
sudo restart network-manager
```

---

### Post by QwUo173Hy on 2010-03-14
Well, the updates seem to have fixed it for me - although I have other problems now with autologin.

---

### Post by Cincinnatux on 2010-03-15
> **syphr42 said:**
> I just hit this problem. Wheelsner is correct about the state, but you do not need to delete the file. It's a simple text file and you will probably find the following line:

```
NetworkingEnabled=false
```

Just change that false to true and then restart Network Manager:

```
sudo restart network-manager
```

Not to be a complete noob here, but could somebody explain how the above code operates differently from:

```
 sudo /etc/init.d/NetworkManager restart 
```

I found the latter elsewhere on UbuntuForums.org when my upgrade from Mint7 to Mint8 borked my Network Manager, and the latter command did indeed restore Internet access.  I remain, however, confused as to the difference in effect between these two commands.

I find it stunning (and embarrassing) that after running Ubuntu exclusively for two years, I *still* am in the 'noob mode' of copying commands letter-for-letter without understanding what I'm doing.  Clearly, not an ideal way to be a computer user.  Thank goodness for these fora, or I'd still be a Windows user.  But I still wish I could learn this stuff.  I hate being incompetent.

Thanks to those of you with the patience and generosity to share your knowledge with those of us who are still a bit adrift!

---

### Post by cariboo on 2010-03-15
As with everything, there is usually at least 3 different ways to do anything.

---

### Post by ALIENDUDE5300 on 2010-03-16
just wanted to say that the proper command is "sudo /etc/init.d/network-manager restart", not sudo /etc/init.d/NetworkManager restart". The command is case sensitive, and there is a hyphen between the words.

---

### Post by odysseusjak on 2010-03-18
None of these steps worked for me.  The wireless card is on, but there is not light on the machine and Network Manager states 'wireless is disabled'.

---

