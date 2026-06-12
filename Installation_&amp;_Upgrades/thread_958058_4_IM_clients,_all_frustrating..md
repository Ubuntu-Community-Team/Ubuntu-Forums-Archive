---
title: "4 IM clients, all frustrating."
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by SheNux on 2008-10-25
*Big breath* Alright! Let's start with the clients I have/had.
aMSN, kopete, gaim and pidgin.

For some unknown reason, pidgin and gaim started to EAT my contact lists. They were randomly deleting contacts and that in itself is pretty frustrating. When I'd restart them and log in again, I kept getting authorisation requests from my buddies that shouldn't have been deleted in the first place. I'm pretty sure it all starte when I tried to group my buddies by accounts too.

What I was doing, was I had two MSN accounts logged in, and I created group A for MSN A, and group B for MSN B. I thought because I *think* i was using Pidgin at the time all the shenanigans started, I'd completely remove Pidgin and reinstall it. That didn't work because apparently my repositories were wrong, or something. I could have sworn they were right, and Pidgin stopped showing up in Synaptic Package Manager. Bugger!

I tried to get aMSN working again. I have 0.96, and apparently I had to upgrade to 0.97. I used a thread I found on these forums to try to install the upgrade, but at the last step, I tried to download the Feisty Fawn version of aMSN0.97 only to get a 404 not found page. Aaaaarrrrgh! I still haven't been able to install aMSN 0.97 which is mandatory because for some reason MS changed the protocol, and 0.97 was to fix that. They didn't release an update of aMSN specifically for Feisty, which I'm running.

I tried to install the gutsy version, but it says the dependency zlib1g can't be satisfied, even though I have it installed, I know it because I picked up terminal and typed "sudo apt get install zlib1g" and it said that the latest version was already installed.

Three down, one to go.

I asked a friend who I trust to log into my main account in Windows Live Messenger and re-add my contacts. I thought it might have been a client problem. He confirmed that my whole contact list had been deleted, and started re-adding everybody. He logged out, I logged back in with Kopete, and everything seemed to be sorting itself out. My buddies started coming back!

Except now, I'm getting random SIGABRT message 6 errors from kopete! I checked the backtrace, and got the following.

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1241094448 (LWP 24834)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb60c0df0 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb60c2641 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb62c4270 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb62c1ca5 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb62c1ce2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb62c1e1a in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0xb62c225e in operator new () from /usr/lib/libstdc++.so.6
#14 0xb62c233d in operator new[] () from /usr/lib/libstdc++.so.6
#15 0xb6c12774 in operator>> () from /usr/lib/libqt-mt.so.3
#16 0xb701c37a in ?? () from /usr/lib/libkdecore.so.4
#17 0xbfafdbd4 in ?? ()
#18 0xbfafdc10 in ?? ()
#19 0x00000001 in ?? ()
#20 0xbfafdcd4 in ?? ()
#21 0xbfafdc38 in ?? ()
#22 0xbfafdc30 in ?? ()
#23 0xbfafdc28 in ?? ()
#24 0x00000000 in ?? ()

```

I'm currently using gaim which is co-operating for now apart from the occasional "connection error occurred" messages, but I would really love to get aMSN working again. To me, it seems like the MSN servers hate my guts, but I'm sure my clients have something to do with it.

If only all my friends knew how to use IRC, we'd never have these problems. :P

---

