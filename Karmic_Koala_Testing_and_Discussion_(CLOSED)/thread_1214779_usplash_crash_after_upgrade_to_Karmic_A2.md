---
title: "usplash crash after upgrade to Karmic A2"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mudi on 2009-07-16
I didn't know which forum to post this in so hopefully it will be moved to the correct place (would have posted it in a test version forum but didn't see one!)  I upgraded to Karmic Alpha 2 on a Acer Aspire One netbook in hope of getting better hardware support (couldn't get builtin microphone working in Jaunty, it does work now!)

After a couple very silly issues with the touchpad that I was able to resolve after finding it was an error on my part, I now get usplash crashing on every boot.  The relevant dmesg notice is this:
[    4.204422] <6>usplash[913]: segfault at b7feb530 ip 00ac44f0 sp bfc7b180 error 6 in libusplash.so.0[aa0000+2c000]

I don't know if anyone else has experienced this and has a fix.  It's not a major problem but a minor annoyance for sure.  I really don't know how to debug usplash to get a more useful error report either.

edit: Oops, just found the testing forum, but it wasn't on the front page :oops: sorry...

---

