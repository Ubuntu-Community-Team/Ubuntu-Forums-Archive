---
title: "kubuntu network manager problems"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Asraniel on 2009-03-20
Hello,
i've got a small problem with the networkmanager widget. When connecting to my home wireless network (i don't about others) my network password is asked (the WEP one). After entering it is asked just again, and again (3 times usualy). after entering it 3 times, i get the popup message that the connection failed. But the connection continues, and after some time (2 minutes perhap), i get the message that the connection was successfull (and it was).
What is interesting is that kwallet stores 13 passwords (some empty, others not) in maps(called like that in german). The maps are called like that:
{2f11eec1-8f0f-4015-801e-a79ce239b6d1};802-11-wireless-security
{2f11eec1-8f0f-4015-801e-a79ce239b6d1};802-1x
{4f12200b-6148-499b-85e1-75758f423d38};802-11-wireless-security
...........

So it seems like the password storing is somehow broken, or not (since it works after some time).

This is actually my last kubuntu bug!!! this will be a great release (and i'm  putting some pressure now because i want to install that release on my gf's computer tomorrow ).

have a nice day and thx for the great work

---

### Post by jlacroix on 2009-03-20
> **Asraniel said:**
> Hello,
i've got a small problem with the networkmanager widget. When connecting to my home wireless network (i don't about others) my network password is asked (the WEP one). After entering it is asked just again, and again (3 times usualy). after entering it 3 times, i get the popup message that the connection failed. But the connection continues, and after some time (2 minutes perhap), i get the message that the connection was successfull (and it was).
What is interesting is that kwallet stores 13 passwords (some empty, others not) in maps(called like that in german). The maps are called like that:
{2f11eec1-8f0f-4015-801e-a79ce239b6d1};802-11-wireless-security
{2f11eec1-8f0f-4015-801e-a79ce239b6d1};802-1x
{4f12200b-6148-499b-85e1-75758f423d38};802-11-wireless-security
...........

So it seems like the password storing is somehow broken, or not (since it works after some time).

This is actually my last kubuntu bug!!! this will be a great release (and i'm  putting some pressure now because i want to install that release on my gf's computer tomorrow ).

have a nice day and thx for the great work

I have the same problem, but mine won't connect at all. The network manager in Jaunty Kubuntu is HORRIBLE. I've never had trouble with networking before.

You should chime in on my bug report about this here:
[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/339313](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/339313)

Sorry I didn't have a solution. :(

---

### Post by Reiger on 2009-03-20
Actually it is better than it *used* to be. Or rather it was till I replaced it with wicd. (apt-get install wicd) You could do the same, see if that fixes ;it'. Now don't quote me on the following but IIRC 802.1x uses various WEP keys, and each WEP key will be stored somewhere in your wallet-manager/keyring if you use network manager (kde or gnome). So that might help explain why you get to see a total of 13 WEP keys.

---

### Post by jlacroix on 2009-03-20
> **Reiger said:**
> Actually it is better than it *used* to be. Or rather it was till I replaced it with wicd. (apt-get install wicd) You could do the same, see if that fixes ;it'. Now don't quote me on the following but IIRC 802.1x uses various WEP keys, and each WEP key will be stored somewhere in your wallet-manager/keyring if you use network manager (kde or gnome). So that might help explain why you get to see a total of 13 WEP keys.

The KDE wallet is one of the first things I disable.

---

