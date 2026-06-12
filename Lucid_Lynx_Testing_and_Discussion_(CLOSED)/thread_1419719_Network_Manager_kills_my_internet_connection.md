---
title: "Network Manager kills my internet connection"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MaX on 2010-03-02
Hi,

When I start my computer I have internet connection, but when I try to open Empathy it says Disconnected (No network connected (altough everything else works fine), so I right click Network Manager and select Internet (Wired). Now I get a dialogue box that states that I'm disconnected from the wired network. So I select it again. Still the same message.

Network manager is unable to use a simple dchp command to get internet to work. So I open a terminal and write
```

sudo dhclient3

```
And now Internet works again, but I still can't connect Empathy since the damn network manager doesn't know I'm connected...

Does anyone know what might be the problem?

---

### Post by k3lt01 on 2010-03-03
> **MaX said:**
> Hi,

When I start my computer I have internet connection, but when I try to open Empathy it says Disconnected (No network connected (altough everything else works fine), so I right click Network Manager and select Internet (Wired). Now I get a dialogue box that states that I'm disconnected from the wired network. So I select it again. Still the same message.

Network manager is unable to use a simple dchp command to get internet to work. So I open a terminal and write
```

sudo dhclient3

```
And now Internet works again, but I still can't connect Empathy since the damn network manager doesn't know I'm connected...

Does anyone know what might be the problem?None of that scenario makes sense. If the last part is accurate then NM is not the problem, Empathy however is.

---

### Post by MaX on 2010-03-03
Well according to NM I'm not connected to the Internet either...

---

### Post by k3lt01 on 2010-03-03
> **MaX said:**
> Well according to NM I'm not connected to the Internet either...If that is the case why did you say this?
> **MaX said:**
> And now Internet works again, but I still can't connect Empathy since the damn network manager doesn't know I'm connected...So is this wrong then? You are either connected or you aren't, you can't have it both ways.

Can you surf the net in your "connected" but not connected state? If yes then you are connected and Empathy has a problem connecting which has nothing to do with NM cause you can surf the net anyway.

If indeed NM isn't connecting you wont be able to get anything at all so your above statement is wrong and we need to know what the reality of your situation is.

---

### Post by Ibidem on 2010-03-03
Try this:
nm-applet AND empathy fail to recognize the internet connection.
I wonder...How do the two detect "online/offline"? Is it via some common backend?

---

### Post by k3lt01 on 2010-03-04
> **Ibidem said:**
> Try this:
nm-applet AND empathy fail to recognize the internet connection.
I wonder...How do the two detect "online/offline"? Is it via some common backend?But is this the case? I'm trying to point the OP to accurately describe his problem. Is he able to browse the internet at all? By his first post he is, if that is really the case then there may be another problem and we need the problem to be accurately described.

---

### Post by MaX on 2010-03-14
> **k3lt01 said:**
> If that is the case why did you say this?
So is this wrong then? You are either connected or you aren't, you can't have it both ways.

Can you surf the net in your "connected" but not connected state? If yes then you are connected and Empathy has a problem connecting which has nothing to do with NM cause you can surf the net anyway.

If indeed NM isn't connecting you wont be able to get anything at all so your above statement is wrong and we need to know what the reality of your situation is.


NM doesn't do anything for me. I could uninstall it and I'd still have Internet connected through dhclient3. 
NM doesn't detect that I'm connected at all. It doesn't want to connect. Even though I already am connected NM doesn't detect this.

Since NM reports that I'm "Not Connected to any network" (Although I clearly am since I can write this on the forums) Empathy listens to NM and thus sets itself to Offline. The fault here is with NM not being able to detect my dhcp connection.

---

### Post by katie-xx on 2010-03-14
> **MaX said:**
>  Empathy listens to NM and thus sets itself to Offline. 
The fault here is with NM not being able to detect my dhcp connection.

Its a bit of a struggle here trying to match this to how things actually work.
What do you think is happening when Empathy is not involved? Is everything ok then?

Kate

---

### Post by k3lt01 on 2010-03-14
Max, If what you are saying in your last post is correct then you can simply remove NM and install Wicd. See if that makes any difference.

I will repeat, you need to be accurate in your posting, especially thread titles because it is obvious NM has NOT killed your internet connection if you are able to use the same machine and post here.

---

### Post by diebels on 2010-03-15
> **k3lt01 said:**
> Max, If what you are saying in your last post is correct then you can simply remove NM and install Wicd. See if that makes any difference.

I will repeat, you need to be accurate in your posting, especially thread titles because it is obvious NM has NOT killed your internet connection if you are able to use the same machine and post here.
The description from the OP is perfectly plausible.  When NetworkManager is offline, it signal through dbus that it is offline.  This is detected by several applications epiphany, evolution, firefox and they refuse to communicate with the internet.  Actually in firefox you are able to force the online/offline status in the File-WorkOffline menu.

So in the sense of the OP's Internet Connection status available through dbus, yes, NetworkManager has killed it.

Also one of the main purposes of this forum section is testing of Ubuntu 10.04, so it's better to figure out what the problem is with the applications that's part of the standard Ubuntu install and not recommending to install wicd.

---

### Post by k3lt01 on 2010-03-15
> **diebels said:**
> Actually in firefox you are able to force the online/offline status in the File-WorkOffline menu.When describing something most people describe what is happening and how they are circumventing it. Max hasn't done this and I am trying to get him to tell us what is happening accurately. If he is using Firefox via the Offline menu he should tell us this.

> **diebels said:**
> So in the sense of the OP's Internet Connection status available through dbus, yes, NetworkManager has killed it. I think you may be jumping the gun somewhat here. When we get an accurate description off Max of what he is doing, and I mean a step-by-step process maybe we could come to that conclusion. As it is he is here and then he goes away for a week, only to come back without any more information apart from the fact he could remove NM and still connect even though he isn't connected.

> **diebels said:**
> Also one of the main purposes of this forum section is testing of Ubuntu 10.04, so it's better to figure out what the problem is with the applications that's part of the standard Ubuntu install and not recommending to install wicd. When a user makes a statement like I paraphrased above it is somewhat logical to offer him other options so he could test his theory. That way if Wicd is no different to NM we can categorically state that NM is NOT the problem and we can move on to what it may be. With the amount of people testing non-standard installs, and openly stating that is what they are doing, I don't see a problem in offering this as a possible test.

As I have been, until today, the only person really responding to Max about this issue I will continue my attempt to help him as best as I can with the information, or lack there-of, he is supplying. If you have other suggestions that may help him please feel free to make them. I fail to see any such attempt though.

---

