---
title: "Network manager, Jaunty, and CDMA internet issue"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by charlener on 2009-04-05
I'm using the a daily build of ubuntu netbook remix (jaunty) on a haier x200 with an anydata adu-310 modem and cdma mobile broadband from g-mobile here in Mongolia.

I've disabled the PIN, and setting up a PPP connection in Mongolia with my the dial-out number of #777 and my supplied username and password works fine.

When I try using it in ubuntu, the device gets automatically recognized by network manager as "auto mobile broadband (cdma) connection." I went into its settings and used the same username/password as in the windows setup, but when I attempt to connect a box pops up asking for my password again, and then it disconnects without ever fully authenticating (I think).

Any ideas why this may be happening? It's my only source of internet so to get online for this support I have to use Windows.  I'm comfortable using command lines and utilities but am rather unfamiliar with linux and don't know where to start.  Any help would be greatly appreciated.

Thanks,
Charlene

---

### Post by Sef on 2009-04-05
moved to jaunty.

---

### Post by blackened on 2009-04-05
[ATTACH]108839[/ATTACH]

You may have to use trial and error to find the correct authentication methods available on your connection. Try checking your providers website for more information. I originally had to disable a few to get my Sierra 598u to work properly on a different machine running Jaunty.

---

### Post by charlener on 2009-04-06
I have fussed around with it - I tried setting to only CHAP and PAP but no luck so far...this is what the modem is ostensibly set up to use typically (see image attached)

---

### Post by charlener on 2009-04-06
Hmm.  Actually, I tried it again and it connected - two or three times - with no problems.  However, after another couple of trial connects-disconnects I began to get the same error again. I unplugged and replugged in the modem with no success.  Haven't tried rebooting yet though to see if that makes a different.

---

### Post by charlener on 2009-04-07
A workaround to this - I find if, after a connection error, I edit the IPv4 settings to Automatic (PPP) addresses only, then connect, disconnect, and change back to Automatic (PPP) and connect it works.

Seems quite odd, but it only seems to work if I follow those specific steps.

---

