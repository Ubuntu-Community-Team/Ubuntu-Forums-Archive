---
title: "Problem in reinstalling Hamachi"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2007-11-09
I had hamachi installed in my Ubuntu 7.04 before which was working OK. After I upgraded to 7.10, it stopped working. So I tried to reinstall it. At first, I did not do anything to remove the old hamachi files, but just followed the following tutorial
 [http://www.computechgroup.com/?p=360](http://www.computechgroup.com/?p=360)
to install hamachi as a system service. But when I ran 
```

sudo hamachi-init -c /etc/hamachi

```

The following did not gets print out
```

Initializing Hamachi configuration (/etc/hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /etc/hamachi directory .. ok
  saving /etc/hamachi/client.pub .. ok
  saving /etc/hamachi/client.pri .. ok
  saving /etc/hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

```

And, if I try to follow the rest of the tutorial, hamachi does not function. Is there any suggestion?

Thanks.

---

### Post by djwheels on 2007-11-09
Try this, look for the part about upx-ucl-beta

[http://ubuntuforums.org/showthread.php?t=586005](http://ubuntuforums.org/showthread.php?t=586005)

---

