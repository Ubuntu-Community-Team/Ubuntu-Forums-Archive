---
title: "Need some explanations..."
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by cursebg on 2007-06-30
Urrr... how do i compile something? I don't understand this:
```
Installation

    *
      Download kernel patch: linux-2.6.13-mppe-mppc-1.3.patch.gz or linux-2.4.31-mppe-mppc-1.3.patch.gz,

    *
      Download pppd-2.4.3,

    *
      Download pppd patch: ppp-2.4.3-mppe-mppc-1.1.patch.gz

    *
   [COLOR="Red"]   Apply patches to the kernel and pppd,
[/COLOR]
    *
      Do eg. "make menuconfig". In "Network device support" choose "PPP (point-to-point protocol) support" and then mark "Microsoft PPP compression/encryption (MPPC/MPPE)",

    *
      Mark SHA1 and RC4 algorithms in CryptoAPI's configuration menu,

    *
     [COLOR="Red"] Compile kernel and pppd[/COLOR],

    *
      If you have compiled MPPE/MPPC as module, add to your /etc/modules.conf following line:

    [CODE]  alias ppp-compress-18 ppp_mppe_mppc
```[/CODE]
Could someone please tell me what to type in the terminal?

---

### Post by solar george on 2007-06-30
What are you trying to do, there is probably an easier way than recompiling the kernel.

---

### Post by cursebg on 2007-06-30
> **solar george said:**
> What are you trying to do, there is probably an easier way than recompiling the kernel.

Oh, I thought there is, too. But I can't find any other way to make PPTPCONFIG use MS-CHAP-v2 so I thought that the MPPE (Microsoft Point to Point Encryption) part of the kernel is bugged.
Any other suggestions than recompiling it? Please help! I'm freaking out! :-({|= :confused: It's already 7 hours trying to fix it...

---

### Post by solar george on 2007-06-30
Have you seen these [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) instructions?

---

### Post by cursebg on 2007-06-30
> **solar george said:**
> Have you seen these [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) instructions?

OF course... and it sux! After I install it, run it, set it, etc. I click connect and... It shows me a message:
MPPE required, but MS-CHAP[v2] not performed.

Then I run the debug facilities and in the detailed info the error is explained like this:

Sent: ...<MPPE required but not available>
Rcvd(recieved): ...<peer refused to authenticate>



And I thought that this might be a problem with the kernel although it's supposed to support MPPE (it is version 2.6.20)
Please HELP!

---

### Post by cursebg on 2007-06-30
The problem is explained here: [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_bmanp](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_bmanp)
but i can't understand it!!!

---

### Post by cursebg on 2007-06-30
C'mon please someone help me!

---

