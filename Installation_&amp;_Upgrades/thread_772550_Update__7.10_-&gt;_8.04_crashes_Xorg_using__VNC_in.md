---
title: "Update  7.10 -&gt; 8.04 crashes Xorg using  VNC in login screen"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by gourry on 2008-04-28
I just updated an Ubuntu 7.10 to 8.04. The login screen doesn't work with VNC any more: whenever I click the mouse (in any position of the screen, even when it's pointing to the background) the X server crashes and, on the client PC, I get the message > Connection reset by peer (10054) On Xorg.log the following error is reported:

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f52420]
2: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN3rfb16VNCSConnectionST12pointerEventERKNS_5PointEi+0xb6) [0xb7ba5e46]
3: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN3rfb10SMsgReader16readPointerEventEv+0xda) [0xb7baed7a]
4: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN3rfb12SMsgReaderV37readMsgEv+0x15a) [0xb7ba301a]
5: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN3rfb11SConnection10processMsgEv+0xd2) [0xb7ba2932]
6: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN3rfb16VNCSConnectionST15processMessagesEv+0x48) [0xb7ba69f8]
7: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN3rfb11VNCServerST18processSocketEventEPN7network6SocketE+0x3f) [0xb7b983df]
8: /usr/lib/xorg/modules/extensions//libvnc.so(_ZN14XserverDesktop13wakeupHandlerEP6fd_seti+0xef) [0xb7b8c27f]
9: /usr/lib/xorg/modules/extensions//libvnc.so [0xb7b847be]
10: /usr/bin/X(WakeupHandler+0x59) [0x8091719]
11: /usr/bin/X(WaitForSomething+0x1e2) [0x81b1d22]
12: /usr/bin/X(Dispatch+0x8d) [0x808d69d]
13: /usr/bin/X(main+0x48b) [0x807471b]
14: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ceb450]
15: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

```

I'm connecting to the Ubuntu machine using RealVNC viewer on a WindowsXP machine. My Ubuntu machine has no monitor nor keyboard/mouse. Actually I cannot use it anymore, so I need a quick solution...

I hope anybody can help me. Thank you everybody for your hard work!

---

### Post by gourry on 2008-05-05
Has anybody the same problem?

---

### Post by anigodin on 2008-05-06
It sound about the same problem I have.

I have two computer, both with linux. one is my main machine and the other an HTPC with Mythbuntu with an ubuntu look. I was using VNC from a terminal to control the HTPC. then, a few days ago I upgraded both computers to ubuntu 8.04 and now when I try to connect I can, but as soon as I click with the mouse in the remote computer it logs off and it say that the user will login in 30 sec.

Somebody told me it might be a firewall problem. anybody has an idea?

---

### Post by sizzam on 2008-05-19
There is an open bug for this in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/180619/](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/180619/)

---

